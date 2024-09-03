---
aliases:
  - Linear confinement
status: true
created: Tuesday, August 27th 2024, 4:06:59 pm
modified: Tuesday, September 3rd 2024, 11:49:43 am
tags:
  - soundness
---
These definitions are from [[Quintavalle-2020-Single-shot]].

Confinement roughly stipulates qubit errors cannot grow without triggering more measurement syndromes. In simpler terms, when the error weight is less than a value $t$, an increase in error weight results in a higher syndrome weight.

> [!note] Definition (Confinement)
> Let $t$ be an integer and $f: \mathbb{Z} \rightarrow$ $\mathbb{Z}$ some increasing function with $f(0)=0$. We say that a stabiliser code has $(t, f)$-confinement if, for all errors e with $|e|^{\text {red }} \leq t$, it holds
> $$f(|\sigma(e)|) \geq|e|^{\text {red }}$$

Now we define the good confinement for an family of [[Stabilizer code]].

> [!note] Definition (Good confinement)
> Consider an infinite family of stabiliser codes. We say that the family has good confinement if each code in it has $(t, f)$-confinement where:
>     1. $t$ grows with the length $n$ of the code: $t \in \Omega\left(n^b\right)$ with $b>0$;
>     2. and $f(\cdot)$ is monotonically increasing and independent of $n$.
> We say the code family has good $X$-confinement if the above holds only for Pauli-Z errors.

Codes with good confinement have the following theorem

> [!info] Theorem
> Consider a family of $[[n, k, d]]$ quantum-LDPC codes with good confinement such that $d \geq a n^b$ with $a>0$ and $b>0$. This code family is [[Single-shot]] for the [[Adversarial noise model]]. If the code family only has good $X$-confinement then it is single-shot with respect to Pauli-Z noise.

Also, there is a relation between confinement and [[Soundness]].

> [!info] Lemma
> Consider a LDPC code that is $(t, f)$-sound with $f$ increasing. If its qubit degree is at most $\omega$, then it has $\left(\frac{t}{\omega}, f\right)$ confinement.

