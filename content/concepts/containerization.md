---
title: Containerization
description: The Linux-kernel primitives that make containers possible (namespaces, cgroups, union filesystems), how containers differ from VMs in what they isolate, and the runtime/orchestrator ecosystem that grew around them.
tags:
  - programming
  - concept
  - devops
  - linux
  - infrastructure
author: Linus Sehn | claude-opus-4-7
authored_on: 2026-06-08
sources:
  - "[[devops-with-docker]]"
certainty: B
certainty_notes: "Tier B — kernel primitives (namespaces, cgroups) and the VM contrast are direct citations from kernel and Docker documentation in training data. Specific runtime/orchestrator project status (Swarm de-emphasis, Podman maturity) is time-sensitive — re-verify project health before recommending."
---

A container is not a "lightweight VM." It is a process — or a process tree — running on the host kernel with three things lying to it: its view of the filesystem, its view of other processes, and its quota of resources. Three Linux-kernel mechanisms do the lying. Container runtimes are mostly glue around them; orchestrators are mostly glue around the runtimes.

## The three kernel primitives

**Namespaces** isolate *what a process can see*. There are eight, each scoping a different kind of identifier:

- `mount` — what filesystems are mounted where (this is what gives a container its private `/`)
- `pid` — the process tree; the container's `init` thinks it is PID 1
- `net` — network interfaces, routing tables, firewall rules
- `uts` — hostname and domain name
- `ipc` — System V IPC and POSIX message queues
- `user` — UID/GID mappings (container root can be a host non-root)
- `cgroup` — what cgroup tree the process sees
- `time` — system clock offset (Linux 5.6+)

A process in a namespace cannot observe or affect resources in other namespaces. Namespaces are *partitions*, not sandboxes — they restrict visibility, not capability.

**cgroups** (control groups) limit *how much a process can use*. CPU shares, memory caps, block-IO throttling, network bandwidth, device access. cgroups v2 (default on most modern distros) unified the previously fragmented v1 hierarchy. When Docker says `--memory=512m`, it is writing to a cgroup file under `/sys/fs/cgroup/...`. Without cgroups, a runaway container would happily consume the entire host.

**Union filesystems** (overlayfs is the common one) give containers a *layered* root filesystem. Each Dockerfile instruction adds a read-only layer; the running container gets a thin read-write layer on top. Shared base layers across containers are stored once on disk and mapped into each container's mount namespace. This is why `docker pull` is fast after the first time and why image-size optimisation matters.

The combination — namespaces for isolation, cgroups for quotas, overlay-fs for storage — is what containerization *is*. Everything else (Docker, image registries, Kubernetes) is tooling on top.

## Containers vs virtual machines

A VM emulates hardware. A guest OS — kernel, drivers, init, the whole stack — runs on top of a hypervisor (KVM, Hyper-V, ESXi). The guest cannot see the host kernel; the hypervisor mediates every privileged operation. The isolation boundary is strong (a kernel exploit in the guest does not compromise the host) and the cost is high (~100s of MB of RAM per guest, slow boot, full kernel duplication).

A container shares the host kernel. The "guest" is just a userspace tree running with restricted namespaces and cgroups. Boot is instantaneous (it is just `fork+exec` with extra flags), overhead is negligible, and density is high — hundreds of containers on a host that would struggle with a dozen VMs. The trade is the isolation boundary: a kernel exploit *is* a host compromise, and resource isolation under cgroups is statistical rather than absolute.

The practical consequence: VMs draw a hard line between tenants who do not trust each other; containers draw a soft line between processes owned by the same operator. "Containers in production" really means "containers behind one tenant trust boundary." Multi-tenant container hosting needs a stronger isolation layer underneath — see Kata Containers below.

A useful rule of thumb: containers virtualise the *application*, VMs virtualise the *machine*.

## The runtime layer

The OCI (Open Container Initiative) defines two specifications: an *image format* (the tarball layout produced by `docker build`) and a *runtime spec* (how a runtime is supposed to launch a container from that image). The point is that no specific tool owns the format.

