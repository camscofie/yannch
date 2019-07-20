---
layout: post
title: Diffie-Hellman and ElGamal Encryption
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

### Key generation
1. Generate prime q and [generator](https://en.wikipedia.org/wiki/Generating_set_of_a_group) g 
2. choose an integer x from {1,...,q-1}
3. compute h = g^x
4. public key: (G,q,g,h)
5. secret key: x

### Encryption
1. message m
2. choose an integer y from {1,...,q-1}
3. compute c0 = g^y
4. compute c1 = (h)^y * m          ## h = g^x
5. c = (c1 , c2)
6. send c to receiver

### Decryption
1. receiver has c
2. m = c0^(-x) * c1                ## (g^y)^(-x) * (g^x)^y * m


[Yange]:    http://camscofie.github.io  "Yange"
