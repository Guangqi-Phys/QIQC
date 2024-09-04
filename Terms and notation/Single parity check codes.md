---
aliases:
  - SPC
status: true
created: Tuesday, September 3rd 2024, 11:22:48 pm
modified: Tuesday, September 3rd 2024, 11:24:52 pm
tags:
  - classical-code
  - AI-generated
---
The SPC is a linear block code with a single parity check digit(added in the end to make the codeword).

Let the information bit be given as
$$
\{b_1, b_2, b_3 \ldots, b_k\}
$$
then the check bit will be
$$
b_{k+1}=b_1+b_2+b_3+\ldots+b_k
$$
and the codeword will be
$$
\{b_1, b_2, b_3 \ldots, b_k, b_{k+1}\}
$$
At the receiver end, detector will be able to detect the error if and only if even(odd) parity is used and there are even(odd) numbers of 1's in the received signal. In all other cases, the error will go undetected.