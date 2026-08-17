---
title: Jevons' paradox
description: Efficiency gains in resource use tend to increase, not decrease, total consumption of that resource — because the efficiency drop lowers effective price and demand expands more than the per-unit reduction.
tags:
  - concept
  - economics
  - meta-crisis
author: claude-opus-4-7
authored_on: 2026-06-08
sources: []
certainty: A
certainty_notes: "Tier A for Jevons' original observation and the price-elasticity mechanism (*The Coal Question*, 1865; standard energy-economics literature). Tier B for modern rebound-effect magnitudes — empirical estimates vary substantially by domain and methodology. Tier C for the AI / data-centre extrapolation, where the qualitative pattern is clear but the steady-state numbers are not yet settled."
---

Jevons' paradox is the empirical regularity that **efficiency improvements in the use of a resource tend to increase, not decrease, that resource's total consumption** — because the efficiency gain lowers the effective price of the service the resource provides, and the resulting demand expansion outweighs the per-unit reduction.

## Jevons on coal

William Stanley Jevons, *The Coal Question* (1865). The contemporary argument held that James Watt's more efficient steam engines would slow British coal depletion. Jevons observed the opposite: each gain in engine efficiency made coal-powered industry viable for new applications — railways, ships, more factories, more processes — and *total* coal consumption rose. Efficiency turned coal from an input for one industry into an input for many.

> "It is wholly a confusion of ideas to suppose that the economical use of fuel is equivalent to a diminished consumption. The very contrary is the truth."

## Mechanism

1. Efficiency improvement reduces the resource cost per unit of service.
2. The service becomes cheaper at the margin.
3. Cheaper service is demanded in greater quantity (price elasticity > 0).
4. If the demand expansion exceeds the per-unit efficiency gain, total resource use rises.

The paradox is conditional on **demand elasticity**. Inelastic, saturated-demand cases (residential refrigeration once every home has a fridge) show small or zero rebound. Elastic cases — new industrial applications, new geographies, new use-cases unlocked by the cost drop — show large or full rebound.

## Rebound effect taxonomy

The modern energy-economics literature decomposes the response:

- **Direct rebound** — the same agent uses more of the now-cheaper service (driving farther in a more efficient car).
- **Indirect rebound** — money saved on the cheaper service is spent on other resource-intensive goods.
- **Economy-wide rebound** — the efficiency gain propagates through input-output linkages to the whole economy, often accelerating growth and so resource throughput.

The strong-form claim that economy-wide rebound exceeds 100% — so total consumption rises — is the **Khazzoom–Brookes postulate**. Empirically, direct rebound for most consumer services is 5–30%, indirect adds another 10–30%, and economy-wide effects are hard to measure but plausibly push the total close to or above 100% over long horizons.

## Modern instances

- **LED lighting** — per-lumen electricity ~10× lower than incandescent, but lumen output per capita has risen by a similar factor since the 1990s (architectural over-lighting, screens, urban displays). Total lighting electricity flat or rising in most jurisdictions.
- **Fuel-efficient vehicles** — direct rebound 10–30% (more miles driven), plus induced traffic where road capacity is the binding constraint. CAFE-style standards reduce per-mile emissions but increase total miles.
- **Compute and AI** — Moore's Law, Koomey's Law, and transformer-efficiency gains have each been followed by demand expansion (cloud, mobile, ML training, inference at scale). The 2024–2026 data-centre electricity build-out is the textbook case: every efficiency milestone has been absorbed by larger models, longer training runs, and inference-time scaling. See [[ai-energy-consumption]].
- **Agriculture** — Borlaug-style yield improvements coexist with rising total land cultivation in many regions (partially offset by land spared elsewhere; the net balance is contested).

## What Jevons does not claim

The paradox describes a *frequent* outcome of efficiency gains, not a universal one. Counter-examples:

- **Saturation** — once demand for a service is structurally capped (one fridge per kitchen), efficiency gains do reduce total consumption.
- **Decoupling** — when the efficiency gain shifts the service to a different resource (heat pumps move heating from gas to electricity), the *original* resource sees genuine demand destruction even if total energy use changes little.
- **Hard regulation** — caps, rationing, or carbon budgets that bind absolute throughput prevent demand from absorbing the gain.

Policy implication: efficiency mandates alone are insufficient for absolute reductions. They need to be paired with **price floors, caps, or rationing**. EU ETS cap-and-trade is one design that respects this; carbon pricing without a cap is structurally vulnerable to Jevons dynamics. The [[degrowth]] critique of green-growth narratives is essentially a Jevons argument applied at civilisational scale.

## Adjacent

- [[induced-demand]] — the spatial / transport instance of the same mechanism
- [[ai-energy-consumption]] — the current high-stakes instance
- [[degrowth]] — the policy response that rejects efficiency-as-solution
- [[attention]] — analogue in the attention economy: cheaper content production has expanded consumption rather than freed time
