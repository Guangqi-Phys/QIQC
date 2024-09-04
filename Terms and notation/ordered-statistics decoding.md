---
aliases: [OSD]
status: true
created: Tuesday, August 27th 2024, 5:31:39 pm
modified: Wednesday, September 4th 2024, 4:21:46 pm
tags:
  - AI-generated
  - algorithm
  - decoder
---

In [[Belief propagation]], a significant portion of errors are heralded failures, where the decoder exhausts its iterations and does not converge. When such a failure happens, the ordered statistics decoding (OSD) technique can post-process BP's soft decisions to identify a suitable correction consistent with the syndrome. This integration of BP and OSD (BP+OSD) has demonstrated effectiveness as a general-purpose decoder for [[Quantum LDPC codes]].

In the context of Ordered Statistics Decoding (OSD), we refer to the belief propagation (BP) soft decisions as reliabilities $\mathbf{r} \in \mathbb{R}^n$. These values represent the reliability of each bit in the hard decisions $\mathbf{c}$ output by BP. Specifically, $r_j > r_i$ indicates that bit $c_j$ is more reliable than $c_i$. We define reliabilities as $r_i := Q_{v_i}$ and utilize Log-Likelihood Ratios (LLRs) rather than probabilities, since LLRs preserve order due to their monotonicity.

The initial stage of OSD, known as order-0 reprocessing or OSD-0, involves identifying a set of $k$ bit positions that exhibit high reliability and correspond to $k$ linearly independent columns of the code's generator matrix $G$. This set is called the most reliable information set $\mathbf{T}$. Broadly, an information set refers to any set of $k$ indices that match with $k$ linearly independent columns of the generator matrix $G$.

---
- [0] The OSD algorithm
1. Soft Decoding with BP: Initially, the BP algorithm provides a soft-decision output for each bit of the received codeword. This output is a log-likelihood ratio (LLR) indicating the probability of each bit being a 0 or a 1.
2. Reliability Ordering: The bits are ordered based on the absolute values of their LLRs, with the assumption that larger magnitudes correspond to higher reliability.
3. Hard Decision and Error Pattern Generation: A hard decision is made based on the sign of the LLRs to generate an initial estimate of the codeword. Subsequently, OSD generates and tests various error patterns, starting with the least reliable positions (those with smaller LLR magnitudes).
4. Re-encoding and Syndrome Check: For each generated error pattern, the decoder modifies the initial estimate and checks if the resulting vector satisfies the parity-check equations. If the syndrome (result of the parity-check matrix multiplied by the vector) is zero, a valid codeword has been found.
5. Iterative Improvement: The process may iterate by increasing the size of the error patterns considered until a satisfactory codeword is found or a preset number of iterations is reached.

The pseudocode for OSD

```python
function OSD(BP_Output):
    n = length(BP_Output)
    Codeword = hard_decision(BP_Output)  # Make initial hard decisions
    LLR_Magnitudes = absolute(BP_Output)  # Compute reliability
    Reliability_Order = argsort(LLR_Magnitudes)  # Sort indices by reliability

    for t from 0 to max_error_patterns:
        Error_Patterns = generate_error_patterns(t, Reliability_Order)
        for pattern in Error_Patterns:
            Test_Codeword = Codeword XOR pattern  # Apply error pattern
            if check_syndrome(Test_Codeword) == 0:
                return Test_Codeword  # Return if valid codeword found

    return Codeword  # Return the best estimate if no valid codeword found

function generate_error_patterns(t, Reliability_Order):
    # Generate all t-error patterns based on least reliable positions
    return combinations(Reliability_Order[-t:], t)

function check_syndrome(Test_Codeword):
    # Compute syndrome
    Syndrome = H * Test_Codeword  # Assuming H is the global parity-check matrix
    return sum(Syndrome) % 2

function hard_decision(LLRs):
    # Convert LLRs to binary decisions
    return [1 if LLR < 0 else 0 for LLR in LLRs]
```

