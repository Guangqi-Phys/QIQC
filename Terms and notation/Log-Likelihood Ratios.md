---
aliases:
  - LLRs
status: 
created: Tuesday, September 3rd 2024, 11:19:13 am
modified: Tuesday, September 3rd 2024, 11:19:26 am
tags:
  - cLDPC
---

> [!definition] (Log-Likelihood Ratio)
> Consider a binary (or equivalently bipolar) random variable $X$. We define the log-likelihood ratio (LLR) $L(X)$ as
> $$L(X):=\ln \left(\frac{P(X=0)}{P(X=1)}\right)=\ln \left(\frac{P(\ddot{X}=+1)}{P(\ddot{X}=-1)}\right)$$




Definition (Log-Likelihood Ratio)
Consider a binary (or equivalently bipolar) random variable $X$. We define the log-likelihood ratio (LLR) $L(X)$ as

$$
L(X):=\ln \left(\frac{P(X=0)}{P(X=1)}\right)=\ln \left(\frac{P(\ddot{X}=+1)}{P(\ddot{X}=-1)}\right)
$$


Similary, we define the channel-transition LLR (where $X$ is the binary channel input and $Y$ the channel output)

$$
L(Y \mid X):=\ln \left(\frac{p(Y \mid X=0)}{p(Y \mid X=1)}\right)=\ln \left(\frac{p(Y \mid \ddot{X}=+1)}{p(Y \mid \ddot{X}=-1)}\right)
$$
