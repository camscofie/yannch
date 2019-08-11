---
layout: post
title: Grundbegriffe der Informatik
description: Wörter, Formale Sprachen, Reguläre Ausdrücke, Endliche Automaten, Kontextfreie Grammatiken
category: blogs
---

## Wörter
--------------------
1. Ein endliches **Alphabet Σ** ist eine endliche Menge von Symbolen.
2. Eine endliche Folge von Symbolen aus Σ heißt **Wort** (über Σ). In der Regel ist die Variable für ein Wort w.
3. Die Menge aller Wörter über Σ heißt **Σ∗** . Das heißt w ∈ Σ∗.
4. Die Länge von w ist │w│.
5. Das **leere Wort** ε mit │ε│ = 0 ist ∈ Σ∗ (∀Σ)
6. Der Operator · bezeichne die **Konkatenation**, also Hintereinanderreihung, von Wörtern w1 . . . wn.
7. Eine (nicht! die) beliebige Menge L von Wörtern über einem Alphabet Σ, also L ⊂ Σ∗ heißt (formale) Sprache über Σ. (Eine Sprache beinhaltet nicht immer automatisch ε!)

## Formale Sprachen
--------------------
**Eine formale Sprache L über einem Alphabet Σ ist eine Teilmenge L ⊆ Σ∗ .**
Seien L, L1 , L2 ⊂ Σ∗ Sprachen
1. Produktsprache: L1 · L2 := {w1 · w2 │ w1 ∈ L1, w2 ∈ L2}
2. k-faches Produkt: L^k := {w1·w2 ...·wk │wi ∈ L für 1 ≤ i ≤ k}; L0 = {ε}
3. Quotientensprache: L1/L2 := {w ∈ Σ∗ │∃z ∈ L2 mit w·z ∈ L1 }
4. Kleene’scher Abschluss: L∗ := U(i>=0)L^i = {w1 ·...· wn │wi ∈ L, n∈N0}
5. Positiver Abschluss: L+ := U(i>0)L^i
6. Komplementsprache: L^c := Σ∗ \L

## Reguläre Sprachen
--------------------
**Jede Sprache, die von einem endlichen Automaten erkannt wird, ist reguläre**

Eine Sprache L ⊆ Σ ∗ heißt regulär, wenn für sie einer der folgenden Punkte gilt: (induktive Deﬁnition)
+ Verankerung
  + L = {a} mit a ∈ Σ oder
  + L = ∅ oder
  + L = {ε}
+ Induktion: Seien L1 , L2 reguläre Sprachen
  + L = L1 · L2 oder
  + L = L1 ∪ L2 oder
  + L = L1^*

### Pumping-Lemma

#### Pumping-Lemma für reguläre Sprache
Für jede reguläre Sprache L gibt es eine natürliche Zahl n, sodass gilt: Jedes Wort **w ∈ L mit │w│ >= n hat eine Zerlegung w = uvx** mit den folgenden drei Eigenschaften:

+ │uv│ <= n 
+ │v│ >= 1 
+ u(v^i)x ∈ L für alle i ∈ N

#### Pumping-Lemma für kontextfreie Sprache
**w = uvxyz, mit │w│ >= n**
+ │vy│ > 0
+ │vxy│ < n
+ u(v^i)x(y^i)z ∈ L für alle i ∈ N

## Kontextfreie Grammatiken
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

## Automathen
--------------------

### Deterministische endliche Automaten(DEA)
Ein DEA (Q, Σ, δ, s, F) besteht aus:
+ Q, einer endlichen Menge von Zuständen
+ Σ, einer endlichen Menge von Eingabesymbolen, dem Eingabealphabet
+ δ : Q × Σ ⇒ Q, einer Übergangsfunktion
+ s ∈ Q, einem Startzustand
+ F ⊆ Q, einer Menge von Endzuständen

### Nichtdetermistische endliche Automaten(NEA)
Ein nichtdeterministischer endlicher Automat (NEA) besteht aus:
+ Q, einer endlichen Menge von Zuständen
+ Σ, einem endlichen Alphabet
+ δ : Q × (Σ ∪ {ε}) ⇒ 2^Q , wobei 2^Q die Potenzmenge (Menge aller Teilmengen) von Q darstellt
+ s ∈ Q, einem Startzustand
+ F ⊆ Q, einer Menge von Endzuständen

### Äquivalenz von NEA’s und DEA’s
+ Zwei endliche Automaten, die dieselbe Sprache akzeptieren, heißen äquivalent.
+ Zu jedem nichtdeterministischen endlichen Automaten gibt es einen äquivalenten deterministischen endlichen Automaten.

### Minimierung von Automaten
+ Zustände eines (deterministischen) endlichen Automatens, die vom Anfangszustand aus nicht erreichbar sind, heißen **überﬂüssig**.
+ Die Menge aller überﬂüssigen Zustände eines (deterministischen) endlichen Automaten kann in der Zeit O(│Q│·│Σ│) berechnet werden. (DFS)
+ Der Äquivalenzklassenautomat A≡ zu einem deterministischen endlichen Automaten A ohne überﬂüssige Zustände ist minimal.

### Rechtsinvarianz und Index
+ Eine Äquivalenzrelation R über Σ∗ heißt rechtsinvariant, wenn für alle x , y ∈ Σ ∗ gilt: falls x R y so gilt auch xz R yz für alle z ∈ Σ∗
+ Den Index von R bezeichnen wir mit ind(R); er ist die Anzahl der Äquivalenzklassen von Σ∗ bezüglich R.
  
#### Nerode–Relation Rl
+ Für eine Sprache L ⊆ Σ∗ ist die Nerode–Relation Rl deﬁniert durch: für x , y ∈ Σ ∗ ist x R L y genau dann wenn (xz ∈ L ⇔ yz ∈ L) für alle z ∈ Σ∗ gilt.