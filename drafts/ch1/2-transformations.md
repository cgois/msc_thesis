# Transformations

We now know how to describe static physical systems, which is something that physical systems rarely are. In quantum theory, the evolution of a closed system is governed by the Schrödinger equation. Its solution dictates that an initial state $\rho$ that transforms to $\rho^\prime$ does so unitarily following $\rho^\prime = U \rho U^\dagger$. Here, $U$ must be an unitary operator, which means that $UU^\dagger = U^\dagger U = \id$. Given $U$, we can always find a Hamiltonian $H$ and a suitable interaction time to perform the evolution. Nonetheless, these are not the most general transformations that a quantum state can undergo.

Taking the operational approach, we will define the most general transformation as any one that takes a density operator into another, i.e., any $\mathcal{N} : \mathcal{D}(\hilb) \mapsto \mathcal{D}(\hilb^\prime)$, and look to what properties this implies. First of all, $\mathcal{N}$ must be linear, and the reasoning for that goes as usual: if we mix $\rho, \sigma \in \hilb$ as $w \rho + (1-w) \sigma$ then put it through $\mathcal{N}$, we surely expect the resulting state to be equivalent to independently passing $\rho$ and $\sigma$ through $\mathcal{N}$ and then mixing. Equation-wise, this means that $\mathcal{N} \left[ w \rho + (1-w) \sigma \right] = w \mathcal{N}(\rho) + (1-w) \mathcal{N}(\sigma)$. Additionally, it is easy to argue that $\mathcal{N}$ must be such that, for any $\rho \in \mathcal{D}(\hilb)$, it is trace-preserving, $\text{tr}\left[ \mathcal{N}(\rho) \right] = 1$, and positive, $\mathcal{N}(\rho) \succeq 0$.

Positivity, however, is not a strong enough condition. Suppose that we add an auxiliary system $\hilb_B$ of arbitrary dimension to $\hilb$, thus $\hilb \mapsto \hilb \otimes \hilb_B$, and $\hilb^\prime \mapsto \hilb^\prime \otimes \hilb^\prime_B$, and that $\mathcal{N} \equiv \mathcal{N}_{\hilb \rightarrow \hilb^\prime} \otimes \id_B$. In some situations like this, a positive $\mathcal{N}_{\hilb \rightarrow \hilb^\prime}$ does not guarantee that $\mathcal{N}$ will map all input states to positive operators. This is precisely the case of the transposition map previously discussed, where the fact the the partial transposition may generate non-positive operators is used as an entanglement criterion. 

Amending this requires the stronger condition of \emph{complete positivity} (CP), whereby any CP map $\mathcal{N}$ generates a valid density operator no matter what the dimension of $\hilb_B$ is.

Together, complete positivity and trace preservation are the conditions that define a CPTP map, or \emph{quantum channel} $\mathcal{N}$, which is the most general type of quantum evolution we will consider.

These requirements are easily agreeable, but they are not very practical. What we must now do is find a computation-friendly representation for CPTP maps. This can be found in the Kraus representation theorem \cite{original,wilde-proof}, stating that general map $\mathcal{N} : \mathcal{L}(\hilb) \mapsto \mathcal{L}(\hilb^\prime)$ is CPTP (i.e., a quantum channel) if and only if it has a decomposition
$$
\mathcal{N}(O) = \sum_{i=1}^D K_i O K_i^\dagger ,
$$
where $O \in \mathcal{L}(\hilb)$, all $K_i : \mathcal{L}(\hilb) \mapsto \mathcal{L}(\hilb^\prime)$, and $\sum_{i=1}^d = K_i^\dagger K_i = \id_{\hilb}$. The limit of the sum, $D$, will be at least $1$ (in this case we recover an unitary evolution), and will never need to be larger than $\text{dim}(\hilb) \,\text{dim}(\hilb^\prime)$.

Although the Kraus representation is quite useful, there are several other convenient representations for CPTP maps \cite{https://arxiv.org/pdf/1111.6950.pdf}, of which we will just need the one called \emph{Choi-matrix representation}. It comes from an application of the \emph{Choi-Jamiołkowski isomorphism} \cite{https://doi.org/10.1016/0034-4877(72)90011-0, http://dx.doi.org/10.1103/PhysRevA.87.022310}. This remarkable result states that any quantum channel $\mathcal{N} : \mathcal{L}(\hilb) \mapsto \mathcal{L}(\hilb^\prime)$ can be uniquely mapped to a bipartite state
$$
\rho_{\mathcal{N}} = \left(\id_{\hilb} \otimes \mathcal{N} \right) \rho_{\Phi^+} \in \mathcal{D}(\hilb) \otimes \mathcal{D}(\hilb) ,
$$

where $\rho_{\Phi^+} = \sum_{i,j=1}^{d_{\hilb}} \ketbra{ii}{jj}$ is the density operator of the previously introduced maximally entangled state \cite{}. Taking a closer look, this is actually saying that the space of CPTP maps to the space of bipartite quantum states, and the way to do it is to apply the $\mathcal{N}$ in question to half of that maximally entangled state, while doing nothing to the second part. This is why it is also called \emph{channel-state duality}. And finally, to finish the isomorphism, we must also know how to go back, which is done through
$$
\mathcal{N}_\rho = \ptrb{\hilb}{\rho_{\mathcal{N}} \left( \rho^\intercal \otimes \id_{\hilb^\prime} \right)} .
$$

The representation of quantum channels as bipartite states will become handy when dealing with optimization problems over channels, where a CPTP constraint can be cast as a positivity condition (see sec. \ref{sec:sdps} and sec. \ref{sec:pam-quantum-optimization}.

