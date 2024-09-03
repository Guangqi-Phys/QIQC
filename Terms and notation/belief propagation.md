---
status: false
aliases:
  - BP
  - sum-product
created: Tuesday, August 27th 2024, 4:28:30 pm
modified: Tuesday, September 3rd 2024, 11:38:19 am
tags:
  - algorithm
  - statistics
---


The belief propagation (BP) algorithm (also known as sum-product algorithm) has been shown to be eﬀective at decoding classical LDPC codes. It has a running time that is linear in the block length of the code.

️️BP is a message passing algorithm, in which messages are passed along the edges of a Tanner graph.


---
- [0] 1. Gallagers' lemma

> [!theorem] Lemma (Gallager)
> Consider a sequence of $m$ independent random variables $\mathbf{A}=\left[A_1, A_2, \ldots, A_m\right]$, where $P\left(A_k=1\right)=p_k$. Then
> $$P(\mathbf{A} \text { has even parity })=\frac{1}{2}+\frac{1}{2} \prod_{k=1}^m\left(1-2 p_k\right)$$
> and
> $$P(\mathbf{A} \text { has odd parity })=\frac{1}{2}-\frac{1}{2} \prod_{k=1}^m\left(1-2 p_k\right)$$



The [[Moment generating function]](MGF) of a random variable (Bernoulli variable) $A_k$  which is 1 with probability $p_k$ and 0 with probability $1-p_k$ is: 
$$M_{A_k}(t)=E\left(e^{t A_k}\right)=p_k e^t+\left(1-p_k\right).$$
Since the $A_k$ are independent, the MGF of $S = A_1 + \ldots + A_m$ is given by the product of the MGFs of the $A_k$: 
$$M_S(t)=\prod_{k=1}^m\left(p_k e^t+\left(1-p_k\right)\right).$$
The probability that $S$ is even can be calculated by evaluating the MGF of $S$ at $t = i\pi$ (since $e^{i \pi n}$ equals $(-1)^n$)[^1]: 
$$P(\mathbf{A} \text { has even parity })=E\left(\frac{1+(-1)^S}{2}\right)=\frac{1}{2}\left(1+E\left(e^{i \pi S}\right)\right)$$
Substitute $t = i \pi$ into the MGF of $S$:
$$M_S(i \pi)=\prod_{k=1}^m\left(p_k e^{i \pi}+\left(1-p_k\right)\right)=\prod_{k=1}^m\left(p_k(-1)+\left(1-p_k\right)\right)=\prod_{k=1}^m\left(1-2 p_k\right)$$
Thus, the expression for $P(S \text{ is even})$ is:
$$P(S\text{ is even})=\frac{1}{2}\left(1+M_S(i \pi)\right)=\frac{1}{2}\left(1+\prod_{k=1}^m\left(1-2 p_k\right)\right).$$
---
- [1] 2. [[Log-Likelihood Ratios|LLRs]] and single parity check codes

We now consider the $\mathcal{C}_{\text {SPC }}(n, n-1)$ single-parity-check code and transmission of length-$n$ codewords $x$ over a memoryless channel whose output is $y$.

Remember that the bits $x_i$ in each codeword $\boldsymbol{x}^{[m]}$ have a single constraint: There must be an even number of " 1 "s on $x^{[m]}$.

Without loss of generality, we formulate the [[MAP decoding]] rule for bit $x_1$
$$\hat{x}_1=\arg \max _{b \in\{0,1\}} P\left(x_1=b \mid \boldsymbol{y} \text {, even number of " } 1 \text { "s in } \boldsymbol{x}\right)$$
and we have
$$
\begin{aligned}
P\left(x_1=0 \mid \boldsymbol{y}, \text { even no. of " } 1 \text { "s in } \boldsymbol{x}\right) & =P\left(x_2, \ldots, x_n \text { has even no. " } 1 \text { "s } \mid \boldsymbol{y}\right) \\
& =\frac{1}{2}\left(1+\prod_{\ell=2}^n\left(1-2 P\left(x_{\ell}=1 \mid y_{\ell}\right)\right)\right)
\end{aligned}
$$















> [^1]: When $t = i\pi$, the probability that $S$ is even, $P( \text{even } S)$, can be formulated by considering: $\mathbb{E}\left[(-1)^S\right]=P($ even $S)-P($ odd $S)$. Since the total probability $P($ even $S)+P($ odd $S)=1$, you can solve for $P($ even $S)$ as follows: $P($ even $S)=$ $\frac{1+\mathbb{E}\left[(-1)^S\right]}{2}$. When you evaluate the MGF $M_S(t)$ at $t=i \pi$ : $M_S(i \pi)=\mathbb{E}\left[(-1)^S\right]$ This gives: $P($ even $S)=\frac{1+M_S(i \pi)}{2}$. This expression neatly splits the probabilities of $S$ being even or odd based on the summation of probabilities weighted by $(-1)^S$.