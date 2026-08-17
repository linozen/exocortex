---
title: Single-Page Application architecture
description: The architectural shift from server-rendered HTML to a single page whose contents are manipulated in-browser by JavaScript talking to a JSON API.
tags:
  - programming
  - concept
  - web-development
  - architecture
author: Linus Sehn
authored_on: 2026-06-08
sources:
  - "[[full-stack-open]]"
certainty: B
certainty_notes: "Tier B — synthesised from FSO part 0 notes and general training-data recall. The historical sketch (AJAX → React era) is generally well-attested; specific framework popularity numbers are time-sensitive."
---

A traditional web application has the server own rendering: each user action triggers an HTTP round-trip, the server constructs the full HTML for the new view, the browser tears down the page and re-renders. The SPA architecture inverts this: the server ships one HTML shell and an application-bundle of JavaScript; from that point on, the browser owns rendering, and the server is only consulted for data (typically JSON).

## What the shift actually changes

In the traditional model, every interaction is a navigation event. The form submission round-trip looks like:

1. Browser POSTs form data.
2. Server processes the data, modifies state.
3. Server responds with `302 Location: /next-page`.
4. Browser does a GET on the new URL, receiving a fresh HTML page.
5. Browser parses, fetches CSS, fetches JS, fetches images, repaints.

In the SPA model, the same interaction is:

1. JavaScript event handler intercepts the form's `submit`, calls `preventDefault()`.
2. JavaScript serialises form data to JSON and `fetch`-es a domain-relevant endpoint.
3. Server processes and returns the result (JSON, not HTML).
4. JavaScript updates an in-memory model and triggers a re-render of the affected components only.

The page never reloads. The URL bar may change, but only via the History API, not via navigation.

## Consequences

- **The server stops being a UI concern.** It serves data; the UI lives in the browser. This is the precondition for an API/frontend split, for native apps and SPAs sharing one backend, and for the rise of "frontend" and "backend" as separable specialisations.
- **State lives in the browser.** What used to be reconstructed from request parameters and a session cookie on every page render now lives in JavaScript memory for the session's duration. Lose the tab, lose the state — unless you've explicitly persisted it. This is also what makes state management (Redux, Zustand, Pinia, signals) a category of library.
- **The first paint is slower.** Traditional apps render server-side and ship ready-made HTML; SPAs ship a bundle of JS that must download, parse, execute, fetch initial data, and *then* render. SSR/SSG/island-architecture frameworks (Next, Remix, Astro) exist to recover that initial-paint cost.
- **Routing moves to the client.** "What does `/notes/42` mean" is now answered by a router inside the bundle, not by a server route. The server may not even have a `/notes/42` handler; everything past `/` is the same shell HTML.
- **The architecture commits you to JSON contracts.** What the server returns becomes a stable interface that the frontend depends on — versioning and breakage matter in new ways.

## Pre-SPA milestone: AJAX

AJAX was the wedge that made SPAs possible. Before AJAX (early 2000s), JavaScript could manipulate the DOM but could not fetch new data without a full page reload. `XMLHttpRequest` (and later `fetch`) broke that constraint: now JavaScript could request data in the background and update parts of the page. Everything from there is a matter of degree — SPAs are AJAX taken to its logical end, where the *only* server interactions are background data fetches.

## What SPAs are not the right answer to

- Documents that are mostly read-once and rarely revisited (blog posts, marketing pages). The first-paint penalty is wasted; a server-rendered or statically-generated page is faster and simpler.
- Apps where SEO matters and there is no SSR layer. Search engines vary in how well they render JS-rendered content.
- Forms-and-tables CRUD where a HTMX-style "server returns HTML fragments, client swaps them in" gives the same UX without an SPA framework. The category labelled "hypermedia-driven applications" is a deliberate step back from full-SPA complexity.

## Adjacent

- [[rest-architecture]] — the data-exchange protocol most SPAs are built against
- [[react-component-model]] — the most common implementation substrate for SPAs in 2026
