---
layout: post
title: Block Cipher
description: CBC mode
category: blogs
---

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


[Yange]:    http://camscofie.github.io  "Yange"
