---
aliases: 
status: true
created: Wednesday, September 11th 2024, 9:11:30 pm
modified: Wednesday, September 11th 2024, 9:23:43 pm
tags:
  - definitions
---
- [0] Definition 1
A Hamiltonian is said to have topological order if it has a degenerate ground state and different ground states are locally indistinguishable. [^1]

- [1] Definition 2
Note that what is usually called a topological order translates to coding language as simply the condition for a quantum code to have a macroscopic distance. [^2]

- [2] Definition 3
The notion of topological order was originally introduced in order to characterize the stability of ground states of many-body quantum systems against local perturbations [^3]. Loosely speaking, a system is said to have topological order when its ground state properties do not change significantly under any types of small, but finite local perturbations. This stability of ground states against local perturbations is also valuable for quantum information processing since topologically ordered spin systems can be used as good quantum codes with macroscopic code distances. [^4]

- [3] Definition 4
A stabilizer code has topological order at scale $L_{t q o}$ if any Pauli operator supported on a cube of linear size $L_{t q o}$ satisfies the following conditions:
-  If $P$ commutes with all stabilizers then $P$ is stabilizer itself;
-  If $S(P) \neq \emptyset$ then there is a stabilizer $G \in \mathcal{G}$ such that $P G$ is supported on the 1-neighborhood of the minimum enclosing box $b(S(P))$.
A family of stabilizer codes $\{\mathcal{C}(L)\}_L$ is called topological if there exists a constant $\gamma>0$ such that each code $\mathcal{C}(L)$ has topological order at scale $L_{t q o} \geq L^\gamma$. [^5]


- [4] Definition 5
In stabilizer codes the main step for error correction is the measurement of certain operators, which may be local or not. A class of codes where these measurements are intrinsically local is that of topological stabilizer codes. [^6]


- [5] Definition 6
Physically, this is achieved by realizing the code space in a topologically ordered quantum system. In such a system we have a gap to system excitations and topological degeneracy, which cannot be lifted by any local perturbations to the Hamiltonian. Only topologically non-trivial errors are capable of mapping degenerate ground states one onto another.[^7]

- [6] Definition 7
In general a code is topological if its stabilizer has local generators and non-detectable errors are topologically non-trivial (in the particular space where the qubits are to be placed). Given such a code, one can always construct a local Hamiltonian such that the resulting system is topologically ordered and the error correcting code corresponds to the ground state. [^8]

- [7] Definition 8
We succeed in proving gap stability under generic local perturbations. Our results are valid not just for the toric code, but more generally for any Hamiltonian which can be written as a sum of geometrically local commuting projectors on a $D$-dimensional lattice with certain topological order conditions that we define later. This includes models such as Kitaev's quantum double model and the Levin-Wen string-net model. Furthermore, we prove stability of the spectral gaps separating sufficiently low-lying eigenvalues of the unperturbed Hamiltonian. [^9]

This paper addresses the concept that quantum codes with local stabilizers are equivalent to systems that are stable under local perturbations. This study focuses on the zero-temperature stability of topological phases of matter under weak time-independent perturbations, applying to quantum spin Hamiltonians that can be expressed as a sum of geometrically local commuting projectors on a lattice. The paper establishes that given such a Hamiltonian, there exists a threshold such that for any perturbation represented as a sum of short-range bounded-norm interactions, the perturbed Hamiltonian has well-defined spectral bands separated by a constant gap. This finding is based on conditions TQO-1 and TQO-2, with TQO-1 defining the ground subspace as a quantum code with macroscopic distance and TQO-2 requiring consistency between local ground subspaces and the global one.

- [8] Definition 9
There is no completely rigorous definition of topological order in the literature. At an intuitive level it means that there does not exist a local order parameter or observable which distinguishes different degenerate ground states. Such a property is immediately obtained when the ground space is the code space of a quantum error-correcting code with macroscopic (meaning scaling as some function of the system size) distance as follows. [^10]


[^1]: Sergey Bravyi and Jeongwan Haah. On the energy landscape of 3D spin Hamiltonians with topological order. arXiv, 2011.
[^2]: Sergey Bravyi and Barbara Terhal. A no-go theorem for a two-dimensional self-correcting quantum memory based on stabilizer codes. New Journal of Physics, 11(4):043029, 2009.
[^3]: Xiao-Gang Wen and Qian Niu. Ground-state degeneracy of the fractional quantum hall states in the pres- ence of a random potential and on high-genus riemann surfaces. Physical Review B, 41(13):9377, 1990.
[^4]: Beni Yoshida. Feasibility of self-correcting quantum memory and thermal stability of topological order. arXiv, 2011.
[^5]: Sergey Bravyi and Jeongwan Haah. Analytic and Numerical Demonstration of Quantum Self-Correction in the 3D Cubic Code. Physical Review Letters, 111(20):200501, 11 2013.
[^6]: H. Bombin. Topological subsystem codes. Physical Review A, 81(3), March 2010.
[^7]: H. Bombin and M. A. Martin-Delgado. Topological quantum distillation. Physical Review Letters, 97(18), October 2006.
[^8]: H. Bombin and M. A. Martin-Delgado. Topological computation without braiding. Physical Review Letters, 98(16), April 2007.
[^9]: Sergey Bravyi, Matthew B Hastings, and Spyridon Michalakis. Topological quantum order: stability under local perturbations. Journal of mathematical physics, 51(9), 2010.
[^10]: Barbara M Terhal. Quantum error correction for quantum memories. Reviews of Modern Physics, 87(2):307, 2015.