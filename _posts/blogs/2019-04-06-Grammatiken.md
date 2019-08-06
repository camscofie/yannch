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

## Chomsky-Hierarchie
---------------------
Two important types are context-free grammars (Type 2) and regular grammars (Type 3). The languages that can be described with such a grammar are called context-free languages and regular languages, respectively. Although much less powerful than unrestricted grammars (Type 0), which can in fact express any language that can be accepted by a Turing machine, these two restricted types of grammars are most often used because parsers for them can be efficiently implemented.[8] For example, all regular languages can be recognized by a finite state machine, and for useful subsets of context-free grammars there are well-known algorithms to generate efficient LL parsers and LR parsers to recognize the corresponding languages those grammars generate.

1. Grammatiken ohne weitere Einschränkungen heißen **Grammatiken vom Typ 0**.
  + **言辞**：区别与grammar sensetive：{xAz -> xyz│A∈ N; x,z ∈ (N∪Σ)^*; and γ ∈ (N∪Σ)^+}，y 可以为空值
2. Grammatiken, bei denen alle Ableitungsregeln die unten gestellte Form haben, heißen **kontextsensitiv** oder **Grammatiken vom Typ 1**
  * u → v mit u ∈ V^+ , v ∈ ((V ∪ Σ)\{S})^+ und │u│ ≤ │v│, oder
  * S→ε
+ **言辞**：与grammar free的区别：{xAz -> xyz│A∈ N; x,z ∈ (N∪Σ)^*; and γ ∈ (N∪Σ)^+}。 变量A变成string y，只在input 前后有string x 和 z 的情况下。
3. Grammatiken, bei denen alle Ableitungsregeln die Form A → v mit A ∈ V und v ∈ (V∪Σ)^∗ haben, heißen **kontextfrei** oder **Grammatiken vom Typ 2**
+ **言辞**： production 等式左边只有一个 non-terminal 变量
4. Grammatiken, bei denen alle Ableitungsregeln die Form A → v mit A ∈ V und v = ε oder v = aB für a ∈ Σ, B ∈ V haben, heißen **rechtslinear( regular languages)** oder **Grammatiken vom Typ 3**.
+ **言辞**：左边如上，右边 （可以为空值││单个terminal 变量││单个terminal 变量 + non-terminal 变量）




## CYK algorithm

CYK algorithm is a parsing algorithm for context-free grammars, it can calculate if giving string can be represented in the giving context-free grammers in O(n^3).

```
let the input be a string I consisting of n characters: a1 ... an.
let the grammar contain r nonterminal symbols R1 ... Rr, with start symbol R1.
let P[n,n,r] be an array of booleans. Initialize all elements of P to false.
for each s = 1 to n
  for each unit production Rv → as
    set P[1,s,v] = true
for each l = 2 to n -- Length of span
  for each s = 1 to n-l+1 -- Start of span
    for each p = 1 to l-1 -- Partition of span
      for each production Ra  → Rb Rc
        if P[p,s,b] and P[l-p,s+p,c] then set P[l,s,a] = true
if P[n,1,1] is true then
  I is member of language
else
  I is not member of language
```

![alt text](../../resources/postImage/Grammatiken/CYK_algorithm_animation_showing_every_step_of_a_sentence_parsing.jpg)
