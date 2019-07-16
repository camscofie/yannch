---
layout: post
title: Diffie-Hellman and ElGamal
description: good stuff
category: blogs
---

## [Diffie–Hellman](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)
-----------------

**Process**
1. Alice and Bob choose a pair (p,g).    //p is prime, and g is [primitive root modulo p](https://en.wikipedia.org/wiki/Primitive_root_modulo_n)
2. Alice and Bob choose their secret integer, a and b.
3. Alice sends Bob her A = g^a mod p.
4. Bob sends Alice his B = g^b mod p.
5. Alice computes s = B^a
6. Bob computes s = A^b

**now they share the same secret s.**

![alter text](../../resources/postImage/DiffieHellman/800px-Diffie-Hellman_Key_Exchange.svg.png)

## [ElGamal encryption](https://en.wikipedia.org/wiki/ElGamal_encryption)
----------------------------------



[Yange]:    http://camscofie.github.io  "Yange"
