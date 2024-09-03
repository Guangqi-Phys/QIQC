---
aliases: 
status: 
created: Tuesday, September 3rd 2024, 3:00:09 pm
modified: Tuesday, September 3rd 2024, 3:00:18 pm
tags:
  - code
---
Repetition coding is one of the simplest forms of error correction coding used in digital communication systems. Its primary goal is to improve the reliability of data transmission over noisy channels by adding redundancy to the original message.

- [0] 1. Basic Concept:
- Repetition: In a repetition code, each bit of the original message is repeated multiple times. For instance, if the original bit is ' 0 ' or ' 1 ', it is repeated $n$ times to form a codeword. The number $n$ is typically an odd number to facilitate majority voting at the receiver.

- [1] 2. Encoding Process:
- Original Message: Suppose the original message is a sequence of bits, e.g. `101`.
- Repetition Encoding: Using a 3-repetition code, the encoded message would be `111000111`.

- [2] 3. Decoding Process:
- Majority Voting: At the receiver, the original bit is recovered by performing majority voting on the received bits. For each group of $n$ bits, the most frequent bit is chosen as the decoded bit.
- Example: If the received sequence is `111001111` (with one error in the second group), majority voting in each group gives `1` (from `111`), `0` (from `001`), and `1` (from `111`), recovering the original message ` 101 `.

- [3] 4. Error Correction Capability:
- Repetition codes are capable of correcting up to $\left\lfloor\frac{n-1}{2}\right\rfloor$ bit errors within each codeword of length $n$.