---
title: REST architecture
description: An architectural style for distributed systems that uses resource URLs, HTTP verbs, and uniform representations — and the Richardson maturity model that grades how far implementations actually go.
tags:
  - programming
  - concept
  - web-development
  - architecture
  - http
author: Linus Sehn
authored_on: 2026-06-08
sources:
  - "[[full-stack-open]]"
certainty: B
certainty_notes: "Tier B — synthesised from FSO part 3 notes and the Richardson Maturity Model article by Martin Fowler (referenced in the original notes). The Fielding dissertation is the canonical source for REST itself; this note paraphrases the operational subset most APIs implement."
---

REST (Representational State Transfer) is an architectural style — not a protocol or specification — proposed in Roy Fielding's 2000 dissertation. Most modern web APIs claim to be RESTful; in practice, almost all of them implement only a subset. The Richardson Maturity Model is a useful way to grade how far an API actually goes.

## The four levels of the Richardson Maturity Model

**Level 0 — the swamp of POX.** A single endpoint, all requests are POSTs, and the verb is encoded in the request body. This is RPC over HTTP — it uses the protocol as a pipe, not as a vocabulary.

**Level 1 — resources.** Each thing the system knows about gets its own URL: `/notes`, `/notes/42`, `/users/7`. Still typically POST-only, but at least the URL space is meaningful.

**Level 2 — HTTP verbs.** Methods carry semantics:
- `GET /notes/42` — retrieve resource (safe, idempotent, cacheable)
- `POST /notes` — create a new resource under the collection
- `PUT /notes/42` — replace resource (idempotent)
- `PATCH /notes/42` — partial update
- `DELETE /notes/42` — remove resource (idempotent)

Status codes also become meaningful: `200 OK`, `201 Created`, `204 No Content`, `404 Not Found`, `409 Conflict`. This is where the bulk of "RESTful" APIs live in practice — FSO course APIs included.

**Level 3 — HATEOAS** (Hypermedia as the Engine of Application State). Responses include links to related resources and to available next actions. A `GET /orders/42` returns the order *and* a link to cancel it, a link to ship it, links to related customers, etc. The client follows links rather than constructing URLs from a fixed schema. Almost no public APIs implement this — and the cost of Level 3 is high enough that "RESTful" in industry usage usually means Level 2.

## The constraints REST imposes

- **Client/server separation.** UI and storage are different concerns.
- **Statelessness.** Each request carries everything needed to interpret it; the server does not retain session state between requests. (Authentication tokens count as state carried *in* the request, not held by the server.)
- **Cacheability.** Responses declare whether they can be cached and for how long.
- **Uniform interface.** Resources are identified by URL; representations (JSON, XML, …) are decoupled from the underlying resource; verbs are standard.
- **Layered system.** A client cannot tell whether it is talking to the origin server or to an intermediary (proxy, gateway, CDN).
- **Code on demand** (optional). Servers can ship executable code to clients — JavaScript bundles fit this constraint.

## Where REST trades off against alternatives

- **GraphQL** trades the multiple-endpoint structure for a single endpoint and a query language. Wins for clients that need bespoke shapes of data; loses for caching (every query is unique) and for being significantly more complex on the server.
- **gRPC** trades JSON/HTTP for protobuf/HTTP-2. Wins for performance, schema enforcement, and code generation; loses on browser-friendliness (gRPC-Web is an additional layer) and on debuggability (binary payloads).
- **HTMX / hypermedia approaches** lean into Level 3 explicitly: the server returns HTML fragments with embedded links to next actions, and the client (the browser, augmented by HTMX) follows them. The shape of the API maps directly to the UX.

## Adjacent

- [[spa-architecture]] — SPAs are the most common Level-2 REST client
- [[react-component-model]] — orthogonal but commonly paired
