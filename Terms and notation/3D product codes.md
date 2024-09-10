---
aliases: 
status: true
created: Thursday, September 5th 2024, 9:44:36 am
modified: Tuesday, September 10th 2024, 4:03:25 pm
tags:
  - quantum-code
  - stabilizer-code
  - product-code
---
> [!note] See [Single-shot error correction of three-dimensional homological product codes](https://arxiv.org/abs/2009.11790) or [[Quintavalle-2020-Single-shot]]

3D product codes are [[Higher dimensional hypergraph product]] codes. By this nomenclature we refer to the CSS codes obtained by the homological product of three length-1 chain complexes (See [the original paper](https://arxiv.org/abs/1810.01519)). 

Given three classical linear codes with parity check matrices $\delta_A, \delta_B$ and $\delta_C$ we can build a 3D quantum code as follows. If $\delta_{\ell}$ is a binary matrix of size $m_{\ell} \times n_{\ell}$, it defines a linear map $\delta_{\ell}: C_{\ell}^0 \rightarrow C_{\ell}^1$, where $C_{\ell}^0$, $C_{\ell}^1$ are vector spaces over $\mathbf{F}_2$ of dimension $n_{\ell}$ and $m_{\ell}$ respectively; in other words, each linear map defines a length-1 chain complex. The 3D product of the seed matrices $\delta_A, \delta_B, \delta_C$, is the length- 3 chain complex $\mathcal{C}$ given by:


```tikz
\usepackage{tikz-cd}

\begin{document}

\begin{tikzcd}[column sep=small, row sep=large]
& C^0_A \otimes C^0_B \otimes C^0_C \arrow[d] \arrow[dl] \arrow[dr] & \\
C^1_A \otimes C^0_B \otimes C^0_C \arrow[d] \arrow[dr] & C^0_A \otimes C^1_B \otimes C^0_C \arrow[dl] \arrow[dr] & C^0_A \otimes C^0_B \otimes C^1_C \arrow[d] \arrow[dl] \\
C^1_A \otimes C^1_B \otimes C^0_C \arrow[dr] & C^1_A \otimes C^0_B \otimes C^1_C \arrow[d] & C^0_A \otimes C^1_B \otimes C^1_C \arrow[dl] \\
& C^1_A \otimes C^1_B \otimes C^1_C & 
\end{tikzcd}

\end{document}

```
In a simple form
$$\mathcal{C}_0 \xrightarrow{\delta_0} \mathcal{C}_1 \xrightarrow{\delta_1} \mathcal{C}_2 \xrightarrow{\delta_2} \mathcal{C}_3.$$
where

$$
\begin{aligned}
& \delta_0=\left(\begin{array}{l}
\delta_A \otimes \mathbf{1} \otimes \mathbf{1} \\
\mathbf{1} \otimes \delta_B \otimes \mathbf{1} \\
\mathbf{1} \otimes \mathbf{1} \otimes \delta_C
\end{array}\right), \\
& \\
& \delta_1=\left(\begin{array}{ccc}
\mathbf{1} \otimes \delta_B \otimes \mathbf{1} & \delta_A \otimes \mathbf{1} \otimes \mathbf{1} & 0 \\
\mathbf{1} \otimes \mathbf{1} \otimes \delta_C & 0 & \delta_A \otimes \mathbf{1} \otimes \mathbf{1} \\
0 & \mathbf{1} \otimes \mathbf{1} \otimes \delta_C & \mathbf{1} \otimes \delta_B \otimes \mathbf{1}
\end{array}\right), \\
& \\
& \delta_2=\left(\mathbf{1} \otimes \mathbf{1} \otimes \delta_C \quad \mathbf{1} \otimes \delta_B \otimes \mathbf{1} \quad \delta_A \otimes \mathbf{1} \otimes \mathbf{1}\right) .
\end{aligned}
$$
It is easy to verify that $\delta_{i+1} \delta_i=0$ is valid for $i=$ $1, \ldots, 3$ and therefore the chain complex $\mathcal{C}$ is well defined. As explained above, we define a CSS code on $\mathcal{C}$ by equating
$$H_Z=\delta_0^T, \quad H_X=\delta_1.$$

We refer to the matrix $M=\delta_2$ as the metacheck matrix for the $X$-stabilisers. Note that $M H_X=0$ and as a consequence we can think of the matrix $M$ as a parity check matrix on the $X$ syndromes: any valid $X$-syndrome satisfies the constraints defined by $M$.

Let $\left[n_{\ell}, k_{\ell}, \delta_{\ell}\right] /\left[n_{\ell}^T, k_{\ell}^T, d_{\ell}^T\right]$ be the parameters of the classical linear code with parity check matrix $\delta_{\ell} / \delta_{\ell}^T$.  $\mathcal{C}$ is thus associated with an $\left[\left[n, k, d_x, d_z\right]\right]$ code such that, if $k \neq 0$,
$$
\begin{aligned}
&n =n_a^T n_b n_c+n_a n_b^T n_c+n_a n_b n_c^T \\
& \\
&k =k_a^T k_b k_c+k_a k_b^T k_c+k_a k_b k_c^T \\
& \\
&d_x =\min \left\{d_b d_c, d_a d_c, d_a d_b\right\} \\
& \\
&d_z =\min \left\{d_a^T, d_b^T, d_c^T\right\}
\end{aligned}
$$

By convention, the the distance of a code with dimension 0 is $\infty$. We define the single-shot distance $d_{s s}$ of the chain complex $\mathcal{C}$ as the minimum weight of a vector in $\mathcal{C}_2$ that satisfies all the constraints given by $\delta_2$ (i.e. it belongs to the kernel of $\delta_2$ ) but is not a valid $X$-syndrome (i.e. it does not belong to the image of $\delta_1$ ). In other words, $d_{s s}$ is the minimum weight of a vector in the second homology group $\mathcal{H}_2=\operatorname{ker} \delta_2 / \operatorname{Im} \delta_1$ of the chain complex $\mathcal{C}$. It is easy to verify that $d_{s s}=\min \left\{d_a, d_b, d_c\right\}$ if $\mathcal{H}_2 \neq 0$ and $\infty$ otherwise (See [the original paper](https://arxiv.org/abs/1810.01519)).

