---
layout: post
title: Asymmetirsche Authentifikation
description: ElGamal Signaturen
category: blogs
---

## Digitale Sinaturschemata
--------------------------------

+ (pk,sk) <- Gen(1^k) wie bei Public-Key-Verschluesselung.
+ Signieren: σ <- Sig(sk,M)
+ Verifizieren: Ver(pk,M,σ) = {0,1}

### Schema EUF-CMA-sicher:
_kein PPT-Angreifer A wins._
1. A has pk and access to Sig(sk,*)-Orakel
2. A gives (M*,σ*)
3. A wins, when Ver(pk,M*,σ*) = 1 and M* != M.
![alt text](/resources/postImage/asymmetirscheAuthentifikation/EUF-CMA.png)
## ElGamal-Signaturen
------------------------------------------

Es sei **G einen endliche zyklische Gruppe** und **g ein Erzeuger von G**:

+ **Gen**(1^k): Zieht ein x zufaellig und gibt als geheimen Schluessel sk = (G,g,x) und als oeffentlichen Schluessel: pk = (G,g,g^x) aus

+ **Sig**(sk,M): Waehle ein e zufaellig und setze a :=g^e. Berechne b als Loesung von a*x + e *b = M mod G. Die Signatur ist dann σ  = (a,b).

+ **Ver**(pk,M,σ=(a,b)): Gebe 1 aus, wenn (g^x)^a * a^b = g^M, sonst gebe 0 aus.

[Yange]:    http://camscofie.github.io  "Yange"
