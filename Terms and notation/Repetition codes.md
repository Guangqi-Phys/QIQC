---
aliases: 
status: true
created: Tuesday, September 3rd 2024, 3:00:09 pm
modified: Tuesday, September 3rd 2024, 3:00:18 pm
tags:
  - code
---
Repetition coding is one of the simplest forms of error correction coding used in digital communication systems. Its primary goal is to improve the reliability of data transmission over noisy channels by adding redundancy to the original message.

- [0] 1. Basic Concept:
- Repetition: In a repetition code, each bit of the original message is repeated multiple times. For instance, if the original bit is ' 0 ' or ' 1 ', it is repeated $n$ times to form a codeword. The number $n$ is typically an odd number to facilitate majority voting at the receiver.

- [1] 2. Encoding Process:
- Original Message: Suppose the original message is a sequence of bits, e.g. `101`.
- Repetition Encoding: Using a 3-repetition code, the encoded message would be `111000111`.

- [2] 3. Decoding Process:
- Majority Voting: At the receiver, the original bit is recovered by performing majority voting on the received bits. For each group of $n$ bits, the most frequent bit is chosen as the decoded bit.
- Example: If the received sequence is `111001111` (with one error in the second group), majority voting in each group gives `1` (from `111`), `0` (from `001`), and `1` (from `111`), recovering the original message ` 101 `.

- [3] 4. Error Correction Capability:
- Repetition codes are capable of correcting up to $\left\lfloor\frac{n-1}{2}\right\rfloor$ bit errors within each codeword of length $n$.

- [4] [[Log-Likelihood Ratios|LLRs]] and repetition codes

We now consider the $\mathcal{C}_{\text {rep }}(n, 1)$ repetition code, where a bit $x \in\{0,1\}$ is transmitted and the vector $\boldsymbol{y}=\left(y_1, y_2, \ldots, y_n\right)$ is received. We assume that $P(X=0)=P(X=1)=\frac{1}{2}$.

We compute the a posteriori LLR
$$L(X \mid \boldsymbol{y})=L(\boldsymbol{y} \mid X)=\ln \left(\frac{p(\boldsymbol{y} \mid X=0)}{p(\boldsymbol{y} \mid X=1)}\right)$$
which can be expressed by assuming the property that the channel is memoryless
$$L(X \mid \boldsymbol{y})=\ln \left(\frac{\prod_{i=1}^n p\left(y_i \mid X=0\right)}{\prod_{i=1}^n p\left(y_i \mid X=1\right)}\right)=\sum_{i=1}^n \ln \left(\frac{p\left(y_i \mid X=0\right)}{p\left(y_i \mid X=1\right)}\right)$$
Thus, we finally get for the $\mathcal{C}_{\text {rep }}(n, 1)$ repetition code assuming uniform priors that
$$L(X \mid \boldsymbol{y})=\sum_{i=1}^n L\left(y_i \mid X\right)$$
i.e., the a posteriori LLR is the sum of the channel-transition LLRs, which can be easily computed.
The MAP decoder for the repetition code thus takes the LLRs for each channel output and adds them. The MAP decision is $\hat{x}=0$ if $L(X \mid \boldsymbol{y}) \geq 0$ and $\hat{x}=1$ otherwise, i.e.,
$$\hat{\ddot{x}}=\operatorname{sign}(L(X \mid \boldsymbol{y}))=\operatorname{sign}\left(\sum_{i=1}^n L\left(y_i \mid X\right)\right)$$
