---
title: Substitution model & evaluation order
description: A simplified mental model for what procedure application means — and the two orders (applicative, normal) in which arguments can be reduced.
tags:
  - concept
  - programming
  - computer-science
  - functional-programming
author: Linus Sehn
authored_on: 2026-06-08
sources:
  - "[[abelson2002]]"
certainty: A
certainty_notes: "Tier A — direct extraction from SICP §1.1 (Abelson & Sussman). The substitution model is explicitly disclaimed in the book as not how real interpreters work; it is a teaching device."
---

The substitution model is a deliberately naive answer to the question "what does it mean to apply a procedure?" It says: to evaluate a procedure call, take the procedure body, replace each formal parameter with the corresponding argument, and reduce. It is not how interpreters actually work — the real story involves environments — but it is enough to reason about correctness of pure (side-effect-free) code, and it makes evaluation order visible.

## Applicative-order evaluation

Evaluate the arguments first, then substitute. This is what most modern languages do (Scheme, Python, Java, JavaScript).

```scheme
(f 5)
;; evaluate arguments first
(sum-of-squares (+ 5 1) (* 5 2))
(sum-of-squares 6 10)
;; then substitute into the body
(+ (square 6) (square 10))
(+ 36 100)
136
```

## Normal-order evaluation

Fully expand first, reduce later. Each argument is substituted *as an expression*, unevaluated, and only forced when needed.

```scheme
(f 5)
(sum-of-squares (+ 5 1) (* 5 2))
(+ (square (+ 5 1)) (square (* 5 2)))
(+ (* (+ 5 1) (+ 5 1)) (* (* 5 2) (* 5 2)))
(+ (* 6 6) (* 10 10))
136
```

## Why the distinction matters

For pure expressions both orders produce the same result. They diverge when:

- **Side effects are present.** Applicative order forces every argument exactly once; normal order may force the same argument multiple times (re-evaluating `(+ 5 1)` above) or zero times. Languages with side effects pick applicative for predictability.
- **Termination differs.** Normal order can succeed where applicative diverges, because it never evaluates arguments the body does not use. This is the basis of lazy evaluation: `(if (= n 0) 1 (/ x n))` terminates safely under normal order even when `(/ x n)` would have failed.
- **Cost differs.** Naive normal order re-evaluates arguments on every reference. Lazy languages (Haskell) bolt on memoisation to make it tractable — the result is *call-by-need*, a third option between the two.

## Adjacent

- [[higher-order-procedures]] — procedures as values, the next abstraction step from the substitution model
- [[abstraction-barriers]] — where the substitution model stops being enough and environments take over
