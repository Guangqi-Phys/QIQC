---
aliases: ["Bayes' theorem"]
status: true
created: Wednesday, August 28th 2024, 11:45:51 pm
modified: Thursday, August 29th 2024, 10:07:03 am
tags:
  - Bayesian
  - statistics
---

1. The **prior probability** is the probability of an event before new data is collected. It reflects the initial belief about the event, based on existing knowledge or assumptions before any actual testing or observation is done.
2. The **posterior probability** is the revised probability of an event occurring after taking into account new evidence. It is derived from the prior probability and the likelihood of the new evidence given the prior. In Bayesian statistics, this updating of beliefs is formalized through Bayes' theorem. ^353427

> [!theorem] Bayes' Theorem
> Bayes' theorem is typically stated as: $P(A\mid B)=\frac{P(B\mid A) \times P(A)}{P(B)}$ where:
> - $P(A\mid B)$ is the posterior probability of hypothesis $A$ given the evidence $B$.
> - $P(B\mid A)$ is the likelihood, which is the probability of observing the evidence $B$ given that hypothesis $A$ is true.
> - $P(A)$ is the prior probability of hypothesis $A$.
> - $P(B)$ is the total probability of observing the evidence $B$ under all possible hypotheses.


