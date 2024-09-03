---
aliases: [LLRs]
status: 
created: Tuesday, September 3rd 2024, 11:19:13 am
modified: Tuesday, September 3rd 2024, 1:08:59 pm
tags:
  - cLDPC
---

> [!definition] (Log-Likelihood Ratio)
> Consider a binary (or equivalently bipolar) random variable $X$ ($\ddot{X}$ is the [[Binary Phase Shift Keying|BPSK]] of $X$). We define the log-likelihood ratio (LLR) $L(X)$ as
> $$L(X):=\ln \left(\frac{P(X=0)}{P(X=1)}\right)=\ln \left(\frac{P(\ddot{X}=+1)}{P(\ddot{X}=-1)}\right).$$
> Similary, we define the channel-transition LLR (where $X$ is the binary channel input and $Y$ the channel output)
> $$L(Y \mid X):=\ln \left(\frac{p(Y \mid X=0)}{p(Y \mid X=1)}\right)=\ln \left(\frac{p(Y \mid \ddot{X}=+1)}{p(Y \mid \ddot{X}=-1)}\right).$$


Log-Likelihood Ratios (LLRs) are preferred over normal ratios for binary random variables (and in general) for several important reasons:

1.  **Addition instead of multiplication:** In many algorithms, especially in decoding and estimation, working with log-likelihood ratios simplifies calculations. Multiplying probabilities (as would be necessary with normal ratios) can lead to very small numbers, increasing the risk of numerical underflow. By taking the logarithm, multiplication becomes addition, making computations more stable and efficient.
2. **Symmetry in probabilities**:The LLR transforms the probability ratio into a value that can range from $-\infty$ to $\infty$, with zero representing equal likelihoods for both binary states. This symmetric range is useful in decision-making processes, such as comparing the LLR to a threshold to determine the most likely state.
3. **Alignment with decision theory:** LLRs naturally align with Bayesian decision-making and Maximum A Posteriori (MAP) estimation. In these frameworks, decisions are often based on comparing LLRs against a threshold, which is derived from prior probabilities and costs. This makes LLRs a natural fit for these types of statistical inference problems.
4. **Handling of small probabilities:** LLRs can handle very small or very large likelihoods without leading to extreme values, which can occur when working directly with probability ratios. This is particularly important in communication systems and machine learning algorithms, where extremely unlikely events may need to be represented without causing numerical issues.

> [!note] Advantages of LLRs (more)
> - Log-Likelihood Ratios (LLRs) are commonly used due to their advantages when it comes to hardware implementation. 
> - Many bits are needed to quantize probabilities sufficiently fine to capture all the dynamics of the decoders. Due to the logarithmic representation, LLRs have less numerical instability issues.
> - Probabilities need to be normalized after each computing step to ensure that $P(X=0)+P(X=1)=1$. The normalization step is not needed with LLRs as the normalization factors cancel.
> - In case of the commonly used BSC and AWGN channels, LLRs can be easily computed!
> - Costly multiplications of probabilities become additions of LLRs.
> - Most practical implementations of nowadays coding schemes use LLRs


> [!example] Example: [[Binary Symmetric Channel|BSC]]
> Consider the BSC with error probability $\delta$. We have
> $$P(Y=0 \mid X=0)=1-\delta, P(Y=1 \mid X=1)=1-\delta.$$ 
> $$P(Y=0 \mid X=1)=\delta, P(Y=1 \mid X=0)=\delta.$$
> We can compute the log-likelihood ratio for $Y=0$:
> $$L(Y=0 \mid X)=\ln \left(\frac{P(Y=0 \mid X=0)}{P(Y=0 \mid X=1)}\right)=\ln \left(\frac{1-\delta}{\delta}\right).$$
> Similarly, we may compute for $y=1$:
> $$L(Y=1 \mid X)=\ln \left(\frac{P(Y=1 \mid X=0)}{P(Y=1 \mid X=1)}\right)=\ln \left(\frac{\delta}{1-\delta}\right)=-\ln \left(\frac{1-\delta}{\delta}\right).$$
> In general, we may thus say
> $$\begin{aligned}L(Y=y \mid X) & = \begin{cases}\ln \left(\frac{1-\delta}{\delta}\right) & \text { if } y=0 \\-\ln \left(\frac{1-\delta}{\delta}\right) & \text { if } y=1\end{cases} \\& =(-1)^y \cdot \ln \left(\frac{1-\delta}{\delta}\right)=\ddot{y} \cdot \underbrace{\ln \left(\frac{1-\delta}{\delta}\right)}_{=: L_c} \\ & =L_c \cdot(-1)^y=L_c \cdot \ddot{y}\end{aligned}$$
> where $L_c$ is the channel reliability parameter.

