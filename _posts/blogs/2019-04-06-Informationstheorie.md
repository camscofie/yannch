---
layout: post
title: Informationstheorie
description: Informationstheorie - Einführung
category: blogs
---

## Deﬁnition von Information
Information I: des Auftretens eines Zeichens k
+ Information soll nie negativ sein: I ≥ 0
+ Ein sicheres Ereignis soll keine Information liefern: Pr[(Pi = 1)] ⇒ I = 0
+ Information soll stetig sein
+ Die Information einer Zeichenkette soll gleich der Summe der Einzelinformationen sein: I(pi·pj) = I(pi) + I(pj)

Sei p eine Wahrscheinlichkeit, die Information von p zur Basis b ist deﬁniert als:

I(p) = − log b (p).

In TGI verwenden wir immer b = 2

+ 为什么有一个负号
  其中，负号是为了确保信息一定是正数或者是0，总不能为负数吧！
+ 为什么底数为2
  是因为，我们只需要信息量满足低概率事件x对应于高的信息量。那么对数的选择是任意的。我们只是遵循信息论的普遍传统，使用2作为对数的底！

## Entropie (entropy, 熵)
* 假设存在一个随机变量 x, 当我们被告知一个极不可能发生的事情发生了，那我们就接收到了更多的信息；而当我们观测到一个非常常见的事情发生了，那么我们就接收到了相对较少的信息量。因此信息的量度应该依赖于概率分布 p(x), **所以说熵 h(x) 的定义应该是概率的单调函数**

* 如果我们有俩个不相关的事件x和y，那么我们观察到的俩个事件同时发生时获得的信息应该等于观察到的事件各自发生时获得的信息之和，即：

h(x,y) = h(x) + h(y)

* 由于x，y是俩个不相关的事件，那么满足

p(x,y) = p(x)*p(y).

* 我们很容易看出h(x)一定与p(x)的对数有关（因为只有对数形式的真数相乘之后，能够对应对数的相加形式）。因此我们有信息量公式如下：

h(x) = -log2 p(x)

+ 最后，我们用熵来评价整个随机变量 x 平均的信息量，而平均最好的量度就是随机变量的期望，即熵的定义如下：

**H(x) = -sum(p(x)*log2(p(x)))**
