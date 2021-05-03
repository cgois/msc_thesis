# Composite systems and entanglement

[Citação Dagmar Bruss]

- Section \ref{sec:states_transformations_measurements} was dedicated to review the mathematical structures used to represent states, transformations and measurements in quantum theory. Special emphasis was put on those aspects of quantum measurements that most drastically differ from their classical counterparts, such the existence of incompatible measurements. A second structure also at the core of the most unusual of quantum behaviors is \emph{entanglement} --- a property that may or not be present in composite quantum systems. The unusual correlations that entanglement may originate were pointed out as early as 1935 by Einstein, Podolsky and Rosen \cite{}, and also discussed by Schrödinger, who coined the term (originally, ``Verschränkung'') \cite{}. This discussion was later rescued by John Bell in 1964 \cite{}, and since then been extensively tested and developed \cite{}, ultimately becoming a central feature of many quantum informational protocols, such as superdense coding \cite{}, quantum key distribution \cite{} and teleportation \cite{}. As with quantum measurements, this a vast and endlessly interesting field of study in itself, which we now review with special focus on bipartite systems and making no attempt of comprehensiveness.



- Entanglement --- and its opposite concept, \emph{separability} ---, are properties related to composite quantum systems. If we choose $2$ for the number of subsystems, the underlying Hilbert space $\hilb$ of a state $\rho$ can be correspondingly factored as $\hilb \equiv \hilb_A \otimes \hilb_B$, for choices of  $\hilb_A$ and $\hilb_B$ respecting $\text{dim} \,\hilb_A \; \text{dim} \,\hilb_B = \text{dim } \hilb$. Using the tensor product for composition is the quantum analogue of using the Cartesian product to build composite phase spaces in classical mechanics.
- Letting $\{ \ket{ \psi_i } \}_{i=1}^{d_A}$ and $\{ \ket{ \varphi_\alpha } \}_{\alpha=1}^{d_B}$ be orthonormal bases for $\hilb_A$ and $\hilb_B$, respectively, we can easily build an orthonormal basis for $\hilb$ as $\{ \ket{\psi_i} \otimes \ket{\varphi_\alpha} \}_{i=1, \alpha = 1}^{d_A, d_B}$. Analogously, with $\{ \ketbra{\psi_i}{\psi_j} \}_{i,j=1}^{d_A}$ as a basis for $\mathcal{L}(\hilb_A)$ and $\{ \ketbra{\varphi_\alpha}{\varphi_\beta} \}_{\alpha,\beta=1}^{d_B}$ one for $\mathcal{L}(\hilb_B)$, any operator $O \in \mathcal{L}(\hilb)$ may be decomposed as

$$
O = \sum_{ij\alpha\beta} O_{ij\alpha\beta} \ketbra{\psi_i}{\psi_j} \otimes \ketbra{\varphi_\alpha}{\varphi_\beta}
\label{eq:decomposed-operator}
$$

- Suppose $A$ is an operator acting only on the part $O^A \in \mathcal{L}(\hilb_A)$ of $O$. The corresponding operator in $\hilb$ is just $A \otimes \id_B$. To find a description for $O^A$, we notice that the expectation value $\tr{A \otimes \id_B \,O}$ should be equal to $\tr{ A \,O^A}$, and to comply with it we define the partial trace $\text{tr}_B : \mathcal{L}(\hilb_A \otimes \hilb_B) \mapsto \mathcal{L}(\hilb_A)$ as

$$
\ptr{B}{O} \equiv \sum_{ij\alpha\beta} O_{ij\alpha\beta} \,\tr{\ketbra{\psi_i}{\psi_j}} \otimes \ketbra{\varphi_\alpha}{\varphi_\beta} = \sum_{i\alpha\beta} O_{ii\alpha\beta} \ketbra{\varphi_\alpha}{\varphi_\beta}
$$

- and call $O^A = \ptr{B}{O}$ the reduced operator. This definition can be trivially adapted to tracing out the first subsystem instead of the second, and to dealing with more than two subsystems. Moreover, it can be shown that this is the unique operation satisfying the expectation value equality condition, and that it is also completely positive and trace preserving (the significance of these latter conditions will be discussed later) \cite{}. This operation is especially useful when applied to density operators, in which case we call $\ptr{B}{\rho} = \rho^A$ the \emph{reduced state} (of $\rho$ in subsystem $A$).

- Given a factorization of $\hilb$, a state $\rho$ acting on $\hilb$ is said to be \emph{separable} if and only if it can be written as 
  $$
  \rho = \sum_i p_i \rho_i^A \otimes \rho_i^B
  \label{eq:separable-state}
  $$

- where the $p_i$ are probabilities, and $\rho_i^A \in \hilb_A$; correspondingly for $\rho_i ^B$. A state that is not separable is entangled. For pure states, this reduces to $\ket{\psi}_{AB} = \ket{\psi}_A \otimes \ket{\psi}_B$, and when this is not possible to write, $\ket{\psi}_{AB}$ is entangled. 

