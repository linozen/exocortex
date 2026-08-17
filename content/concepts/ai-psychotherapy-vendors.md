---
title: AI vendors in psychotherapy
description: Running snapshot of vendors building AI tools for psychotherapy — session transcription, analysis, documentation, supervision. German market in focus, international players for context.
tags:
  - concept
  - ai
  - psychotherapy
  - market-landscape
author: Linus Sehn | claude-opus-4-7
authored_on: 2026-06-07
sources: []
certainty: C
certainty_notes: "Tier C — vendor descriptions assembled from a 2024–2025 personal market scan, not re-verified against vendor sites in this session. Re-check before citing."
---

A running list. The German market is the primary lens; the US/UK entries are here as comparators, not exhaustive coverage. Re-verify any specific claim against the vendor site before treating it as current — this space moves fast.

## German-speaking market

- **[via-health.de](https://www.via-health.de/)** *(primary German competitor)* — AI documentation software for psychotherapists. Records sessions, transcribes, generates session notes and psychological reports. **Cloud-based**, EU-hosted, DSGVO-compliant; targeted at individual therapists and small practices. Verified against vendor site 2026-06-07.
- **[iptas.de](https://iptas.de)** — German vendor in the psychotherapy AI / session-analysis space.
- **[audEERING](https://www.audeering.com/de/)** (Munich) — AI-based voice analysis specialising in emotion and speech-pattern recognition. Their *audio AI* product offers multimodal emotion recognition and is deployed in healthcare contexts among others.
- **[vitagroup Health Intelligence / Health Dialog](https://hd.vitagroup.ag/)** — health-intelligence platform; relevance to therapy documentation tangential.
- **ZI Projekt** — no public information.
- **[screenapp.io/de/use-cases/therapy](https://screenapp.io/de/use-cases/therapy)** — general transcription product with a therapy use-case page.
- **[nyra.health](https://www.nyra.health/)** — neurological rehab software for clinic and home. Heavy investment in verbatim transcription; ships **CrisperWhisper** (see [[local-speech-stack]]).
- **[psychoware.de](https://www.psychoware.de/references/)** — adjacent vendor (training / documentation context).
- **[psydix.org](https://psydix.org/)** — adjacent vendor.

## International comparators

### Yung Sidekick (USA) — [yung-sidekick.com](https://yung-sidekick.com)

AI-powered transcription and summarisation for psychotherapists. Automates note-taking, reducing manual documentation time. Generates session notes for supervisors and self-review. **Limitation**: English-language market; German clinical terminology and workflow integration would require non-trivial localisation.

### Limbic (UK) — [limbic.ai](https://limbic.ai)

AI platform for mental-health interaction between patient and therapist. Chatbots for assessments and continuous patient monitoring between sessions. **Limitation**: focused on monitoring rather than session-documentation automation — not a direct replacement for a session-transcription product.

### Ember Copilot (USA) — [embercopilot.ai](https://www.embercopilot.ai/)

Automated session documentation for therapists; rapid note generation from audio. **Limitation**: positioned as a broader documentation tool — psychotherapy-specific terminology depth unclear.

### SimplePractice / TheraNest / TherapyNotes (USA)

Practice-management platforms covering scheduling, billing, basic documentation. Provide session-note templates but **no advanced AI transcription or NLP analysis**. All-in-one administrative coverage rather than AI-first documentation.

### Otter.ai / Descript (general competitors)

Broad AI transcription tools — not psychotherapy-specific. High accuracy on speech-to-text, easy workflow integration. **Limitations**: no therapy-specific terminology recognition, no emotion analysis, and the cloud-based architecture poses GDPR concerns for highly sensitive therapy data.

## Adjacent

- [[local-speech-stack]] — the local-first ASR/diarization/hardware components vendors in this space are stitching together
- [[ai-psychotherapy-research-questions]] — open research questions the products in this space implicitly bet on
- [[ocr-pipeline]] — local-document ingestion patterns relevant where session notes already exist as PDFs

## Test resources

- [psyndex.de/tests/testarchiv](https://psyndex.de/tests/testarchiv/) — German archive of psychological tests; useful when evaluating products that claim to track therapeutic outcomes
