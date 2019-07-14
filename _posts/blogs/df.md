---
layout: post
title: Precomputed hash chains and Rainbow table
description: hash attack
category: blogs
---

## Reversing Cryptographic Hash Functions
> What to do if you have a hashed Message H(msg), and you want to have 'msg'?

Because the hash function is always one way, the way to get the message from the hashed code is to try a lot with different word, and see if you end up have same hashed code as H(msg).


## Precomputed Hash Chains
We trade time with space. What do we do is, we compute the H(*) before everything happened. But save all the discrete msg-hash pair in not effecient. Better approch is to create a reverse function R (invert of definion and value space from H function) and we do ![alt text](/resources/postImage/rainbowTable/equation.svg)

Later if we get our H(msg) as '0CAFC376' , we do R(0CAFC376) and we get 'crepa', because we have already saved the 'crepa' as later word started from 'zhihu', so we can only recalculate from 'zhihu', then we know the 'vfkkd' is the msg.


## Rainbow Table
One big problem of precomputed hash chains has two problems:
1. it's really hard to find a good R, so in reality we end up have a lot of R(*) is out of the defination space from H,
2. R has hash collision. 

What rainbow table is doing, is that we use number of R (R1...Rk), we do such ![alt text](/resources/postImage/rainbowTable/Rainbow_table1.svg)

the only way to collide two chains is by hitting same value at same iteration. So we solve the second question. 
