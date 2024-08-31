 Let $\mathcal{C}$ be the code subspace of a stabilizer code, defined in terms of the stabilizer group $S$. The code subspace can be viewed as the ground state subspace of a Hamiltonian of the form $\hat{H} = \sum_{i=1}^{m}{(I-s_i)}/{2}$, where $\{s_1, \ldots, s_m\} \subset S$ is a set of generators. Note that the energy barrier depends on the choice of the generating set. For an operator $P$ in the Pauli group $\mathcal{P}$, the energy of the state $P|\psi\rangle$ is given by $\bra{\psi}P^\dagger \hat{H} P\ket{\psi} = \epsilon(P)$. Here $\ket{\psi}$ is any ground state with $\bra{\psi}\hat{H}\ket{\psi} = 0$, and $\epsilon(P)$ is the energy cost of $P$. This is the number of $s_i$s that anti-commute with $P$, i.e., $\epsilon(P) = | \{i: s_iP = -Ps_i\}|$. Equivalently, one may define the energy barrier in terms of the parity check matrix $H$ of the stabilizer code. Let $v(P)$ be the binary (bit-string) representation of a Pauli $P$:

$\epsilon(P) = \text{wt}(Hv(P)).$

The minimum energy associated with a Pauli $P$ is the smallest value of $\epsilon_{\text{max}}$ across all possible [[path]]s from $0$ to $P$. This is the energy barrier of $P$, denoted as $\Delta(P)$:

 $\Delta(P) = \min_{r\in w(I,P)}\epsilon_{\max}(r).$

The energy barrier of the quantum code is the minimum energy barrier over the set of nontrivial logical operators.

> [!Definition]
>  Let $S$ be a stabilizer group, and $L(S)$ be the set of nontrivial logical operators. The energy barrier is  
>  $\Delta(H) := \min_{\ell \in L(S)}\Delta(\ell).$

This is the smallest energy the environment has to overcome to enact a logical operation on the encoded qubit.