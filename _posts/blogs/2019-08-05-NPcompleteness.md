---
layout: post
title: NP-completeness
description: Formale Sprachen
category: blogs
---

### Deﬁnition
Eine **polynomiale Transformation** einer Sprache L1 ⊆ Σ1∗ in eine Sprache L2 ⊆ Σ2∗ ist eine Funktion f : Σ1∗ → Σ2∗ mit den folgenden Eigenschaften:
1. Es existiert eine polynomiale deterministische Turing-Maschine, die f berechnet.
2. Für alle x ∈ Σ1^∗ gilt: x ∈ L1 ⇔ f(x) ∈ L2.

Wir schreiben dann **L1 ∝ L2** (L1 ist polynomial transformierbar in L2 ). Intuitiv bedeutet L1 ∝ L2 , dass L2 gleich schwierig oder schwieriger als L 1 ist. Damit deﬁnieren wir eine sehr wichtige Klasse von Sprachen:

### Deﬁnition
Eine Sprache L heißt **NP-vollständig**, wenn:
1. L ∈ NP
2. ∀L' ∈ NP : L' ∝ L