---
aliases:
  - LDPC
status: true
created: Tuesday, September 3rd 2024, 3:59:02 pm
modified: Tuesday, September 3rd 2024, 7:31:28 pm
tags:
  - graph
  - classical-code
---
Low-Density Parity-Check (LDPC) codes are a type of error-correcting code used in communication systems to detect and correct errors in transmitted data. LDPC codes are widely recognized for their ability to approach the theoretical limits of channel capacity, as defined by Claude Shannon's information theory.

- [0] 1. Sparse Parity-Check Matrix: 
LDPC codes are defined by a sparse parity-check matrix (H matrix), where the majority of the elements are zeros, and only a small percentage are ones. This sparsity is crucial as it allows for efficient decoding algorithms.

- [1] 2. Bipartite Graph Representation: 
LDPC codes can be visualized using a bipartite graph, where one set of nodes represents the bits of the codeword (variable nodes), and the other set represents the parity-check constraints (check nodes). The edges in the graph correspond to the non-zero entries in the parity-check matrix.

- [2] 3. Efficient Decoding: 
One of the most significant advantages of LDPC codes is their efficient decoding via iterative algorithms, such as the Belief Propagation (BP) or Sum-Product Algorithm (SPA). These algorithms iteratively update the beliefs (probabilities) of each bit being a 0 or 1 until convergence, effectively correcting errors in the received data.

- [3] 4. Near-Shannon Limit Performance: 
LDPC codes are known for their performance close to the Shannon limit, meaning they can achieve error rates close to the theoretical minimum for a given signal-to-noise ratio. This makes them highly effective in scenarios requiring reliable communication, such as deep-space communication, satellite broadcasting, and modern wireless standards like $5 G$.

- [4] 5. Flexibility: 
LDPC codes are flexible and can be designed with various code rates and lengths, making them suitable for a wide range of applications, from short block lengths in storage devices to very long block lengths in data transmission.

- [5] 6. Applications of LDPC Codes:
- **Wireless Communication**: LDPC codes are used in standards such as 5G, Wi-Fi (802.11n and beyond), and DVB-S2 for satellite communication.
- **Data Storage**: LDPC codes are employed in hard drives, SSDs, and other storage technologies to enhance data integrity.
- **Digital Television and Satellite**: The high efficiency of LDPC codes makes them ideal for broadcasting high-definition television signals and satellite communication systems.

- [6] 7. [[Log-Likelihood Ratios|LLRs]] and LDPC codes ^8cb15c
The variable nodes of degree $d_{\mathrm{v}}$ of an LDPC code can be considered as $\left(d_{\mathrm{v}}+1,1\right)$ repetition codes where 1 bit is tranmitted over the channel and the other bits are "transmitted over the graph". As in "soldier counting" we send a message once we have received $d_{\mathrm{v}}-1$ messages
Variable Nodes, Example $d_{\mathrm{v}}=4$ :

```mehrmaid
graph TB
    A["$L(y_i \mid X_i)$"] --> B(( ))
    C["$L(\chi_1)$"] --> B
    D["$L(\chi_2)$"] --> B
    E["$L(\chi_3)$"] --> B
    B --> F["$L(\xi_4)$"]
    style B fill:#ccc,stroke:#333,stroke-width:2px
    style F stroke:#00f,stroke-width:2px,color:#00f

```

Similarly, we get for the other edges
$$
\begin{aligned}
& L\left(\xi_1\right)=L\left(y_i \mid X_i\right)+L\left(\chi_2\right)+L\left(\chi_3\right)+L\left(\chi_4\right) \\
& L\left(\xi_2\right)=L\left(y_i \mid X_i\right)+L\left(\chi_1\right)+L\left(\chi_3\right)+L\left(\chi_4\right) \\
& L\left(\xi_3\right)=L\left(y_i \mid X_i\right)+L\left(\chi_1\right)+L\left(\chi_2\right)+L\left(\chi_4\right)
\end{aligned}
$$
i.e., we exclude the edge under consideration from the computation (extrinsic message).

The best decision for the bit $\hat{x}_i$ is obtained from the a posteriori LLR (see [[Repetition codes#^b4d844]])
$$L\left(X_i \mid \boldsymbol{y}\right)=L\left(y_i \mid X_i\right)+\sum_{i=1}^4 L\left(\chi_i\right)$$



