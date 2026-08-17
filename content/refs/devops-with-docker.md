---
title: "Notes on: DevOps with Docker"
description: University of Helsinki MOOC covering Docker, docker-compose, and basic CI/CD with CircleCI.
tags:
  - ref
  - mooc
  - devops
  - docker
  - stub
aliases:
  - devops-with-docker
author: Linus Sehn
authored_on: 2026-06-08
certainty: A
certainty_notes: "Tier A — direct reference to the course and personal completion record."
medium: course
---

# DevOps with Docker — University of Helsinki

Self-paced MOOC on Docker basics, multi-container apps with `docker-compose`, and a CircleCI-based CI/CD walkthrough. Free, browser-runnable exercises. Source: [devopswithdocker.com](https://devopswithdocker.com/).

## Status

Worked through all three parts when the course still referenced the deprecated `docker-compose` v1 binary; modern Docker bundles `docker compose` as a subcommand. Concepts transfer; specific command syntax may need refreshing against current Docker docs.

## What was covered

- Part 1 — images vs containers, the Dockerfile, port publishing vs exposing, basic CLI
- Part 2 — `docker-compose`, named and bind volumes, container networking, reverse-proxy patterns with nginx, scaling services
- Part 3 — CI/CD with CircleCI, image registry push, multi-stage builds, basic security hygiene

## Extracted concept notes

- [[containerization]] — the kernel primitives (namespaces, cgroups, overlay-fs) Docker is built on, the VM contrast, and adjacent runtimes / orchestrators (Podman, Kata, gVisor, Kubernetes, Swarm)

## Adjacent

- [[abelson2002]] — SICP, in the same MOOC-completion set
- [[full-stack-open]] — the other Helsinki MOOC in this set
- [[local-speech-stack]] — where container packaging may matter for local clinical-data pipelines