- **runc** — the reference low-level runtime. Implements the OCI runtime spec; given a config and a rootfs, it creates the namespaces and cgroups and execs the container's command. Almost all higher-level tools call into runc.
- **Docker** — the high-level toolchain that popularised containers (2013). Today it is a stack: a CLI (`docker`), a daemon (`dockerd`), a container manager (`containerd`), and runc underneath. Most of what makes Docker "Docker" is the daemon API, the image builder, and the registry protocol — none of which are in the OCI spec.
- **Podman** — drop-in Docker CLI replacement from Red Hat. Daemonless (each `podman run` is a direct user-space process) and rootless by default, using user namespaces so an unprivileged user can run containers. Its `podman compose` and `podman generate kube` aim for source-compatibility with Docker tooling and Kubernetes manifests.
- **containerd** — extracted from Docker as a standalone container manager. Used directly by Kubernetes (via the CRI plugin) and as Docker's internal engine. The dominant low-level runtime in production clusters.
- **CRI-O** — Kubernetes-specific runtime, a thin OCI implementation that speaks the CRI (Container Runtime Interface) directly. No Docker compatibility surface — explicitly scoped to Kubernetes nodes.

## Stronger isolation: when the kernel boundary isn't enough

- **Kata Containers** — runs each container in a lightweight VM (a stripped-down kernel + minimal userspace) while preserving the container UX. The OCI runtime interface is unchanged; Kubernetes does not know the difference. The cost is per-container kernel overhead; the benefit is hypervisor-grade isolation between mutually untrusting workloads. This is the right answer when a cloud provider runs other tenants' containers on shared infrastructure.
- **gVisor** — Google's alternative: a user-space Linux-syscall implementation that intercepts the container's syscalls and reimplements them outside the host kernel. Stronger isolation than plain runc, lower overhead than Kata, but a smaller compatible syscall surface (some workloads fail under gVisor).
- **Firecracker** — AWS's microVM. Not really a container runtime, but commonly mentioned alongside: it boots a hardware-virtualised guest in ~125ms, providing VM isolation at near-container density. The substrate for Lambda and Fargate.

## Orchestration

A single host running containers is the easy case. Production wants schedulers that pack containers across a fleet, restart failures, route traffic, manage secrets, and roll out updates.

- **Kubernetes** — the de-facto orchestrator since ~2017. Declarative API (`apply` a YAML, controllers reconcile cluster state to match). Operates at the pod abstraction (one or more co-located containers sharing a network and mount namespace) and uses the CRI to talk to whichever runtime is on the node. Its complexity is real but is also what lets it absorb every container concern (storage, networking, secrets, ingress, autoscaling, batch jobs) into one model.
- **Docker Swarm** — Docker's built-in orchestrator. Simpler than Kubernetes by a large margin, but largely abandoned by the industry. Still works for small clusters; recommending it in 2026 means accepting that the ecosystem has moved on. Docker, Inc. has quietly de-emphasised it; community Mirantis-owned forks exist.
- **Nomad** — HashiCorp's orchestrator. Multi-workload (containers, VMs, raw binaries, Java apps); much simpler than Kubernetes; not container-specific. Sees use where the operational complexity of Kubernetes is not justified.
- **ECS** — AWS's proprietary orchestrator. Tighter integration with AWS primitives (IAM, ALB, EFS) than self-hosted Kubernetes on EKS, but vendor-locked.

The pattern across all of them: an orchestrator talks to a runtime (containerd / CRI-O / Kata / Firecracker) on each node, the runtime talks to the kernel primitives. Swapping the runtime is mostly transparent to the orchestrator; that is the OCI spec earning its keep.

## What containerization is not

- Not a security boundary against a hostile workload. The kernel surface is shared.
- Not free of state. Volumes, networks, image storage, and orchestrator state all need backups and lifecycle management — "stateless containers" only means the *process* is stateless.
- Not a virtualization replacement for workloads that need a different kernel, different OS, or hardware-grade isolation.

## Adjacent

- [[devops-with-docker]] — the source ref this was extracted from; Docker-specific commands and workflows
- [[ocr-pipeline]] and [[local-speech-stack]] — local clinical-data pipelines where container isolation matters less than reproducible packaging
