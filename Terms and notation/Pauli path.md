---
aliases:
  - path
status: true
created: Thursday, August 15th 2024, 1:48:59 pm
modified: Tuesday, September 3rd 2024, 11:46:40 am
tags:
---
A sequence $\{P_0, P_1, \ldots, P_t\}$ from the Pauli group $\mathcal{P}$ forms a path from $P_0$ to $P_t$ if for each index $i$, the operators $P_i$ and $P_{i+1}$ differ at no more than one qubit. 

The notation $w\left(P_0, P_t\right)$ represents the collection of all such paths from $P_0$ to $P_t$. For $r \in w\left(P_0, P_t\right), \epsilon_{\max }(r)$ denotes the highest energy along the path $r$, i.e., $\epsilon_{\max }(r)=\max _{P_i \in r} \epsilon\left(P_i\right)$, as the energy barrier of $E$ along the path $r$.