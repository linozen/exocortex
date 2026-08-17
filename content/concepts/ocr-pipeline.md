---
title: OCR pipeline (do it right)
description: A counter-argument to using multimodal LLMs as the OCR primitive. Salvaged from an unknown Hacker News comment.
tags:
  - programming
  - concept
  - ai
  - method
---

The wrong way: dump a document image into a multimodal model and hope. They hallucinate the moment the input isn't pristine 100% high-fidelity.

The right way (paraphrased from an HN comment, ~2024):

- Use an **object detection model trained on documents** to find the bounding boxes of each section as _images_. Each box comes with a confidence score for free.
- Feed each text box to a **regular OCR model** — also gives you a per-prediction confidence score.
- Feed each image box into a **multimodal model** to describe what the image is about (image-only, never as the text extractor).
- For tables, use a **specialist model** (e.g. GridFormer) — not the hyped general-purpose stuff.
- Stitch everything into **flat XML markup** (Markdown is for humans to read, not for pipelines).
- Now you have flat XML per object-detection category, with multi-level probability metadata per box, per letter, per cell.
- Feed _that_ programmatically into an LLM for the actual _text_ processing, using the XML to control which parts of the document get sent.
- Chunk with location data + confidence scores as metadata in the RAG store.

The commenter claimed to have built a system reading 500k pages/day fully locally on $20k of hardware using this pattern.

Relevance: this is the pattern for any local-first clinical-document ingestion. See [[local-speech-stack]] for the audio-side analogue.

## Open-source implementations

Two production-quality stacks already implement the staged-pipeline pattern. Neither exposes per-element confidence scores by default — the one capability the HN argument depends on — but both expose intermediate bounding boxes and block structure, so confidence can be re-derived from the constituent models if wired through.

- **[marker](https://github.com/datalab-to/marker)** (datalab.to) — Surya for OCR + layout + reading order, Texify for math, optional LLM pass for hard layouts. Outputs Markdown / JSON / HTML / RAG-ready chunks. ~0.18 sec/page on H100 (~122 pages/sec parallelised), 3.5 GB VRAM average per worker, runs on CPU / GPU / MPS. **License: GPL-3.0 code, Modified Open RAIL-M model weights** — free for research and personal use; commercial deployment requires a license from datalab.

- **[docling](https://github.com/docling-project/docling)** (IBM Research Zurich, now an LF AI & Data Foundation project) — Heron layout model + table-structure recognition + OCR; optional integration with the GraniteDocling 258M VLM for hard cases. Outputs Markdown, HTML, lossless JSON, and DocTags (a structured XML schema designed for downstream LLM consumption). Specialist parsers for USPTO patents, JATS articles, XBRL financial reports. **License: MIT** (unencumbered for commercial use). Python 3.10+, runs on CPU and GPU, x86_64 and arm64.

Practical heuristic: docling first for commercially-deployed pipelines on account of the MIT license; marker when its model fidelity on a specific document distribution actually beats docling enough to justify the commercial-licensing step. Both are far easier starting points than rolling the staged pipeline from scratch.

## 2025 update: Mistral OCR

Mistral released [Mistral OCR](https://mistral.ai/news/mistral-ocr) in March 2025 — a single multimodal model targeting exactly the use case the HN commenter argued against. The benchmark numbers are strong enough to take seriously:

- ~2000 pages/min on a single node; ~$1 per 1000 pages via API (batch ~halves cost).
- Outputs interleaved markdown with images preserved positionally; structured JSON also supported for downstream function calls.
- Self-reported 94.89% overall accuracy, 96.12% tables, 98.96% scanned documents, 99.02% multilingual fuzzy match across thousands of scripts.

What this changes for the argument above:

- **Confidence scores are still missing.** No per-token, per-cell, or per-region probability metadata exposed. For provenance-critical use (clinical, legal), the staged pipeline retains a real advantage independent of raw accuracy — you cannot RAG-cite what you cannot quantify.
- **On-prem is gated.** Self-hosting available on "selective basis" via sales contact — effectively API-only for most users. Kills the local-first thesis if data residency is a hard constraint.
- **Benchmarks are self-reported.** Treat the 94.89% as marketing until reproduced on the actual document distribution. Failure modes typical of multimodal OCR (handwriting, degraded scans, dense multi-column layouts with footnotes) are not broken out in the announcement.

Read: useful as a baseline to beat with the staged pipeline, and good enough for non-critical document understanding where provenance and on-prem are not required. Doesn't refute the staged-pipeline argument for clinical-document ingestion — it raises the bar the staged pipeline has to clear on the documents where it still wins.
