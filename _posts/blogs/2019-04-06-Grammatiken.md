---
layout: post
title: Grammatiken und die Chomsky-Hierarchie
description: Kontextfreie Grammatik
category: blogs
---

## Grammatik
--------------------
Eine Grammatik G besteht aus vier Komponenten (auch etwas unübersichtlich als 4-Tupel G = (Σ, V, S, R) geschrieben):
+ Ein endliches Alphabet Σ mit den Terminalsymbolen, auch Terminalalphabet genannt
+ Eine endliche Menge V von Variablen, auch Nichtterminale genannt, wobei Σ ∩ V = ∅ gelten muss.
+ Dem Startsymbol S ∈ V
+ Eine endliche Menge von Ableitungsregeln R, auch Produktionen genannt. Eine Ableitungsregel ist ein paar (l,r), mit l ∈ (V ∪ Σ)^+ und r ∈ (V ∪ Σ)^∗ . Wir werden meistens l → r schreiben.

```
Σ = {), (, a, +, ∗}

V = {S}

R = {S → (S) + (S), S → (S) ∗ (S), S → a, S → a + a, S → a ∗ a}
```

### Chomsky-Hierarchie
---------------------
1. Grammatiken ohne weitere Einschränkungen heißen **Grammatiken vom Typ 0**.
2. Grammatiken, bei denen alle Ableitungsregeln die unten gestellte Form haben, heißen **kontextsensitiv** oder **Grammatiken vom Typ 1**
  * u → v mit u ∈ V^+ , v ∈ ((V ∪ Σ)\{S})^+ und │u│ ≤ │v│, oder
  * S→ε
3. Grammatiken, bei denen alle Ableitungsregeln die Form A → v mit A ∈ V und v ∈ (V∪Σ)^∗ haben, heißen **kontextfrei** oder **Grammatiken vom Typ 2**
4. Grammatiken, bei denen alle Ableitungsregeln die Form A → v mit A ∈ V und v = ε oder v = aB für a ∈ Σ, B ∈ V haben, heißen **rechtslinear** oder **Grammatiken vom Typ 3**.