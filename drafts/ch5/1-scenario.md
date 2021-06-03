# Dense coding as prepare-and-measure

In dense coding, two parties share an entangled pair and communicate via a quantum state. Quantum communication happens one-way, and the transmitted state is of the same local dimension (w.r.t. the encoding device) as the entangled pair. The task is to encode a classical message $x \in \mathcal{X} \equiv \posrange{N-1}$, and it is known that two \emph{d}its ($N = d^2$) can be perfectly recovered from one qudit of communication, for some choices of a measurement with $N$ outcomes \cite{}.

Translating to the prepare-and-measure lingo, we let Alice and Bob share an entangled state $\rho \in \densop{\hilb_A \otimes \hilb_B}$ as a resource. Their local dimensions, $\dim{\hilb_A} = d_A$ and $\dim{\hilb_B} = d_B$, need not be the same, but Alice's preparation must be of dimension $d_A$. To achieve quantum advantage in the dense coding task, Alice and Bob must be able to exploit the correlations available in their entangled pair. Under the circumstances, her most general strategy is to apply a local transformation $\Lambda_x : \densop{\hilb_A} \mapsto \densop{\hilb_A}$ directly on her share of $\rho$, then send it to Bob. After that,
$$
\rho \mapsto \left( \Lambda_x \otimes \id \right)\rho \equiv \rho_x
$$
will be in his possession. It is crucial to enforce that
$$
\ptr{A}{\rho_x} = \ptr{A}{\rho_{x^\prime}} \quad\forall x, x^\prime ,
$$
a condition remindful of no-signalling, for it subsumes the fact the Alice's operations, being local, cannot affect Bob's marginal state.

On his end, a good selection of a quantum measurement $\mathcal{M} = \{ E_b \}_{b=0}^{k-1}$ may provide advantage (over classical encodings) in the task of recovering her choice of $x$. Naturally, $\sum_b E_b = \id$, and each $E_b$ is a positive semidefinite operator acting on $\hilb_A \otimes \hilb_B$, which means to say he measures on both his and her transformed share of $\rho$. Summing it up, dense coding behaves in $\mathcal{Q}^\rho_{d_A,d_A^2,d_A^2,1}$, but we will also discuss some further generalizations.

Many rounds of this protocols allow them to collectively infer the behavior
$$
\mathbf{p} = \{ \condprob{b}{x} \}_{b,x} = \{ \tr{\rho_x E_b } \}_{b,x} ,
$$
and from it we can assess their performance. To that end, we assume that her choices of $x$ are equiprobable in $\mathcal{X}$ and define the probability of success as
$$
p_{\text{suc}} = \frac{1}{N} \sum_0^{N-1} \condprob{b=x}{x} .
$$
This is the very same average success probability discussed under the random access coding protocols of sec. \ref{sec:racs}, except that we now deal with a single measurement on Bob's side. Differently from the usual dense coding formulation --- which requires knowledge on the exact preparations and measurements employed ---, computing $p_{\text{suc}}$ relies solely observational data. It is thus a device independent figure of merit, completing our device independent formulation of the dense coding protocol.

Generalizations, such as letting Bob choose from $Y > 1$ measurements, are possible. We discuss a first result towards that direction at the end of sec. \ref{sec:dense-coding-results}. Another interesting possibility is to allow Alice's local dimension $d_A$ to be larger than the actual communicated qudit, i.e., to let $\Lambda_x : \densop{d_A} \mapsto \densop{d}$, with $d < d_A$. First discussions on that situation were recently started in \cite{rigidity,tavakolieapam}.