- Asking whether a state $\rho \in \hilb$ is entangled is only meaningful when the factorization structure is specified. As a matter of fact, any bipartite pure entangled state $\ket{\psi} \in \hilbd{2}_A \otimes \hilbd{2}_B$ can be made separable by a fitting choice of factorization \cite{}. This observation implies that entanglement is a property of a state \emph{with respect to} a choice of subsystems, and not of the state in itself.

- Naturally, one may also discuss entanglement in larger number of subsystems \cite{}, but the complexity scales significantly fast, and the discussion would be of little usefulness to our objective.

- A rationale for the definition of separability comes from a preparation procedure \cite{werner1989}. Consider two separate laboratories, each equipped with a device that prepares quantum states, and sharing a source of (classical) randomness. Given a random number $i$, generated by the source with probability $p_i$, the laboratories locally prepare states $\rho_i^A$ and $\rho_i^B$. The first laboratory then measures $\mathcal{M}_A$, and the second $\mathcal{M_B}$, each on their respective preparation. For a pair of measurement effects $E_{m_A} \in \mathcal{M}_A$ and $E_{m_B} \in \mathcal{M}_B$,

$$
p(m_A, m_B) = \sum_i p_i \tr{E_{m_A} \rho_i^A} \tr{E_{m_B} \rho_i^B} = \tr{ E_{m_A} \otimes E_{m_B} \rho}
$$

- where $\rho$ matches the definition of a separable state. With this discussion, it is also clearer that separable states are \emph{not} uncorrelated. However, they may only exhibit correlations as strong as the ones possible in classical systems, and for this reason are said to be \emph{classically correlated}. Entangled states, conversely, manifest correlations that are not classically reproducible, which makes it a intrinsically nonclassical property.
- Properly justified, the definition of entanglement is quite amicable. On the other hand, determining whether a given state $\rho$ can be decomposed as in eq.~\eqref{eq:separable-state} or not is a daunting task. Even in bipartite structures, the problem is fully solved only under special circumstances, such as dimensionally limited Hilbert spaces, or for some special classes of quantum states, including Werner states, isotropic states and pure states. These will be important in due time, so we discuss them now.
- Whenever we limit the dimensions as $\hilb = \hilbd{2} \otimes \hilbd{2}$ or $\hilb = \hilbd{2} \otimes \hilbd{3}$, the \emph{positive partial transpose} (PPT) criterion provides a necessary and sufficient condition for entanglement. In all other cases, the condition is still sufficient, though not necessary. To understand this last affirmation, we recall that the \emph{partial transpose} is a transposition operation acting only on some subsystems. Reusing the decomposition in eq.~\eqref{eq:decomposed-operator}, the partial transpose over $B$ is defined as

$$
O^{\intercal_B} = (\id_A \otimes T)\,O = \sum_{ij\alpha\beta} O_{ij\alpha\beta} \ketbra{\psi_i}{\psi_j} \otimes \ketbra{\varphi_\beta}{\varphi_\alpha} = \sum_{ij\alpha\beta} O_{ij\beta\alpha} \ketbra{\psi_i}{\psi_j} \otimes \ketbra{\varphi_\alpha}{\varphi_\beta}
$$

- where $T$ stands for the transposition map. Now suppose that we take a separable state $\rho$ and transpose, for instance, its second subsystem (the argument is equivalent for transposing the other). Then $\rho^{\intercal_B} = \sum_i p_i \rho_i^A \otimes \left( \rho_i^B \right)^\intercal$. Building on the fact that $\rho_i^B$ was a valid density operator, and that the transpose preserves its trace and eigenvalues, it follows that $\left( \rho_i^B \right)^\intercal$ is also a density operator. With $\rho_i^A$ left unchanged, this implies that $\rho^{\intercal_B} \succeq 0$. Consequently, all separable states have positive partial transpose, which also implies that whenever the partial transpose of $\rho$ has negative eigenvalues, $\rho$ is entangled. Shortly after Peres made this argument \cite{}, Horodecki et al. showed that for $d_A d_B \leq 6$ the PPT criterion is actually necessary \emph{and} sufficient: no entangled states in these factorizations have positive partial transpose \cite{}. For larger dimensions, though, they also prove this is false.

- [Isotropic and Werner states]
- For pure bipartite states, things are much easier. [schmidt decompositino]
- [Entanglement measures, schmidt number, singlet fraction]
- [Transformações em estados compostos: unitaŕia no global mas as vezes queremos operr localmente... então mapas CPTP and isomotphism]



# Dúvidas

- Só da pra separar com outra escolha de fatorização no caso de bipartido? Ou vale pra qualquer caso?