````functionplot
---
title: Channel reliability of BSC
xLabel: delta
yLabel: L_c
bounds: [0,1,-10,10]
disbaleZoom: 0
grid: true
---
f(x) = log((1-x)/x)
````


> [!example] Example: [[BI-AWGN]] channel
> In this channel
> $$L(Y=y \mid X)=\frac{2}{\sigma_n^2} \cdot y=L_c \cdot y$$\
> with
> $$L_c:=\frac{2}{\sigma_n^2}=4 \frac{E_{\mathrm{s}}}{N_0}$$
> In the case of the BI-AWGN channel, the LLRs $L(Y \mid X)$ are simply obtained by multiplying the received value $y$ with a constant $L_c$ that depends on the channel parameter $E_{\mathrm{s}} / N_0$ (or $\sigma_n^2$, equivalently). This makes LLRs especially attractive for practical systems, as the LLRs are readily obtained with a single multiplication (avoiding $\ln$ and $\exp$ function evaluations).

- [0] Properties of LLRs: Inverse Relation
Consider the LLR $L(X)$ associated with a binary random variable $X$. Then we have
$$L(X)=\ln \left(\frac{P(X=0)}{P(X=1)}\right)=\ln \left(\frac{P(X=0)}{1-P(X=0)}\right)$$
or equivalently
$$e^{L(X)}=\frac{P(X=0)}{1-P(X=0)}$$
Solving this expression for $P(X=0)$ leads to
$$P(X=0)=\frac{e^{L(X)}}{1+e^{L(X)}}=\frac{1}{1+e^{-L(X)}}$$
Similarly
$$P(X=1)=\frac{1}{1+e^{L(X)}}$$
- [1] Properties of LLRs: Expectation
We can calculate the expectation of $\ddot{X}$
$$
\begin{aligned}
\mathbb{E}\{\ddot{X}\} & =+1 \cdot P(\ddot{X}=+1)+(-1) \cdot P(\ddot{X}=-1)=\underbrace{P(X=0)}_{1-P(X=1)}-P(X=1) \\
& =1-2 P(X=1)
\end{aligned}
$$
We have, for the binary random variable $X$,
$$1-2 P(X=1)=1-\frac{2}{1+e^{L(X)}}=\frac{1+e^{L(X)}-2}{1+e^{L(X)}}=\frac{e^{L(X)}-1}{e^{L(X)}+1}$$
and with $\tanh (\tau):=\frac{e^{2 \tau}-1}{e^{2 \tau}+1}$, we get
$$\mathbb{E}\{\ddot{X}\}=1-2 P(X=1)=1-2 P(\ddot{X}=-1)=\tanh \left(\frac{L(X)}{2}\right).$$
- [2] A Posteriori LLRs
In many decoding problems, we want to maximize a posteriori LLRs $P(X=\hat{x} \mid Y)$

> [!definition] Definition (A Posteriori Log-Likelihood Ratios)
> We define the a posteriori LLRs of a binary channel input $X$ given the channel output $Y=y$
> $$L(X \mid Y=y)=\ln \left(\frac{P(X=0 \mid Y=y)}{P(X=1 \mid Y=y)}\right)=\ln \left(\frac{P(\ddot{X}=+1 \mid Y=y)}{P(\ddot{X}=-1 \mid Y=y)}\right)$$

If we assume that $X$ is uniformly distributed, i.e., $P(X=0)=P(X=1)=\frac{1}{2}$, then we get by applying Bayes' theorem
$$
\begin{aligned}
L(X \mid Y=y) & =\ln \left(\frac{P(X=0 \mid y)}{P(X=1 \mid y)}\right)=\ln \left(\frac{P(y \mid X=0) \cdot P(X=0)}{P(y \mid X=1) \cdot P(X=1)}\right) \\
& =\ln \left(\frac{P(y \mid X=0)}{P(y \mid X=1)}\right)+\ln \left(\frac{P(X=0)}{P(X=1)}\right) \\
& =L(Y=y \mid X)+L(X)
\end{aligned}
$$
If $P(X=0)=P(X=1)=\frac{1}{2}$, then $L(X)=0$ and the a posteriori LLR corresponds to the channel-transition LLR, i.e.,
$$L(X \mid Y=y) \stackrel{P(X=0)=\frac{1}{2}}{=} L(Y=y \mid X)$$
