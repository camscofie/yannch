---
layout: post
title: Merkle–Damgård construction
description: Hash algorithms such as MD5, SHA1 and SHA2
category: blogs
---

**[Merkle–Damgård construction](https://en.wikipedia.org/wiki/Merkle%E2%80%93Damg%C3%A5rd_construction) is a method to build collision-resistant cryptographic hash functions from collision-resistant one-way compression functions.**

![alt text](/resources/postImage/Merkle–DamgardConstruction/2880px-Merkle-Damgard_hash_big.svg.png)

## Process
+ M* = M1 + M2 + M3 + ... + Mn
+ Hi := f(Hi-1 + Mi);  1<i<n
![alt text](/resources/postImage/Merkle–DamgardConstruction/2880px-MerkleDamgard.svg.png)

## MD-compliant padding

+ M is a prefix of Pad(M)
+ length(M) = length(M') => len(Pad(M))=len(Pad(M'))
+ len(M) != len(M') => the last block of Pad(M) != last block of Pad(M')


[Yange]:    http://camscofie.github.io  "Yange"