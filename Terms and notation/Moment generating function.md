---
status: true
aliases: [MGF]
created: Wednesday, August 28th 2024, 2:48:26 pm
modified: Tuesday, September 3rd 2024, 5:55:33 pm
tags:
  - statistics
---

The moment generating function (MGF) is a statistical tool that summarizes all the moments (expected values of powers) of a random variable into a single function. For a variable $X$, the MGF can be used to compute $E(X), E(X^2), E(X^{3),}$, and so on.

The moment generating function defined as $M_X(t)=\mathbb{E}\left[e^{t X}\right]$, where $\mathbb{E}$ denotes the expectation, and $t$ is a real number. The $n$-th moment of the random variable $X$ can be derived by differentiating the MGF $n$ times with respect to $t$ and then evaluating at $t=0$.[^1] That is, $\mathbb{E}\left[X^n\right]=M_X^{(n)}(0)$, where $M_X^{(n)}$ denotes the $n$-th derivative of $M_X$.

For independent random variables $X$ and $Y$, the MGF of their sum $X+Y$ is the product of their MGFs: $M_{X+Y}(t)=M_X(t) \cdot M_Y(t)$. This property is particularly useful for studying sums of independent random variables, as it simplifies many calculations.

MGFs can often transform complex probability problems into more manageable algebraic or calculus problems, especially those involving sums of random variables or finding distributions of functions of random variables.


> [!example] Bermoulli random variable
> A Bernoulli random variable $X$ takes on only two values, 0 and 1, with probabilities $P(X=1)=p$ and $P(X=0)=1-p$, respectively.
> The MGF $M_X(t)$ of a Bernoulli random variable $X$ is defined as the expected value of $e^{t X}$, where $t$ is a real number: $M_X(t)=\mathbb{E}\left[e^{t X}\right]$.
> Since $X$ can only take on values 0 and 1 , the expression for $e^{t X}$ simplifies due to the properties of the exponential function: If $X=0$, then $e^{t X}=e^{t \cdot 0}=1$, If $X=1$, then $e^{t X}=e^{t \cdot 1}=e^t$. Therefore, the MGF $M_X(t)$ is given by:
> $$M_X(t)=\mathbb{E}\left[e^{t X}\right]=P(X=0) \cdot e^0+P(X=1) \cdot e^t=(1-p) \cdot 1+p \cdot e^t.$$
> This simplifies to:
> $$M_X(t)=1-p+p e^t$$






> [^1]: Using the Taylor series expansion of $e^{t X}$, we have: $e^{t X}=\sum_{n=0}^{\infty} \frac{(t X)^n}{n!}$. Taking the expectation of both sides, the MGF becomes: $M_X(t)=\mathbb{E}\left[\sum_{n=0}^{\infty} \frac{(t X)^n}{n!}\right]$. Due to the linearity of expectation and assuming we can interchange the order of expectation and summation (which we typically justify by conditions such as absolute convergence), this leads to $M_X(t)=\sum_{n=0}^{\infty} \frac{t^n}{n!} \mathbb{E}\left[X^n\right]$. If we differentiate $M_X(t)$ once with respect to $t$ and evaluate at $t=0$, we get: $M_X^{\prime}(t)=\sum_{n=1}^{\infty} \frac{t^{n-1}}{(n-1)!} \mathbb{E}\left[X^n\right] \cdot M_X^{\prime}(0)=\mathbb{E}\left[X^1\right]=\mathbb{E}[X]$. If we differentiate $M_X(t) n$ times, the $n$-th derivative will be: $M_X^{(n)}(t)=\sum_{k=n}^{\infty} \frac{k(k-1) \cdots(k-n+1) t^{k-n}}{k!} \mathbb{E}\left[X^k\right]$. Simplifying by cancelling the terms and setting $t=0: M_X^{(n)}(t)=\sum_{k=n}^{\infty} \frac{k!}{(k-n)!n!} t^{k-n} \mathbb{E}\left[X^k\right]$. $M_X^{(n)}(0)=\frac{n!}{n!} \mathbb{E}\left[X^n\right]=\mathbb{E}\left[X^n\right]$.



