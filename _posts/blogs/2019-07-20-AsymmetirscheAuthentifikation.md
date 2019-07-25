---
layout: post
title: Asymmetirsche Authentifikation
description: ElGamal Signaturen
category: blogs
---

## Digitale Sinaturschemata
--------------------------------

+ (pk,sk) <- Gen(1^k) wie bei Public-Key-Verschlüsselung.
+ Signieren: σ <- Sig(sk,M)
+ Verifizieren: Ver(pk,M,σ) = {0,1}

### EUF-CMA (Existential Unforgeability under Chosen Message Attack):
_kein PPT-Angreifer A wins._
1. A has pk and access to Sig(sk,*)-Orakel
2. A gives (M*,σ*)
3. A wins, when Ver(pk,M*,σ*) = 1 and M* != M.
![alt text](/resources/postImage/asymmetirscheAuthentifikation/EUF-CMA.png)

## RSA als Signaturschema
-------------------------------------------
sig(sk,M) = M^d mod N

Ver(pk,M,σ)=1 :<=> M=σ^e mod N

### Problem bei RSA:
1. _Unsinnige Nachrichten können signiert werden._
* Wähle zuerst Signatur σ ∈ ZN beliebig
* Setze dann M := σ^e mod N
* Damit ist σ gültige RSA-Signatur für M
   
2. _Homomorphie von RSA_
+ Φ: G -> H
+ Φ(g * h) = Φ(g) ★ Φ(h)

let's say pk = (N,e), two Signatures σ1 and σ2 for two Message M1 != M2, so we get the Signature of Message (M1*M2) mod N, by calculating σ1 *σ2 mod N.

### Repair: 
(RSA-)PSS: _Probabilistic Signature Scheme_

* _Vorverarbeitung(Padding) der Nachricht_:

Sig(sk,M) = (pad(M))^d mod N


## ElGamal-Signaturen
------------------------------------------

Es sei **G einen endliche zyklische Gruppe** und **g ein Erzeuger von G**:

+ **Gen**(1^k): Zieht ein x zufällig und gibt als geheimen Schlüssel sk = (G,g,x) und als öffentlichen Schlüssel: pk = (G,g,g^x) aus
+ **Sig**(sk,M): Wähle ein e zufällig und setze a :=g^e. Berechne b als Lösung von a*x + e *b = M mod ord(G). Die Signatur ist dann σ  = (a,b).
+ **Ver**(pk,M,σ=(a,b)): Gebe 1 aus, wenn (g^x)^a * a^b = g^M, sonst gebe 0 aus.

### Problem:
a = g^e wird sowohl als G-Element als auch als Exponent interpretiert

* _Randomisierung ⇒ Signaturen für unsinnige Nachrichten_
1. Wähle c zufällig
2. Setze a := (g^c)(g^x) = g^c+x und b := −a mod ord(G) 
3. Damit ist (a, b) gültige Signatur für die Nachricht

### Repair:
_Hash-Then-Sign-Paradigma_
Sei (Gen, Sig, Ver) EUF-CMA-sicher und H eine kollisionsresistente Hashfunktion.
Dann ist das durch:
+ Gen'(1^k) = Gen(1^k)
+ Sig'(sk,M) = Sig(sk, H(M))
+ Ver'(pk,M, σ) = Ver(pk, H(M), σ)

erklärte Signaturverfahren EUF-CMA-sicher.

[Yange]:    http://camscofie.github.io  "Yange"
