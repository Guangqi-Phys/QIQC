
Generally, there are three different level of noises. Code capacity noise, phenomenological noise, and circuit level noise. In the following sections, we describe each element individually and with precision. (Also see [[2024-08-21]])

 - [0] Code capacity noise
    This noise model considers only qubit errors and excludes measurement noise, assuming all measurements are perfect. Consequently, the threshold provided by this model is the highest among all error models, such as 11% for the toric code. In this model, qubit errors can be described by various channels, including depolarizing and erasure channels.
- [1] Phenomenological noise
    In this noise model, we account for both qubit errors and measurement errors. Measurement errors are incorporated in a straightforward manner by assigning a probability of error to each measurement outcome. This approach is generally sufficient for most cases. However, considering the measurement error results in a significantly lower threshold compared to the code capacity noise model. For instance, the toric code exhibits a threshold of 3.3%.
- [2] Circuit level noise
    In the circuit-level noise model, measurement errors are more accurately represented. Unlike the phenomenological noise model, which assigns a probability of error to each measurement outcome, the circuit-level model considers the specific circuits implementing the measurements. For each single-qubit gate and two-qubit gate, an error model is applied. Consequently, measurement errors arise due to gate noise. This noise model results in a lower error threshold for the toric code, approximately 1.1%.








