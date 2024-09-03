---
aliases: 
status: true
created: Tuesday, September 3rd 2024, 1:14:35 pm
modified: Tuesday, September 3rd 2024, 1:16:00 pm
tags:
  - error-model
---

The Binary Input Additive White Gaussian Noise (BI-AWGN) channel models a communication system where the input is binary ( 0 or 1 ), and the transmission is affected by additive white Gaussian noise (AWGN). 

- [1] 1. Channel description
- Binary Input: The BI-AWGN channel restricts the input signal to binary values, typically represented as 0 and 1 . These values can also be mapped to -1 and +1 for mathematical convenience by [[Binary Phase Shift Keying|BPSK]].
- Additive White Gaussian Noise (AWGN): The noise added to the signal during transmission is Gaussian distributed, with a mean of 0 and a certain variance. This noise is "white," meaning it has a constant power spectral density across the frequency band.
- Output Signal: The received signal is the sum of the transmitted binary input and the Gaussian noise. If $X$ is the transmitted binary signal and $N$ is the Gaussian noise, the received signal $Y$ can be expressed as:
$$Y=X+N$$
- [2] 2. Noise characteristics
- The noise $N$ follows a normal distribution with mean 0 and variance $\sigma^2$, denoted as $N \sim$ $\mathcal{N}\left(0, \sigma^2\right)$.
- The variance $\sigma^2$ is related to the signal-to-noise ratio (SNR), which is a critical parameter in determining the performance of the communication system.
- [3] 3. Channel capacity
The capacity of the $\mathrm{BI}-\mathrm{AWGN}$ channel, which represents the maximum achievable data rate for reliable communication, is given by:
$$C=1-h_2\left(Q\left(\sqrt{\frac{2 E_b}{N_0}}\right)\right)$$
where $h_2(\cdot)$ is the [[Binary entropy function]], $Q(\cdot)$ is the [[Q-function]] representing the tail probability of the Gaussian distribution, $E_b$ is the energy per bit, and $N_0 / 2$ is the noise power spectral density.
- [4] 4. Applications
The BI-AWGN channel is widely used as a theoretical model for analyzing digital communication systems, including wireless communication, data transmission over networks, and more. It provides insights into error rates, coding strategies, and overall system performance.
- [5] 5. Error probability
The probability of bit error (BER) in a BI-AWGN channel is an important metric and is given by:
$$P_e=Q\left(\sqrt{\frac{2 E_b}{N_0}}\right)$$
where $Q(\cdot)$ represents the [[Q-function]].
