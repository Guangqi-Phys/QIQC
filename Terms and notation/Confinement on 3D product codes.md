---
aliases: []
status: false
created: Thursday, September 5th 2024, 9:41:17 am
modified: Thursday, September 5th 2024, 9:49:45 pm
tags:
  - comments
  - confinement
  - higher-dimensional
  - hypergraph-product
  - single-shot
---

In the paper [[Quintavalle-2020-Single-shot]], the authors demonstrate the [[Confinement ]]condition of [[3D product codes]] in Theorem 3 as follows:

> [!theorem] Theorem 3. 
> All $3 D$ product codes have $(t, f) X$-confinement where $t$ is equal to the $Z$-distance of the code and $f(x)=$ $x^3 / 2$ or better.

In this notes, we follow the paper to give a detailed proof for this theorem.

---

<mark style="background: #D2B3FFA6;">Before give the proof, I would like to make some comments</mark> . At first, I thought this theorem solved my problem about the energy barrier of [[Higher dimensional hypergraph product]] code, as they said, the 3D product code have X-[[confinement]], which is sufficient to give a energy barrier. After reading the first part of the proof, I found they didn't solve the problem I'm pursuing, here is why:
 - First, the only give a confinement with $f(x)=$ $x^3 / 2$. So, the [[energy barrier]] (the syndrome weight) should be the cubic root of the distance at most, but we want to prove that for $d = d_Ad_B$, the energy barrier is proportional to $d_A$ (more specificly, the energy barrier is equal to $d_AE_b$, where $E_b$ is the energy barrier of $L_B$ (with distance $d_b$)).
 - Second, it seems that $t = {d_A, d_B, d_C}$, which is far more less than $d=d_Ad_B$, but they claim that $t$ could be the size of $Z$ logical error, which is the thing I didn't understand.
Anyway, the good news is, there are still something we can do! #comments

---

