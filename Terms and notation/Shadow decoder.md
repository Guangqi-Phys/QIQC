---
aliases: []
status: true
created: Tuesday, August 27th 2024, 5:24:40 pm
modified: Tuesday, September 3rd 2024, 5:58:42 pm
tags:
  - decoder
---

See [[Quintavalle-2020-Single-shot]].

> [!info] Definition (Shadow decoder) 
> The Shadow decoder has variable parameter $t>0$. Given an observed syndrome $\bar{s}=\sigma(e)+\bar{s}_e$ where $\bar{s}_e \in \mathbb{F}_2^m$ is the syndrome error, the Shadow decoder of parameter $t$ performs the following 2 steps: 
> 1. Syndrome repair: find a binary vector $\bar{s}_r$ of minimum weight $\left|\bar{s}_r\right|$ such that $\bar{s}+\bar{s}_r$ belongs to the $t$-Shadow of the code, where $t \text {-Shadow }=\{\sigma(e):|e| \leq t\}$ 
> 2. Qubit decode: find $e_r$ of minimum weight $\left|e_r\right|$ such that $\sigma\left(e_r\right)=\bar{s}+\bar{s}_r$. We call $r=e_r \cdot$ e the residual error. 
> The $t$-Shadow means to repair the syndrome such that make sure that the error corresponding to the syndrome after the repairation has weight less than $t$.


The Shadow decoder, a theoretical two-stage decoder, is [[Single-shot]] on codes with good [[Confinement]] against adversarial noise. The basic idea is that when a code has conﬁnement, the weight of the residual error after one decoding cycle is bounded by a function of the weight of the syndrome error. (Just like the [[Small-set flip decoder]] for quantum expander code).

