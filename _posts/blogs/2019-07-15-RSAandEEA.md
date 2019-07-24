---
layout: post
title: RSA Encryption and EEA
category: blogs
description: calculation
---

## [RSA Process](https://en.wikipedia.org/wiki/RSA_(cryptosystem))
-----------------------------------------

### RSA Key generation
1. choose P != Q, both prime
2. N = P x Q, λ(N) = (P-1)(Q-1)
3. pick e from (3,...,λ(N)-1), ggt(e,λ(N)) = 1
4. calculate d ≡ e^(−1) (mod λ(N)).         //d⋅e ≡ 1 (mod λ(n))
5. pk = (N,e); sk = (N,d)

### Encryption
c(m) ≡ m^(e) mod N

### Decryption
m(c) ≡ c^(d) mod N

------------------------------

#### Tricks zum Rechnen:
+ 51^2 mod 59 = (59-8)^2 mod 59 = (-8)^2 mod 59
+ 3^60 mod 59 = 3^(60 mod 58) mod 59 = 3^2 mod 59.    ## ord(G) ist 58, da 59 Prim

## [Extended Euclidean algorithm](https://en.wikipedia.org/wiki/Extended_Euclidean_algorithm)
----------------------------------------------

**Question**:
47x + 30y = 1

**forwards**:

47 = 30 x 1 + 17

30 = 17 x 1 + 13

17 = 13 x 1 + 4

13 =  4 x 3 + 1

**rewrite Rest**

1 = 13 - 3(4)

  = 13 - 3(17-13)

  = 4(13) - 3(17)

  = 4(30-17) - 3(17)

  = 4(30) - 7(17)

  = 4(30) - 7(47-30)

  = -7(47) + 11(30)

**x = -7, y = 11**





[Yange]:    http://camscofie.github.io  "Yange"
[1]:    {{ page.url}}  ({{ page.title }})
