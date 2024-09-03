---
aliases: [MAP, Maximum A Posteriori Decoding]
status: true
created: Tuesday, September 3rd 2024, 5:27:24 pm
modified: Tuesday, September 3rd 2024, 11:26:41 pm
tags:
  - Bayesian
  - decoder
  - statistics
---

MAP Decoding (Maximum A Posteriori Decoding) is a method used in communication systems and error-correcting codes to decode received signals into the most likely transmitted message. The goal of MAP decoding is to maximize the posterior probability of the transmitted message given the received signal.

- [0] 1. A Posteriori Probability [[Probability#^353427]]:
The term "a posteriori" refers to the probability of a hypothesis (in this case, the transmitted message) being true given observed evidence (the received signal). Mathematically, the posterior probability of a transmitted codeword $\mathbf{c}$ given the received signal $\mathbf{y}$ is denoted as $P(\mathbf{c} \mid \mathbf{y})$.

- [1] 2. MAP Criterion:
The MAP decoding rule selects the codeword $\mathbf{c}$ that maximizes the posterior probability:
$\hat{\mathbf{c}}=\arg \max _{\mathbf{c} \in \mathcal{C}} P(\mathbf{c} \mid \mathbf{y})$. Here, $\mathcal{C}$ represents the set of all possible codewords, and $\hat{\mathbf{c}}$ is the decoded codeword.

- [2] 3. Bayes' Theorem:
The posterior probability $P(\mathbf{c} \mid \mathbf{y})$ can be expressed using Bayes' theorem:
$$P(\mathbf{c} \mid \mathbf{y})=\frac{P(\mathbf{y} \mid \mathbf{c}) P(\mathbf{c})}{P(\mathbf{y})}$$
Since $P(\mathbf{y})$ (the probability of the received signal) is constant for all codewords, the MAP decoding simplifies to maximizing the product of the likelihood $P(\mathbf{y} \mid \mathbf{c})$ and the prior probability $P(\mathbf{c})$ :
$$\hat{\mathbf{c}}=\arg \max _{\mathbf{c} \in \mathcal{C}} P(\mathbf{y} \mid \mathbf{c}) P(\mathbf{c})$$

- [3] 4. Special Case - ML Decoding:
If all codewords are equally likely (i.e., $P(\mathbf{c})$ is uniform), MAP decoding reduces to Maximum Likelihood (ML) decoding, where:
$$\hat{\mathbf{c}}=\arg \max _{\mathbf{c} \in \mathcal{C}} P(\mathbf{y} \mid \mathbf{c})$$

- [4] 5. Applications:
MAP decoding is used in various communication systems, including those involving [[Turbo Codes]], [[LDPC codes|LDPC]] Codes, and [[Convolutional Codes]].
It is particularly effective in scenarios where the prior probabilities of different codewords are not uniform or where specific codewords are more likely to be transmitted than others.

- [5] 6. Complexity:
MAP decoding can be computationally intensive because it involves calculating the posterior probabilities for all possible codewords, especially when the codeword space $\mathcal{C}$ is large. In practice, efficient algorithms like the [[Viterbi algorithm]] (for convolutional codes) or [[Belief propagation|sum-product]] algorithm (for LDPC codes) are often used to approximate MAP decoding.

- [6] 7. Soft-Output MAP Decoding:
In some applications, rather than outputting a single most likely codeword, MAP decoding can provide a probability distribution over possible codewords (or bits), known as **soft-output decoding**. This is useful in iterative decoding schemes like Turbo Decoding.