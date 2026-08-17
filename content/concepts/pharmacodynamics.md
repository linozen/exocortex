---
title: Pharmacodynamics
description: What the drug does to the body — receptor binding, dose-response, mechanism of action. The "effect" half of pharmacology; pairs with pharmacokinetics ("the body's processing of the drug").
tags:
  - concept
  - pharmacology
author: claude-opus-4-7
authored_on: 2026-06-08
sources: []
certainty: A
certainty_notes: "Tier A for definitions and the ADME / dose-response framework (standard pharmacology textbook material; Goodman & Gilman canonical). Tier B for cross-references to specific receptor systems — re-verify against current literature when claims become clinically actionable."
---

Pharmacodynamics (PD) is the study of **what the drug does to the body** — receptor binding, downstream signaling, and the dose-response relationship. Its complement is [[pharmacokinetics]], which is what the body does to the drug.

## The receptor model

Most clinically used drugs act by binding to specific receptors (G-protein-coupled receptors, ion channels, enzymes, nuclear receptors, transporters). Binding kinetics distinguish:

- **Agonist** — binds and activates the receptor, producing the natural ligand's effect. _Full agonists_ produce the maximum possible response; _partial agonists_ produce less even at saturation.
- **Antagonist** — binds without activating, blocking the natural ligand. Competitive antagonists can be displaced by high agonist concentrations; non-competitive cannot.
- **Inverse agonist** — binds and produces the opposite of the agonist effect (relevant where the receptor has constitutive activity).
- **Allosteric modulator** — binds at a site other than the orthosteric one, shifting the receptor's response to natural ligands up (positive) or down (negative).

[[caffeine]] is a clean teaching example: a non-selective competitive antagonist at [[adenosine]] A1 and A2A receptors. The stimulant effect is _disinhibition_, not direct excitation.

## Dose-response

Two scalar properties dominate clinical reasoning:

- **Efficacy** — the maximum effect a drug can produce (E_max). A partial agonist has lower efficacy than a full agonist by definition.
- **Potency** — the concentration required for half-maximal effect (EC₅₀ or, for therapeutic effect, ED₅₀). Higher potency = lower required dose. **Potency does not imply better outcomes** — it just specifies where on the dose axis the response sits.

The dose-response curve is typically sigmoidal on log-dose scale; the slope reflects receptor cooperativity. The **therapeutic window** is the gap between the dose that produces useful effect (ED₅₀) and the dose that produces unacceptable harm (TD₅₀ or LD₅₀); the ratio is the **therapeutic index**.

## Tolerance and desensitization

Repeated exposure to many drugs reshapes the receptor population:

- **Downregulation** — chronic agonist exposure reduces receptor density.
- **Upregulation** — chronic antagonist exposure (or natural-ligand deprivation) increases receptor density.
- **Desensitization** — receptors become less responsive at the same density (e.g. β-arrestin internalization of GPCRs).

This is the substrate for [[caffeine-withdrawal]] (A1/A2A upregulation), opioid tolerance (μ-opioid receptor desensitization), and psychedelic tolerance (5-HT2A downregulation, see [[psychedelics]]).

## What pharmacodynamics does not explain

PD describes the *effect once the drug reaches the receptor*. It says nothing about:

- How the drug gets there (absorption, distribution — see [[pharmacokinetics]]).
- How long it stays there (half-life, clearance — also pharmacokinetics).
- How individual patients differ (genotype, age, comorbidity — both PK and PD).

A drug with perfect pharmacodynamics fails if the pharmacokinetics don't deliver it to the right tissue at the right concentration.

## Adjacent

- [[pharmacokinetics]] — the complementary half
- [[caffeine]] — worked example: A1/A2A antagonism
- [[psychedelics]] — 5-HT2A agonism and tolerance
