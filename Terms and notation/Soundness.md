---
aliases: []
status: true
created: Monday, August 12th 2024, 11:15:41 pm
modified: Thursday, September 19th 2024, 9:26:10 pm
tags: []
---
See [A theory of single-shot error correction for adversarial noise](https://arxiv.org/abs/1805.09271).

Roughly, this property is that for low weight syndromes there exists a low weight physical error producing the syndrome. More formally,

> [!definition] (Soundness) 
> Let $t$ be an integer and $f: \mathbb{Z} \rightarrow \mathbb{R}$ be some function called the soundness function with $f(0)=0$. Given some set of Pauli checks $\mathcal{M}$, we say it is $(t, f)$-sound if for all Pauli errors $E$ with $|\sigma(E)|=x<t$, it follows that there exists an $E^{\star}$ with $\sigma\left(E^{\star}\right)=\sigma(E)$ such that $\mathrm{wt}^{\star}\left(E^{\star}\right) \leqslant f(x)$.

The phrase soundness comes from the literature on [[Locally testable codes]]. More rigorously, we define the following notion of goodness

> [!definition] (Good soundness)
> Consider an infinite check family $\mathcal{M}_n$. We say the family has good soundness if each $\mathcal{M}_n$ is $(t, f)$-sound where:
>     1. $t$ grows with $n$ such that $t \geqslant a n^b$ for some positive constants $a, b$. That is, $t \in \Omega\left(n^b\right)$ with $b>0$;
>     2. $f(x)$ is some polynomial that is monotonically increasing with $x$ and independent of $n$.

The intuition behind $f$ being a polynomial is that we are formalising an algebraic version of an area or volume law that is encountered in topological codes. For instance, in the classical 2D Ising model we know that the area within a boundary follows a quadratic scaling.