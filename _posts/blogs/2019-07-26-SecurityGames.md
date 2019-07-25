---
layout: post
title: 安全游戏
description: EUF-CMA IND-CPA
category: blogs
---
## IND-CPA (Indistinguishability under Chosen Plaintext Attack)
**Schema IND-CPA-sicher ⇔ kein eﬃzienter Angreifer A kann Chiﬀrate von selbstgewählten Klartexten unterscheiden**
1. A erhält im Folgenden Zugriﬀ auf Enc(K, ·)-Orakel
2. A wählt zwei Nachrichten M (1) , M (2) gleicher Länge 
3. A erhält C ∗ := Enc(K, M (b) ) für gleichverteiltes b ∈ {1, 2} 
4. A gewinnt, wenn er b richtig rät
![alt text](/resources/postImage/SecurityGames/Screenshot&#32;2019-07-26&#32;at&#32;00.49.53.png)

## EUF-CMA (Existential Unforgeability under Chosen Message Attack):
_kein PPT-Angreifer A wins._
1. A has pk and access to Sig(sk,*)-Orakel
2. A gives (M*,σ*)
3. A wins, when Ver(pk,M*,σ*) = 1 and M* != M.
![alt text](/resources/postImage/SecurityGames/EUF-CMA.png)


[Yange]:    http://camscofie.github.io  "Yange"
