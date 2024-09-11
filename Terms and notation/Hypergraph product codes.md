---
aliases:
  - HP
status: true
created: Tuesday, September 3rd 2024, 6:37:11 pm
modified: Wednesday, September 11th 2024, 1:45:25 pm
tags:
  - quantum-code
  - stabilizer-code
  - css-code
---
Quantum error-correcting codes (QECCs) are essential in quantum computing to protect quantum information from noise and errors. A quantum hypergraph product code is a type of [[stabilizer code]]. This type of code generalizes the classical hypergraph product to the quantum setting, providing a framework to construct quantum [[LDPC codes|LDPC]] (Low-Density Parity-Check) codes.

The quantum hypergraph product code is constructed by taking the product of two classical codes, typically defined by their parity-check matrices. Given two classical codes $C_1$ and $C_2$, with parity-check matrices $H_1$ and $H_2$, the quantum hypergraph product defines a quantum code whose parity-check matrices involve the Kronecker product of these matrices, resulting in a quantum code with two sets of stabilizer generators: one related to the rows and one to the columns of the original matrices. This construction maintains properties from the classical codes and translates them into the quantum domain.

More formally, hypergraph product codes are [[CSS code]]s formed from two classical [[Linear code]]s. Let $H_1$ and $H_2$ be $r_1 \times n_1$ and $r_2 \times n_2$ parity check matrices, respectively. The parity-check matrix of the hypergraph product code becomes:
$$
\begin{aligned}
H_X & =\left(H_1 \otimes \mathbf{I}_{n_2} \mathbf{I}_{r_1} \otimes H_2^T\right) \\
H_Z & =\left(\mathbf{I}_{n_1} \otimes H_2 H_1^T \otimes \mathbf{I}_{r_2}\right)
\end{aligned}
$$

Because $H_X H_Z^T=0$, these two parity check matrices define a CSS code, with a quantum parity check matrix
$$
H_{\left(H_1, H_2\right)}=\left(\begin{array}{cc}
H_X & 0 \\
0 & H_Z
\end{array}\right) .
$$

The classical codes defined by $H_1, H_2, H_1^T$, and $H_2^T$ form the parent classical codes. Assuming that $H_i$ and $H_i^T$ define codes with parameters $\left[n_i, k_i, d_i\right]$ and $\left[r_i, k_i^T, d_i^T\right]$, for $i=1,2$. Under this assumption, the quantum code is a $\left[\left[n_1 n_2+r_1 r_2, k_1 k_2+k_1^T k_2^T, \min \left(d_1, d_2, d_1^T, d_2^T\right)\right]\right]$ code. With [[Energy barrier]] $\Delta\left(H_{\left(H_1, H_2\right)}\right)=\min \left(\Delta\left(H_1\right), \Delta\left(H_2\right), \Delta\left(H_1^T\right), \Delta\left(H_2^T\right)\right)$.




