---
title: Local speech stack
description: Local-first ASR, diarization, pseudonymization, and audio hardware — components for an offline transcription pipeline that keeps sensitive audio on-device
tags:
  - concept
  - ai
  - tools
  - audio
  - transcription
author: Linus Sehn | claude-opus-4-7
authored_on: 2026-06-07
sources: []
certainty: B
certainty_notes: "Tier B — repos and projects collected from a 2024–2025 personal scan, verified at collection time. Versions and project status drift fast; treat links as starting points."
---

Components for a transcription pipeline that runs **fully on local hardware** — no cloud APIs, no third-party round-trips. Motivated by sensitive audio (clinical, legal, journalistic). Each section is a shortlist; not exhaustive.

## ASR / transcription

- [whisper.cpp](https://github.com/ggerganov/whisper.cpp) — C++ port; CPU-friendly; supports a naive stereo-channel diarization approach
- [WhisperX](https://github.com/m-bain/whisperX) — Whisper + forced alignment + diarization wrapper
- [whisper-diarization](https://github.com/MahmoudAshraf97/whisper-diarization)
- [WhisperS2T](https://github.com/shashikg/WhisperS2T)
- [CrisperWhisper](https://github.com/nyrahealth/CrisperWhisper) — verbatim Whisper variant from nyra.health (see [[ai-psychotherapy-vendors]])
- [FunASR](https://github.com/modelscope/FunASR) — Alibaba ASR toolkit
- [voice-pro](https://github.com/abus-aikorea/voice-pro) — packaged Whisper-based tool
- [voize](https://www.voize.de/pysa) — German clinical-context speech recognition
- [HF Open ASR Leaderboard](https://huggingface.co/spaces/hf-audio/open_asr_leaderboard)
- [HF Spaces: dwarkesh/transcriber](https://huggingface.co/spaces/dwarkesh/transcriber)
- [awesome-whisper](https://github.com/sindresorhus/awesome-whisper) — curated index

## Diarization (who spoke when)

- [pyannote-audio](https://github.com/pyannote/pyannote-audio)
- [diart](https://github.com/juanmc2005/diart) — real-time diarization on top of pyannote
- [DiarizationLM](https://github.com/google/speaker-id/tree/master/DiarizationLM)
- [awesome-diarization](https://github.com/wq2012/awesome-diarization) — curated index
- [ML6 blog: choosing a diarization tool](https://blog.ml6.eu/who-spoke-when-choosing-the-right-speaker-diarization-tool-3d7a115c524b)
- [ML6 blog: labelling for accurate ASR](https://www.ml6.eu/blogpost/how-to-label-your-way-to-accurate-automatic-speech-recognition-asr)
- [Linguistics speaker-diarization tutorial](https://lingmethodshub.github.io/content/python/speaker-diarization-for-linguistics/)

### Multichannel / stereo notes

Two-microphone capture often beats single-channel diarization in cleanliness, when the room allows it.

- [Whisper discussion #585 — multichannel](https://github.com/openai/whisper/discussions/585)
- [pyannote-audio issue #915 — stereo](https://github.com/pyannote/pyannote-audio/issues/915)

## Pseudonymization

PII-stripping is an optional layer between transcription and downstream processing.

- [piiranha-v1-detect-personal-information](https://huggingface.co/iiiorg/piiranha-v1-detect-personal-information) — HF model for PII detection
- [Presidio analyzer — custom NLP models](https://microsoft.github.io/presidio/analyzer/customizing_nlp_models/) — Microsoft's PII framework

## Local LLM runtime (for summarisation / analysis on top)

- [Ollama library](https://ollama.com/library)
- [llamafile](https://github.com/Mozilla-Ocho/llamafile) — single-binary distribution
- [LocalScore](https://www.localscore.ai/download) — benchmarking local inference hardware

## Orchestration

- [DSPy](https://github.com/stanfordnlp/dspy) — declarative prompting / pipeline composition
- [morphik](https://docs.morphik.ai/introduction)

## Document OCR (where the source is PDF, not audio)

For session notes that already exist as scanned/exported PDFs. See [[ocr-pipeline]] for why multimodal-LLM-first is the wrong architecture; this section just collects implementations.

- [marker](https://github.com/VikParuchuri/marker) — PDF → markdown
- [swift-ocr-llm-powered-pdf-to-markdown](https://github.com/yigitkonur/swift-ocr-llm-powered-pdf-to-markdown) — explicit local-model mode

## Hardware

- [Open Earable](https://open-earable.teco.edu/) — open research-platform earable; on-list as a sensing/audio-input experiment
- Omnidirectional microphones for whole-room capture (typical setup in dyadic recording where one mic per speaker is not feasible)
- Reference workstation example: [Ryzen 7 7700X + RTX 4080 Super build](https://www.mifcom.de/workstation-ryzen-7-7700x-rtx-4080-super-id18377) — illustrative for "what does on-prem inference cost" sizing

## Adjacent

- [[ai-psychotherapy-vendors]] — products in the wild stitching this stack together for clinical use
- [[ai-psychotherapy-research-questions]] — open questions about accuracy, bias, and clinical validity of these tools
- [[ocr-pipeline]] — the document-side analogue of this audio pipeline
