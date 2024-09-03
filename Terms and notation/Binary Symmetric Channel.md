---
aliases: [BSC]
status: true
created: Tuesday, September 3rd 2024, 11:53:02 am
modified: Tuesday, September 3rd 2024, 12:02:27 pm
tags: []
---
The Binary Symmetric Channel (BSC) is one of the simplest models in information theory and digital communication, it is a channel that transmits binary symbols, where each bit transmitted can either be received correctly or flipped to the opposite value due to noise. The channel is characterized by a fixed probability of error, denoted by , which is the probability that a transmitted bit is received incorrectly. Mathematically, if $X$ is the input bit and $Y$ is the output bit, then:
$$P(Y=X)=1-p, \quad P(Y \neq X)=p$$
A common way to visualize the BSC is with a simple diagram:

```mermaid
graph TD 
A(Input Bit 0) -->|1-p| B(Output Bit 0) 
A -->|p| C(Output Bit 1) 
D(Input Bit 1) -->|1-p| C(Output Bit 1) 
D -->|p| B(Output Bit 0)

```

The [[Channel Capacity]] $C$ of the Binary Symmetric Channel, which represents the maximum rate at which information can be reliably transmitted over the channel, is given by:
$$
C=1-H(p)
$$
where $H(p)$ is the binary entropy function defined as:
$$
H(p)=-p \log _2(p)-(1-p) \log _2(1-p)
$$
The channel capacity tells us how much information can be sent through the BSC with an arbitrarily low probability of error, given optimal encoding and decoding schemes.

