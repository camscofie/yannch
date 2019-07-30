---
layout: post
title: Asymmetrische Encryption
description: RSA, Diffie-Hellman and ElGamal
category: blogs
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

### [Extended Euclidean algorithm](https://en.wikipedia.org/wiki/Extended_Euclidean_algorithm)
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



## [Diffie–Hellman](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)
-----------------

**Process**
1. Alice and Bob choose a pair (p,g).    //p is prime, and g is [primitive root modulo p](https://en.wikipedia.org/wiki/Primitive_root_modulo_n)
2. Alice and Bob choose their secret integer, a and b.
3. Alice sends Bob her Xa = g^a mod p.
4. Bob sends Alice his Xb = g^b mod p.
5. Alice computes s = Xb^a mod p.
6. Bob computes s = Xa^b mod p.

**now they share the same secret s.**

![alter text](../../resources/postImage/DiffieHellman/800px-Diffie-Hellman_Key_Exchange.svg.png)

### Man-in-the-middle-Attack
+ Attack starts at: Alice sends Bob g^a, attacker blocks the g^a and g^b
+ attacker chooses a' and send Bob g^a', then send Alice g^b'
+ Alice think the sk is g^ab' and Bob think is g^a'b
+ Attacker knows a'; b'; g^a; g^b, then he can calculate g^ab' and g^a'b
+ Attacker blocks messages from Alice, Decrypt with g^ab' then Encrypt with g^a'b send to Bob, vice versa from Bob.
+ Protocol works all normal, *Alice and Bob never know the attacker's existence.*


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
