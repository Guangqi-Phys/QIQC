---
aliases: []
status: true
created: Tuesday, September 3rd 2024, 1:21:32 pm
modified: Tuesday, September 3rd 2024, 1:23:28 pm
tags:
  - entropy
  - statistics
---

The binary entropy function $h(p)$ is a measure of the uncertainty or entropy associated with a binary random variable. It is defined as:
$$h(p)=-p \log _2(p)-(1-p) \log _2(1-p)$$where:
- $\quad p$ is the probability of one of the two outcomes (e.g., the probability of receiving a ' 1 ' in a binary channel).
- $\log _2$ denotes the logarithm base 2 .

- [0] Interpretation:
- The function $h(p)$ quantifies the amount of information (or uncertainty) in a binary random variable that takes the value ' 1 ' with probability $p$ and ' 0 ' with probability $1-p$.
- The binary entropy function ranges from 0 to 1 bit. It is maximum (equal to 1 ) when $p=0.5$, meaning the outcome is completely unpredictable (maximum uncertainty).
- When $p=0$ or $p=1, h(p)$ is 0 , meaning there is no uncertainty because the outcome is certain.