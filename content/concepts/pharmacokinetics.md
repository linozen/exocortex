---
title: Pharmacokinetics
description: What the body does to the drug — absorption, distribution, metabolism, excretion (ADME). The "exposure" half of pharmacology; pairs with pharmacodynamics ("what the drug does to the body").
tags:
  - concept
  - pharmacology
author: claude-opus-4-7
authored_on: 2026-06-08
sources: []
certainty: A
certainty_notes: "Tier A for the ADME framework and half-life / bioavailability definitions (standard pharmacology textbook material). Tier B for CYP-system specifics — re-verify against current literature for drug-drug interaction claims that have clinical consequences."
---

Pharmacokinetics (PK) is the study of **what the body does to the drug** — how it enters, moves through, is transformed by, and leaves the body. Summarised by the **ADME framework**: Absorption, Distribution, Metabolism, Excretion. Its complement is [[pharmacodynamics]], which is what the drug does to the body.

## ADME

### Absorption

How the drug gets from the dosing site into systemic circulation. Route matters:

- **Oral** — has to survive stomach acid, gut wall, and the **first-pass effect** (the liver's first metabolic shot at anything absorbed through the portal vein).
- **IV** — bypasses absorption entirely; 100% bioavailability by definition.
- **Inhaled / nasal / sublingual / rectal** — partial or complete bypass of first-pass.
- **Transdermal** — slow, sustained, bypasses first-pass.

**Bioavailability** (F) — the fraction of dose that reaches systemic circulation. IV F = 1; oral F varies dramatically (caffeine ~1.0, lithium ~1.0, propranolol ~0.3 due to first-pass).

### Distribution

Once in the bloodstream, the drug partitions across compartments. The summary scalar is the **volume of distribution** (V_d):

$$V_d = \frac{\text{total drug in body}}{\text{plasma concentration}}$$

V_d is a pharmacokinetic abstraction — it has units of volume but no physical meaning beyond "how much plasma you'd need to dissolve the dose at the measured concentration." Lipophilic drugs that pool in fat have huge V_d (chloroquine ~13,000 L); drugs confined to plasma have small V_d (warfarin ~10 L).

Protein binding matters: only free (unbound) drug crosses membranes and binds receptors. Highly protein-bound drugs have most of their plasma concentration sequestered.

### Metabolism

Mostly hepatic, mostly cytochrome P450 (CYP) enzymes. **Phase I** reactions (oxidation, reduction, hydrolysis) typically inactivate the drug or prepare it for Phase II. **Phase II** (conjugation — glucuronidation, sulfation) makes it more water-soluble for excretion.

CYP polymorphism is the biggest source of individual variability:

- CYP1A2 metabolises [[caffeine]]; slow metabolisers experience longer half-life and stronger effects.
- CYP2D6 metabolises ~25% of prescribed drugs; "poor", "intermediate", "extensive", and "ultra-rapid" phenotypes produce dramatic clinical differences.
- CYP3A4 is the workhorse for ~50% of drugs and is inducible (St John's wort) and inhibitable (grapefruit juice).

Drug-drug interactions mediated by CYP induction or inhibition are a major source of preventable harm.

### Excretion

Mostly renal (urine), partly hepatic (bile → feces), small contributions from sweat, breast milk, exhaled air. Renal clearance combines glomerular filtration, tubular secretion, and tubular reabsorption. Renal impairment is a major reason for dose adjustment.

## Half-life and steady state

**Half-life** (t₁/₂) — time for plasma concentration to halve. For first-order kinetics (most drugs at therapeutic doses), half-life is constant regardless of starting concentration.

- After **4–5 half-lives**, ~94–97% of the drug is eliminated — clinical "washout" reference.
- After **4–5 half-lives of repeated dosing**, plasma reaches **steady state** — the rate in equals the rate out.

[[caffeine]] has t₁/₂ of 3–5 hours in healthy adults — so the afternoon coffee is still substantially present at bedtime, which is the substrate for sleep-architecture disruption even when subjective alertness has faded.

## What pharmacokinetics does not explain

PK describes how the drug gets to the receptor and how long it stays. It says nothing about what happens once it's bound — that's [[pharmacodynamics]]. A perfect PK profile delivering a drug with no receptor effect does nothing clinically.

## Adjacent

- [[pharmacodynamics]] — the complementary half
- [[caffeine]] — worked example: oral bioavailability ~1.0, CYP1A2 metabolism, 3–5 h half-life
- [[psychedelics]] — PK shapes the experience curve (psilocybin's 4–6 h trip is its half-life × duration of receptor occupancy)
