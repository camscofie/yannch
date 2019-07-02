---
layout: post
title: Rainbow table
description: hash attack
category: DR
---

Rainbow table is design to get the message from a hashed code, difference to Precomputed hash chains is that, the rainbow table use more than one R (revert of H), such as R1, R2, ... , Rk, so that when there is a hash collision in two or more chains, the chains will not merge as long as the collision doesn't occur at the same position in each chain.