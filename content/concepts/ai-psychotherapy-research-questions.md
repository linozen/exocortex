---
title: Forschungsfragen — KI in der Psychotherapie
description: Offene Forschungsfragen zur Anwendung von ASR/NLP/Sentiment-Analyse auf Therapiesitzungstranskripte — Genauigkeit, Validität, Prozessmodellierung, Ethik
tags:
  - concept
  - ai
  - psychotherapy
  - research-questions
author: Linus Sehn
authored_on: 2026-06-07
sources: []
certainty: B
certainty_notes: "Tier B — eigene Fragenliste aus 2024–2025, formuliert im Kontext von Markt- und Tooling-Recherche. Keine Literaturverankerung pro Frage; sollte mit aktuellem Forschungsstand abgeglichen werden, bevor irgendetwas davon zitiert wird."
---

Offene Fragen rund um den Einsatz von ASR, NLP und KI-gestützter Analyse auf Therapiesitzungs-Material. Notiert auf Deutsch, weil so formuliert und in deutschem klinischen Kontext gedacht.

## Präzision und Validität automatisierter Transkriptionen

**Frage:** Wie genau sind KI-generierte Transkriptionen im Vergleich zu menschlich erstellten Transkripten in der klinischen Psychotherapie?

**Kontext:** Tools wie **Whisper** im Vergleich zu manuellen Transkriptionen — Präzision bei Fachterminologie und Non-Standard-Sprache, Vollständigkeit (Lücken, Fehler).

## Automatisierte Emotionserkennung im therapeutischen Kontext

**Frage:** Welche Accuracy haben KI-gestützte Sentiment-Analysemethoden bei der Identifikation emotionaler Zustände im Vergleich zu menschlichen Bewertungen?

**Kontext:** Sentimentanalyse (VADER, BERT) zur automatischen Erkennung emotionalen Ausdrucks; Vergleich mit manuell durch Therapeut\*innen erstellten Analysen.

## Erkennung therapie-relevanter Themen in Sitzungsprotokollen

**Frage:** In welchem Ausmaß können KI-Modelle durch Topic Modeling wiederkehrende Themen und Themenwechsel im therapeutischen Prozess erkennen?

**Kontext:** NLP-Techniken zur Identifikation von Themenclustern (Angst, Trauma, Selbstwert). Manuell codierte Sitzungen als Vergleichsdatensatz.

## Modellierung des Therapieprozesses durch NLP-basierte Textanalysen

**Frage:** Wie realistisch sind durch KI modellierte Phasen von Veränderungsprozessen innerhalb therapeutischer Sitzungen (z. B. Gestalttherapie oder CBT)?

**Kontext:** NLP zur Identifikation narrativer/sprachlicher Strukturen, die in verschiedenen Therapiephasen auftreten (Problemexploration, Konfrontation, Lösungsfindung).

## Automatisierte Evaluation von Therapeut\*innen-Interventionen

**Frage:** Inwieweit können KI-gestützte Systeme die Qualität und Effizienz von Therapeut\*innen-Interventionen durch quantitative Textanalysen messen?

**Kontext:** Bewertung therapeutischer Interventionen via Dialogsequenzanalyse — wie oft und wann setzen Therapeut\*innen spezifische Fragen oder Interventionen ein (z. B. Motivierende Gesprächsführung, Paraphrasierung).

## Vorhersage von Therapieerfolg

**Frage:** Inwieweit lassen sich **Sprach- und Inhaltsmerkmale** von Therapiesitzungstranskripten als **Prädiktoren** für **Therapieerfolg** mittels NLP und Machine Learning identifizieren?

**Kontext:** Unabhängige Variablen: NLP-Merkmale aus Transkripten (Wortwahl, Emotionen, Themen). Abhängige Variable: messbarer Therapieerfolg (Veränderung in psychometrischen Tests, subjektive Verbesserung, klinische Einschätzung). Ziel: prädiktive Modelle aus sprachlich-inhaltlichen Merkmalen.

## Therapie-Fortschritts-Monitoring durch Sprachmusteranalyse

**Frage:** Kann eine automatische Analyse der Sprachmuster von Patient\*innen Hinweise auf Fortschritt oder Rückschritt liefern?

**Kontext:** Sprachliche Veränderungen während eines Therapieprozesses (z. B. vermehrter Gebrauch positiver Ausdrucksweisen) als mögliche Fortschrittsindikatoren.

## Datenschutz und Ethik

**Frage:** Welche ethischen Herausforderungen und datenschutzrechtlichen Bedenken entstehen bei automatisierter KI-Analyse von Therapiedaten?

**Kontext:** Datensicherheit, Privatsphäre, Vertrauen in die Technologie — speziell bei vertraulichen Therapieinhalten.

## Akzeptanz bei Psychotherapeut\*innen

**Frage:** Wie akzeptieren Psychotherapeut\*innen automatisierte Analysetools zur Transkription und klinischen Auswertung ihrer Sitzungen?

**Kontext:** Qualitative Forschung zu **Akzeptanz** und **Vertrauenswürdigkeit** — werden solche Tools als Unterstützung klinischer Entscheidungen verstanden oder als Bedrohung?

## Verwandt

- [[ai-psychotherapy-vendors]] — Anbieter, die implizit Antworten auf diese Fragen verkaufen
- [[local-speech-stack]] — die technischen Komponenten, deren Genauigkeit/Bias diese Fragen messen wollen
- [[llm-critique]] — Querverbindung zu allgemeinen Vorbehalten gegenüber LLM-basierten Werkzeugen
- [psyndex.de/tests/testarchiv](https://psyndex.de/tests/testarchiv/) — Testarchiv, relevant für die Outcome-Operationalisierung der Erfolgs-Frage
