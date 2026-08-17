---
title: Selection bias
description: When the sample reaching the analyst is filtered by a non-random mechanism, conclusions about the source population are systematically wrong — independent of sample size.
tags:
  - epistemology
  - concept
  - methodology
  - statistics
  - epidemiology
author: Linus Sehn | claude-opus-4-7
authored_on: 2026-06-07
sources: []
certainty: B
certainty_notes: "Tier B — standard methodology concept; phrased from general statistics-training recall, not from a specific cited source in this session."
---

Selection bias arises when the process that determines who ends up in your sample is correlated with the outcome you are trying to measure. The result is that the sample is not representative of the source population on the very dimension of interest — and no amount of additional data of the same kind fixes it. Larger samples make biased estimates more *precise*, not more *accurate*.

## How it differs from sampling error

Sampling error shrinks with sample size; selection bias does not. Sampling error is noise around the true population value; selection bias is a systematic shift away from it. The two are routinely confused because both reduce the trustworthiness of an estimate, but the remedies are different — random sampling addresses sampling error, while selection bias requires fixing the *recruitment mechanism* or modelling the filter explicitly.

## Common mechanisms

- **Self-selection.** Participants opt in. People who answer political surveys differ from those who do not; people who fill out post-purchase reviews differ from those who do not.
- **Survivorship.** Only "successful" cases remain visible to be sampled. Surveying successful startups about their habits ignores the failed startups that had identical habits.
- **Referral / gatekeeping.** A clinician, recruiter, or algorithm decides who reaches the sample frame, and their criteria are correlated with the outcome.
- **Loss to follow-up.** Long-running studies preferentially lose participants whose outcomes diverge from expectations, biasing the remaining sample.
- **Berkson's bias.** Two unrelated conditions appear correlated within a clinical sample because each independently raises the chance of being in the sample.

## Examples

- Wartime aircraft armouring: examining the bullet-hole distribution on planes that returned and reinforcing those regions — Abraham Wald's insight was that the planes that *didn't* return were the missing sample, and the unhit regions of returning planes were the ones to armour.
- Mental-illness diagnosis statistics filtered through help-seeking behaviour — see [[gender-differences-in-mental-illness]].
- Job-applicant pool filtered by recruiter pre-screening — measured hire-rate-by-trait is not population trait distribution.
- Online reviews — opt-in skews toward extreme experiences.

## What to do about it

The honest moves are (a) characterise the selection mechanism explicitly and report what populations the conclusions do and do not generalise to, (b) where possible, sample at a stage *upstream* of the filter (community samples instead of clinical samples; intent-to-treat instead of completers-only), and (c) when neither is possible, use techniques that model the selection process directly (inverse probability weighting, Heckman correction).

## Adjacent

- [[cognitive-illusions]] — the cognitive analogue is the base-rate fallacy: ignoring how the sample was filtered when reading off rates
- [[hawthorne-effect]] — a measurement effect rather than a selection effect, but in the same family of "the sample reaching the analyst is shaped by the act of measurement"
- [[correlation]] — selection can manufacture spurious correlation (Berkson) and erase real ones
- [[gender-differences-in-mental-illness]] — worked example
