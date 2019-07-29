---
layout: post
title: Block Cipher
description: ECB, CBC, CTR
category: blogs
---

## Electronic Codebook Mode (ECB-Modus)
1. Teile M in l Bit Blöcke M1, M2 . . . Mn ∈ {0, 1}^l auf
2. Setze C := (C1 , . . . ) mit Ci := E(K, Mi) ∈ {0, 1}^l
3. Entschlüsselung funktioniert genauso, nur mit D


## Cipher Block Chaining Mode (CBC)
![alt text](/resources/postImage/BlockCipher/CBC_encryption.svg.png)
+ M: Message; C: Ciphertext; IP: Initial Vector; E: Encryption Algorithm; K: key

**1. Encryption:**
+ M = M1 + M2 + ... + Mn
+ C0 = IV
+ C1 = E(K, M1 Xor C0)
+ C2 = E(K, M2 Xor C1)
+ C = C1 + C2 + ... + Cn

**2. Decryption:**
*go backwards*

## Counter (CTR) Mode
![alter text](/resources/postImage/BlockCipher/Xnip2019-07-30_00-40-09.jpg)



![alter text](/resources/postImage/BlockCipher/Xnip2019-07-30_00-46-51.jpg)

[Yange]:    http://camscofie.github.io  "Yange"
