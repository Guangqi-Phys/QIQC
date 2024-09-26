---
aliases: []
status: 
created: Thursday, September 26th 2024, 4:58:40 pm
modified: Thursday, September 26th 2024, 5:03:05 pm
tags:
  - degenerate
---
> [!note] Credit to Adam Zalcman [stackexchange](https://quantumcomputing.stackexchange.com/questions/27279/is-there-a-simple-way-to-tell-if-a-stabilizer-code-is-degenerate).

It is somewhat imprecise to say that a quantum error correcting code is degenerate. Degeneracy means that the code assigns the same syndrome to two different errors, but that is of course true of every code ${ }^1$. Therefore, one should specify the set of errors to be considered. Then the code $C$ is degenerate for the set of errors $\mathcal{E}$ if two distinct errors $e_1, e_2 \in \mathcal{E}$ have the same syndrome. Often, $\mathcal{E}$ is implicitly taken to be the set of correctable errors of the code.

(Interestingly, it is impossible for a classical error correcting code to be degenerate for any set of correctable errors.)

#### 1. Single-qubit errors
It is particularly easy to check if a stabilizer code is degenerate for the set of single-qubit $X$ and $Z$ errors. All we need to do is write down the check matrix $H=\left[H_Z \mid H_X\right]$ and see whether it has two identical columns. We can extend this to all single-qubit errors by expanding the check matrix to $H^{\prime}=\left[H_Z\left|H_X\right| H_Y\right]$ where ${ }^2 H_Y=H_Z+H_X$ and verifying that all columns of $\boldsymbol{H}^{\prime}$ are distinct.

For example, the check matrix for the $[[5,1,3]]$ code is
$$
\left[\begin{array}{lllll|lllll}
0 & 1 & 1 & 0 & 0 & 1 & 0 & 0 & 1 & 0 \\
0 & 0 & 1 & 1 & 0 & 0 & 1 & 0 & 0 & 1 \\
0 & 0 & 0 & 1 & 1 & 1 & 0 & 1 & 0 & 0 \\
1 & 0 & 0 & 0 & 1 & 0 & 1 & 0 & 1 & 0
\end{array}\right]
$$
where all columns are distinct. Moreover, $H_Y=H_Z+H_X$ consists of distinct columns with Hamming weight three and four, so $\boldsymbol{H}^{\prime}$ has distinct columns, too. Therefore, this code is not degenerate for single-qubit errors.

On the other hand, the check matrix for the $[[9,1,3]]$ code is

$$
\left[\begin{array}{lllllllll|lllllllll}
1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 1 & 1 & 1 & 1 & 0 & 0 & 0 \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 1 & 1 & 1 & 1 & 1
\end{array}\right]
$$

where some columns, e.g. tenth and eleventh, are identical. Therefore, the $[[9,1,3]]$ code is degenerate.

The reason this procedure works is that the syndrome $S$ of an error given as a binary vector $e=\left[z_1, \ldots, z_n, x_1, \ldots, x_n\right]$ can be computed as
$$
S=H \Lambda e
$$
where $\boldsymbol{H}$ is the check matrix and $\Lambda=\left[\begin{array}{ll}0 & I \\ I & 0\end{array}\right]$ is a matrix that realizes the standard symplectic inner product in $\mathbb{Z}_2^{2 n}$.

#### 2. General procedure
The above procedure directly generalizes to more complicated sets of errors, but instead of comparing columns of the check matrix, we now need to compare their linear combinations.

The most general way to state the above procedures is the following simple algorithm

```
def is_degenerate(code, errors):
    syndromes = set()
    for e in errors:
        s = code.get_syndrome(e)
        if s in syndromes:
            return True
        syndromes.add(s)
    return False
```

