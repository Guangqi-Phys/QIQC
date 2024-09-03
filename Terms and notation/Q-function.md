---
aliases: 
status: true
created: Tuesday, September 3rd 2024, 1:21:36 pm
modified: Tuesday, September 3rd 2024, 1:23:51 pm
tags:
  - statistics
  - gaussian
---

The Q-function is a function that represents the tail probability of the standard normal distribution (Gaussian distribution). It is defined as:
$$Q(x)=\frac{1}{\sqrt{2 \pi}} \int_x^{\infty} \exp \left(-\frac{t^2}{2}\right) d t$$
where:
- $x$ is the argument of the Q -function.
- $\exp \left(-t^2 / 2\right)$ is the Gaussian function.

- [0] Interpretation:
- The Q-function $Q(x)$ gives the probability that a standard normal random variable (with mean 0 and variance 1 ) exceeds the value $x$.
- In other words, it represents the area under the tail of the Gaussian distribution curve to the right of $x$.
- The Q-function is commonly used in communication theory to calculate the probability of bit error (BER) in systems affected by Gaussian noise. The BER for various modulation schemes can be directly related to the Q-function.

- [1] Example:
If $x=1, Q(1)$ represents the probability that a standard normal random variable is greater than 1 . This is useful for calculating error rates in digital communication systems.