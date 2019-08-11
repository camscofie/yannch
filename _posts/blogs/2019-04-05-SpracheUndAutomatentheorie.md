---
layout: post
title: Sprache und Automatentheorie
description: Formale Sprachen
category: blogs
---

## Formale Sprachen
### Definition
1. Ein endliches **Alphabet Σ** ist eine endliche Menge von Symbolen.
2. Eine endliche Folge von Symbolen aus Σ heißt **Wort** (über Σ). In der Regel ist die Variable für ein Wort w.
3. Die Menge aller Wörter über Σ heißt **Σ∗** . Das heißt w ∈ Σ∗.
4. Die Länge von w ist │w│.
5. Das **leere Wort** ε mit │ε│ = 0 ist ∈ Σ∗ (∀Σ)
6. Der Operator · bezeichne die **Konkatenation**, also Hintereinanderreihung, von Wörtern w1 . . . wn.
7. Eine (nicht! die) beliebige Menge L von Wörtern über einem Alphabet Σ, also L ⊂ Σ∗ heißt (formale) Sprache über Σ. (Eine Sprache beinhaltet nicht immer automatisch ε!)

### Definition 2
Seien L, L1 , L2 ⊂ Σ∗ Sprachen
1. Produktsprache: L1 · L2 := {w1 · w2 │ w1 ∈ L1, w2 ∈ L2}
2. k-faches Produkt: L^k := {w1·w2 ...·wk │wi ∈ L für 1 ≤ i ≤ k}; L0 = {ε}
3. Quotientensprache: L1/L2 := {w ∈ Σ∗ │∃z ∈ L2 mit w·z ∈ L1 }
4. Kleene’scher Abschluss: L∗ := U(i>=0)L^i = {w1 ·...· wn │wi ∈ L, n∈N0}
5. Positiver Abschluss: L+ := U(i>0)L^i
6. Komplementsprache: L^c := Σ∗ \L

## Reguläre Sprachen
+ **Jede Sprache, die von einem endlichen Automaten erkannt wird, ist regulär**

Eine Sprache L ⊆ Σ ∗ heißt regulär, wenn für sie einer der folgenden Punkte gilt: (induktive Deﬁnition)
+ Verankerung
  + L = {a} mit a ∈ Σ oder
  + L = ∅ oder
  + L = {ε}
+ Induktion: Seien L1 , L2 reguläre Sprachen
  + L = L1 · L2 oder
  + L = L1 ∪ L2 oder
  + L = L1^*

## Pumping-Lemma

### Pumping-Lemma für reguläre Sprache
Für jede reguläre Sprache L gibt es eine natürliche Zahl n, sodass gilt: Jedes Wort **w ∈ L mit │w│ >= n hat eine Zerlegung w = uvx** mit den folgenden drei Eigenschaften:

+ │uv│ <= n 
+ │v│ >= 1 
+ u(v^i)x ∈ L für alle i ∈ N

### Pumping-Lemma für kontextfreie Sprache
**w = uvxyz, mit │w│ >= n**
+ │vy│ > 0
+ │vxy│ < n
+ u(v^i)x(y^i)z ∈ L für alle i ∈ N

## Deterministische endliche Automaten(DEA)
Ein DEA (Q, Σ, δ, s, F) besteht aus:
+ Q, einer endlichen Menge von Zuständen
+ Σ, einer endlichen Menge von Eingabesymbolen, dem Eingabealphabet
+ δ : Q × Σ ⇒ Q, einer Übergangsfunktion
+ s ∈ Q, einem Startzustand
+ F ⊆ Q, einer Menge von Endzuständen

## Nichtdetermistische endliche Automaten(NEA)
Ein nichtdeterministischer endlicher Automat (NEA) besteht aus:
+ Q, einer endlichen Menge von Zuständen
+ Σ, einem endlichen Alphabet
+ δ : Q × (Σ ∪ {ε}) ⇒ 2^Q , wobei 2^Q die Potenzmenge (Menge aller Teilmengen) von Q darstellt
+ s ∈ Q, einem Startzustand
+ F ⊆ Q, einer Menge von Endzuständen

