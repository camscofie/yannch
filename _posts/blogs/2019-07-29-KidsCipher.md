---
layout: post
title: Encryption Methods for Kids
description: Cäser, Vigenère, One-Time-Pad, Stream cipher
category: blogs
---

## Cäser Cipher
**Enc(K, M) = (Mi + K mod 26)**

**Bijective Projection**
* Plain:    ABCDEFGHIJKLMNOPQRSTUVWXYZ
* Cipher:   XYZABCDEFGHIJKLMNOPQRSTUVW

Example:
+ Plaintext:  THE QUICK BROWN FOX JUMPS OVER THE LAZY DOG
+ Ciphertext: QEB NRFZH YOLTK CLU GRJMP LSBO QEB IXWV ALD


Problem:
+ no Schlüsselraum, (K ∈ {0, . . . , 25})
+ means: if M make sense, just try around then you find K
  
Hacking tips:
+ Get the most frequent letter out, guessing it's 'E' (if English). 


## Vigenère cipher
**Cäser with K1, K2, K3....Km**
Ci = Pi + Ki (mod 26)

Hacking Tips:
+ Guess the length of the Key, then it's a Cäser loop, see [Kasiski examination](https://en.wikipedia.org/wiki/Kasiski_examination).

## One-Time-Pad
**a Vigenère which the Key has the same length as the Message**

One time pad has the **informationstheoretische Sicherheitseigenschaften**, which means 
* Adversary not get any information from M, even if they have C
* can be formalisiert

Problem:
+ Key too long

Hacking tips:
+ ~~Steal their pad during transfer~~
+ none
  
## Stromchiﬀren mit Pseudozufallszahlen
![alter text](/resources/postImage/KidsCipher/Xnip2019-07-30_00-30-26.jpg)



[Yange]:    http://camscofie.github.io  "Yange"
