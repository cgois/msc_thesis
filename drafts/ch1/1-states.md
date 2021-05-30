# States

A structure at the core of the most unusual of quantum behaviors is \emph{entanglement} --- a property that may or not be present in composite quantum systems. The unusual correlations that entanglement may originate were pointed out as early as 1935 by Einstein, Podolsky and Rosen \cite{}, and also discussed by Schrödinger, who coined the term (originally, "Verschränkung'') \cite{}. This discussion was later rescued by John Bell in 1964 \cite{}, and since then been extensively tested and developed \cite{}, ultimately becoming a central feature of many quantum informational protocols, such as superdense coding \cite{}, quantum key distribution \cite{} and teleportation \cite{}. Entanglement theory is a vast and endlessly interesting field of study in itself, some aspects of which I now review with special focus on bipartite systems, and making no attempt of comprehensiveness.



A \emph{quantum state} is described by a \emph{density operator}, commonly denoted by $\rho$.  Any density operator is a linear, unit-trace and positive-semidefinite operator in a Hilbert space $\hilb$. Conversely, any operator satisfying these properties represents a valid quantum state. Hence, $\mathcal{D}(\hilbd{d}) = \{ \rho \in \mathcal{L}(\mathcal{H}^d) \mid \text{tr}\rho=1, \rho \succeq0 \}$, where $\mathcal{L}(\mathcal{H}^d)$ is the set of linear operators in $\mathcal{H}^d$, is the space of density operators in dimension $d$. Only finite-dimensional Hilbert spaces will be considered.

As $\rho \succeq 0 \Longrightarrow \rho = \rho^\dagger$, we can use the spectral decomposition to write $\rho = \sum_m m \Pi_m$, where each $\Pi_m$ is a projection onto the eigenspace of the eigenvector of $\rho$ associated with eigenvalue $m$. Such eigenvectors are orthogonal. They need not be normalized, but we can always and will take them as being. Orthogonality imply that $\Pi_m \Pi_n = \delta_{mn} \Pi_m$ and $1 \leq \text{rank}(\rho) \leq d$, and normalization that $\tr{\Pi_m} = 1$.  Furthermore, all $m \geq 0$, and $\tr{\rho} = 1 \Longrightarrow \sum_m m = 1$. 

You may recall the more usual definition that a quantum state is described by a unit vector in a Hilbert space and, conversely, that such unit vectors describe quantum states. This is only true for a subset of states called \emph{pure quantum states}. 

Following along the tradition, we will denote pure quantum states as $\lvert \psi \rangle$, where $\psi$ is some label that describes the state. Similar notation is used for the dual vector $\left( \lvert \psi \rangle \right)^\dagger \equiv \langle \psi \rvert$, which is useful to write the inner product between any two vectors in the same space as $\langle \psi \vert \phi \rangle$, and the outer product as $\lvert \psi \rangle \langle \phi \rvert$. An useful geometric intuition on these products is to interpret the inner product as the overlap between $\vert \psi \rangle$ and $\vert \phi \rangle$, and an outer product $\lvert \psi \rangle \langle \psi \rvert$ as a projection onto $\lvert  \psi \rangle$.

Recalling that all eigenvectors of a density operator $\rho$ are normalized, we may now interpret the $\Pi_m \equiv \ketbra{m}{m}$ as projections onto the pure states labeled by $\ket{m}$, and the spectral decomposition $\rho = \sum_m m \Pi_m$ as a probability distribution, weighted by the eigenvalues $m$, over those. Any pure state $\ket{\psi}$ can equivalently be described as $\rho = \ketbra{\psi}{\psi}$, and whenever $\text{rank}(\rho) = 1$, we may infer that $\rho$ stands for a pure state. Equivalently, whenever $\rho$ is such a one-dimensional projection, the \emph{purity} $\tr{\rho^2} = 1$, while in general $1/d \leq \tr{\rho^2} \leq 1$. This is one of the reasons why density matrices are more general than pure states. All other density operators (i.e., those of non-unit rank) are said to describe \emph{mixed quantum states}. Although the spectral decomposition of $\rho$ suggests that a mixed state can be interpreted as a probability distribution over pure states, the understanding of a mixed state as lack of knowledge on the exact state of the system should not be taken literally \cite{arxiv}. One of several reasons for this assertion is that there may be many pure state ensembles generating the same density operator \cite{Physics Letters A 183 (1993) 14-18}.

Given a basis $\{ \lvert e_i \rangle \}_{i=1}^d$ for $\mathcal{H}^d$, any pure state $\lvert \psi \rangle$ in $\mathcal{H}^d$ can be written as $\lvert \psi \rangle = \sum_{i=1}^d c_i \lvert e_i \rangle$, where the $c_i \in \mathbb{C}$ and $\sum_i \abs{c_i}^2 = 1$ due to $\braket{\psi}{\psi} = 1$. We will frequently be interested in $\mathcal{H}^2$, in which it's common to work with the orthonormal *computational basis* $\{ \lvert 0 \rangle, \lvert 1 \rangle \}$. The vector representations associated with the computational basis elements are $\lvert 0 \rangle \equiv \left( 1 \; 0 \right)^\intercal$ and $\lvert 1 \rangle \equiv \left( 0 \; 1 \right)^\intercal$. Any $\lvert \psi \rangle \in \mathcal{H}^2$ can thus be identified with $\lvert \psi \rangle = c_1 \lvert 0 \rangle + c_2 \lvert 1 \rangle = \left( c_1 \; c_2 \right)^\intercal$. An extension to a generalized $d$-dimensional computational basis $\{ \ket{i} \}_{i=0}^{d-1}$ is similarly done. Due to its analogy with two-level classical systems (bits), a $\ket{\psi} \in \hilbd{2}$ is termed a quantum bit (\emph{qubit}) and, similarly, any $\ket{\psi} \in \hilbd{d}$ is a qu\emph{d}it.





Entanglement --- and its opposite concept, \emph{separability} ---, are properties related to composite quantum systems. If we choose $2$ for the number of subsystems, the underlying Hilbert space $\hilb$ of a state $\rho$ can be correspondingly factored as $\hilb \equiv \hilb_A \otimes \hilb_B$, for choices of  $\hilb_A$ and $\hilb_B$ respecting $\text{dim} \,\hilb_A \; \text{dim} \,\hilb_B = \text{dim } \hilb$. Using the tensor product for composition is the quantum analogue of using the Cartesian product to build composite phase spaces in classical mechanics.

Letting $\{ \ket{ \psi_i } \}_{i=1}^{d_A}$ and $\{ \ket{ \varphi_\alpha } \}_{\alpha=1}^{d_B}$ be orthonormal bases for $\hilb_A$ and $\hilb_B$, respectively, we can easily build an orthonormal basis for $\hilb$ as $\{ \ket{\psi_i} \otimes \ket{\varphi_\alpha} \}_{i=1, \alpha = 1}^{d_A, d_B}$. This means that any vector $\ket{\psi} \in \hilb$ has a decomposition
$$
\ket{\psi} \sum_{i=1}^{d_A}\sum_{\alpha=1}^{d_B} c_{i\alpha} \ket{\psi_i, \varphi_\alpha}
\label{eq:pure-state-decomposition}
$$

Analogously, with $\{ \ketbra{\psi_i}{\psi_j} \}_{i,j=1}^{d_A}$ as a basis for $\mathcal{L}(\hilb_A)$ and $\{ \ketbra{\varphi_\alpha}{\varphi_\beta} \}_{\alpha,\beta=1}^{d_B}$ one for $\mathcal{L}(\hilb_B)$, any operator $O \in \mathcal{L}(\hilb)$ may be decomposed as
$$
O = \sum_{ij\alpha\beta} O_{ij\alpha\beta} \ketbra{\psi_i}{\psi_j} \otimes \ketbra{\varphi_\alpha}{\varphi_\beta}
\label{eq:decomposed-operator}
$$

Suppose $A$ is an operator acting only on the part $O^A \in \mathcal{L}(\hilb_A)$ of $O$. The corresponding operator in $\hilb$ is just $A \otimes \id_B$. To find a description for $O^A$, we notice that the expectation value $\tr{A \otimes \id_B \,O}$ should be equal to $\tr{ A \,O^A}$, and to comply with it we define the \emph{partial trace} (over the $B$) $\text{tr}_B : \mathcal{L}(\hilb_A \otimes \hilb_B) \mapsto \mathcal{L}(\hilb_A)$ as
$$
\ptr{B}{O} \equiv \sum_{ij\alpha\beta} O_{ij\alpha\beta} \,\tr{\ketbra{\psi_i}{\psi_j}} \otimes \ketbra{\varphi_\alpha}{\varphi_\beta} = \sum_{i\alpha\beta} O_{ii\alpha\beta} \ketbra{\varphi_\alpha}{\varphi_\beta}
$$

and call $O^A = \ptr{B}{O}$ the reduced operator. This definition can be trivially adapted to tracing out $\hilb_A$ instead, and to dealing with more than two subsystems. Moreover, it can be shown that this is the unique operation satisfying the expectation value equality condition, and that it is also completely positive and trace preserving (the significance of these latter conditions will be discussed later) \cite{}. This operation is especially useful when applied to density operators, in which case we call $\ptr{B}{\rho} = \rho^A$ the \emph{reduced state} (of $\rho$ in subsystem $A$).

Given a factorization of $\hilb$, a state $\rho$ acting on $\hilb$ is said to be \emph{separable} if and only if it can be written as 
$$
\rho = \sum_i p_i \rho_i^A \otimes \rho_i^B
\label{eq:separable-state}
$$
where the $p_i$ are probabilities, and $\rho_i^A \in \hilb_A$; correspondingly for $\rho_i ^B$. A state that is not separable is entangled. For pure states, this reduces to $\ket{\psi}_{AB} = \ket{\psi}_A \otimes \ket{\psi}_B$, and when this form is not possible, $\ket{\psi}_{AB}$ is entangled. 

Asking whether a state $\rho \in \hilb$ is entangled is only meaningful when the factorization structure is specified. As a matter of fact, any bipartite pure entangled state $\ket{\psi} \in \hilbd{2}_A \otimes \hilbd{2}_B$ can be made separable by a fitting choice of factorization \cite{terra}. This observation implies that entanglement is a property of a state \emph{with respect to} a choice of subsystems, and not of the state in itself. Naturally, one may also discuss entanglement in larger number of subsystems \cite{review}, but the complexity scales significantly fast, and the discussion would be of little usefulness to our objective.

A rationale for the definition of separability comes from a preparation procedure \cite{werner1989}. Consider two separate laboratories, each equipped with a device that prepares quantum states, and sharing a source of (classical) randomness. Given a random number $i$, generated by the source with probability $p_i$, the laboratories locally prepare states $\rho_i^A$ and $\rho_i^B$. The first laboratory then measures $\mathcal{M}_A$, and the second $\mathcal{M}_B$, each on their respective preparation. For a pair of measurement effects $E_{m_A} \in \mathcal{M}_A$ and $E_{m_B} \in \mathcal{M}_B$,
$$
p(m_A, m_B) = \sum_i p_i \tr{E_{m_A} \rho_i^A} \tr{E_{m_B} \rho_i^B} = \tr{ E_{m_A} \otimes E_{m_B} \rho}
$$

where $\rho$ matches the definition of a separable state. With this discussion, it is also clearer that separable states are \emph{not} uncorrelated. However, they may only exhibit correlations as strong as the ones possible in classical systems, and for this reason are said to be \emph{classically correlated}. Entangled states, conversely, manifest correlations that are not classically reproducible, which makes it a intrinsically nonclassical property.

Properly justified, the definition of entanglement is quite amicable. On the other hand, determining whether a given state $\rho$ can be decomposed as in eq.~\eqref{eq:separable-state} or not is a daunting task. Even in bipartite structures, the problem is fully solved only under special circumstances, such as for pure states, dimensionally limited Hilbert spaces, or for some special families of quantum states, including Werner states and isotropic states. These will become important in due time, so we discuss them now.



For bipartite pure states of any dimension, the problem can be fully solved through the so-called Schmidt decomposition. The Schmidt decomposition theorem states that any $\ket{\psi} \in \hilb_A \otimes \hilb_B$ can be decomposed as $\ket{\psi} = \sum_{i=1}^d \eta_i \ket{i_A} \otimes \ket{i_B}$, where $\{ \ket{i_A} \}_{i=1}^{d_A}$ and $\{ \ket{i_B} \}_{i=1}^{d_B}$ are orthonormal bases for $\hilb_A$ and $\hilb_B$, respectively, $\eta_i \geq 0$, and $d = \min \{d_A, d_B\}$. We call $\eta_i$ \emph{Schmidt coefficients}, denote by $r_S(\psi)$ the number of non-zero coefficients (\emph{Schmidt rank}), and say $\{ \eta_i (\psi) \}_{i=1}^{r_S(\psi)}$ is the \emph{Schmidt spectrum}.

Contrasted to eq.~\eqref{eq:pure-state-decomposition}, this is a remarkable simplification. For one, this representation requires a single sum, but also, $d$ is the \emph{minimum} local dimension, irrespective of how (finitely) large the other dimension may be. It is also quite similar to the concept of separability versus entanglement for pure states. Actually, it can be shown that a pure bipartite state $\ket{\psi}$ is entangled if and only if its Schmidt rank $r_S(\psi)$ is larger than one; equivalently, if the Schmidt decomposition has more than one term, or if any $\eta_i = 1$, because $\sum_i \eta_i^2 = 1$.



This observation urges us to ask: are some states \emph{more entangled} than others, and can the Schmidt spectrum be used to measure this? Attempting to adequately discuss \emph{entanglement measures} would be going too far. However, as some introductory basic concepts will turn useful, we discuss them with no intention on reproducing the thoroughness in \cite{plenio,terra,reviewhorodecki,dagmar}.

The first important thing is that there is a whole zoo of entanglement measures, such as concurrence, negativity, entanglement of formation, etc. The second is that they do not always agree with each other on the ordering they impose on the set of entangled states. Thus, depending on the intended use, there may be some measure more adequate than another. Nevertheless, there are several desirable properties for an entanglement measure $E : \mathcal{D}(d) \mapsto \mathbb{R}$ to satisfy, such as $E(\rho) = 0$ if $\rho$ is separable, and that it should not increase under local operations with classical communication (LOCC); a condition reminiscent of the operational definition of separability given above.

Making the Schmidt spectrum respect the first condition is easy (just subtract $1$). Using it to impose a partial ordering on the set of pure states requires some extra caution, but it can be done through majorization. We first order the \emph{Schmidt spectrum} $\{ \eta_i (\psi) \}_{i=1}^{r_S(\psi)}$ of some state $\ket{\psi}$ in non-increasing order, then define
$$
\psi \succ \varphi \;\Longleftrightarrow\; \sum_{i=1}^{r} \eta_i^2(\psi) \geq \sum_{i=1}^{r} \eta_i^2(\varphi), \;\forall r .
$$

Then, if $\psi \succ \varphi$, we can safely say that $\ket{\psi}$ is \emph{more} entangled than $\ket{\varphi}$, in the sense that we may convert $\ket{\psi}$ to $\ket{\phi}$ solely with LOCC \cite{Phys. Rev. Lett. 83 436,terra}. With this in mind, states for which $\eta_i = 1/\sqrt{d}$ are said to be \emph{maximally entangled}.

Although the Schmidt decomposition only works for pure states, the idea of the Schmidt rank can be nicely generalized to an entanglement measure over mixed states. The so called \emph{Schmidt number} \cite{/PhysRevA.61.040301,theother} is given by 
$$
r_S(\rho) = \min_{\{ \ket{\psi_i} \}_i} \{ \max_i \left[ r_S(\psi_i ) \right] \} ,
\label{eq:schmidt-number}
$$

where I reuse the notation $r_S$ from the Schmidt rank because the two notions are equivalent for pure states.

Arguably opaque, this definition is better understood through a procedure. Starting from $\rho$, we find an ensemble of pure states $\rho = \sum_i p_i \ketbra{\psi_i}{\psi_i}$ for it, list the $r_S(\psi_i)$ for each state of the ensemble, and take the maximum (this constitutes the inner maximization). However,  the decomposition we choose for $\rho$ is not, in general, unique. So we do this procedure for all possible sets of pure states $\{ \psi_i \}_i$ that may be used to build $\rho$, and take the minimum element of the resultant set, which is what the outer minimization means. Denoting as $S_k$ the set of density operator with Schmidt number less than or equal to $k$, it will be of most importance for us that $S_{k-1} \subset S_k$, that $S_1$ is the set of separable states, that each $S_k$ is a convex set, and that its extremal points are the pure states.



Going back to the problem of determining whether a given $\rho$ is entangled, whenever we limit the dimensions as $\hilb = \hilbd{2} \otimes \hilbd{2}$ or $\hilb = \hilbd{2} \otimes \hilbd{3}$, the \emph{positive partial transpose} (PPT, also "Peres-Horodecki") criterion provides a necessary and sufficient condition. In all other cases, the condition is still sufficient, though not necessary. To understand the sufficiency affirmation, we recall that the \emph{partial transpose} is a transposition operation acting only on some subsystems. Reusing the decomposition in eq.~\eqref{eq:decomposed-operator}, the partial transpose over $B$ is defined as
$$
O^{\intercal_B} = (\id_A \otimes T)\,O = \sum_{ij\alpha\beta} O_{ij\alpha\beta} \ketbra{\psi_i}{\psi_j} \otimes \ketbra{\varphi_\beta}{\varphi_\alpha} = \sum_{ij\alpha\beta} O_{ij\beta\alpha} \ketbra{\psi_i}{\psi_j} \otimes \ketbra{\varphi_\alpha}{\varphi_\beta}
$$

where $T$ stands for the transposition map. Now suppose that we take a separable state $\rho$ and transpose, for instance, its second subsystem (the argument is equivalent for transposing the other). Then $\rho^{\intercal_B} = \sum_i p_i \rho_i^A \otimes \left( \rho_i^B \right)^\intercal$. Building on the fact that $\rho_i^B$ was a valid density operator, and that the transpose preserves its trace and eigenvalues, it follows that $\left( \rho_i^B \right)^\intercal$ is also a density operator. With $\rho_i^A$ left unchanged, this implies that $\rho^{\intercal_B} \succeq 0$. Consequently, all separable states have positive partial transpose, which also implies that if the partial transpose of some $\rho$ has negative eigenvalues, it must be entangled. Just for curiosity's sake: the sum of the negative eigenvalues of a partially transposed entangled state is linked to another entanglement measure, called negativity \cite{horodeckireview}.

Shortly after Peres made this argument \cite{}, Horodecki et al. showed that for $d_A d_B \leq 6$ the PPT criterion is actually necessary \emph{and} sufficient: no entangled states in these factorizations have positive partial transpose \cite{}. For larger dimensions, though, they also prove this is not always true; except under special circumstances.

One such special case is that of \emph{Werner states}. They were central to the first proof that entanglement and Bell nonlocality are not equivalent concepts \cite{}. More specifically, it was shown that a large set of entangled Werner states are nevertheless local under projective measurements. Later, the bounds were improved several times \cite{}, the result was extended to POVMs \cite{}, and they were also made pivotal in the study of quantum steering \cite{} and as a test bed for the capabilities of many quantum informational protocols, such as (semi)device-independent entanglement witnesses. What makes them especially tractable is that they are highly symmetric, as Werner states are bipartite states in $\hilbd{d} \otimes \hilbd{d}$ for which $(U \otimes U) \,\rho\, (U^\dagger \otimes U^\dagger) = \rho$. It can be shown that this is a one-parameter family of states, and that they may be written as
$$
W_d(\alpha) = \left( \frac{d-1+\alpha}{d-1} \right) \frac{\id}{d^2} - \left( \frac{\alpha}{d-1} \right) \frac{S}{d}
$$

here $S = \sum_{i,j=0}^{d-1} \ketbra{ij}{ji}$ is the swap operator. When written in this form, $\alpha = 0$ stands for the maximally mixed state, and $\alpha \leq 1$. Werner states are entangled if and only if $\alpha > \frac{1}{d+1}$ but, under projective measurements, they are unsteerable if and only if $\alpha \leq 1 - \frac{1}{d}$ \cite{}. 

A second family of states that will become useful in due time are the \emph{isotropic states}. Bipartite and also highly symmetric, they are defined as states in $\hilbd{d} \otimes \hilbd{d}$ for which $(U \otimes U^*) \,\rho\, (U^\dagger \otimes U^{*^\dagger}) = \rho$. They were originally constructed to aid in proofs of entanglement distillability criteria \cite{Phys. Rev. A 59, 4206}. Later, together with Werner states, they were used to show that entanglement, EPR steering and Bell nonlocality form a strict hierarchy \cite{}, and they have likewise been useful in a multitude of benchmarks. They can be described through a single real, linear parameter $\alpha$ by
$$
\chi(\alpha) = \left(1 - \alpha\right) \frac{\id}{d^2} + \alpha \ketbra{\Phi^+}{\Phi^+} ,
$$

with $\ket{\Phi^+} = \frac{1}{\sqrt{d}} \sum_{i = 0}^{d - 1} \ket{ii}$, a maximally entangled state. For $d = 2$, they are identical to Werner states up to local unitaries, but this is not true for larger dimensions. They are also nonseparable if and only if $\alpha > \frac{1}{d+1}$, and are unsteerable under projective measurements if and only if $\alpha \leq \frac{H_d - 1}{d-1}$, where $H_d = \sum_{n=1}^d 1/n$ \cite{}. Letting $\alpha$ run in $[0,1]$, the isotropic state $\chi(0)$ is the maximally mixed state, and for $\chi(1)$ we have a maximally entangled one.

Maximally entangled states are resources for many informational protocols, and the performance of some protocols can be characterized through the \emph{singlet fraction}, which measures the maximal overlap of a resource $\rho$ with a maximally entangled state \cite{https://doi.org/10.1103/PhysRevA.60.1888}. Starting from $\ket{\Phi^+}$, all other maximally entangled states $\ket{\Phi}$ can be reached through local unitaries alone, $\ket{\Phi} = (U_A \otimes U_B) \ket{\Phi^+}$, thus the singlet fraction is determined by
$$
\zeta(\rho) = \max_\Phi \braopket{\Phi}{\rho}{\Phi} .
$$

In particular, the singlet fraction of the isotropic states is
$$
\zeta\left[ \chi(\alpha) \right] = \alpha + \frac{1 - \alpha}{d^2} .
$$







- [Citação Dagmar Bruss onde?]







## Trechos soltos

-  A notoriously special class is that of self-adjoint operators. In finite-dimensional spaces, these are equivalent to Hermitian operators; those $A$'s for which $A = A^\dagger$. For this reason, we'll use any of the two terms interchangeably. Whenever $A$ is self-adjoint, the spectral theorem states it can be diagonalized as $\sum_m m \ketbra{m}{m}$, where the eigenvectors $\ketbra{m}{m}$ are orthonormal projectors and $m \in \mathbb{R}$ the associated eigenvalues.
-  Self-adjoint operators represent physically observable quantities, such as position or momentum, and for this reason are equivalently called \emph{observables}. When an observable $A \in \hilb$ is measured on a state vector $\psi \in \hilb$, we get a measurement result $m$ and a post-measurement state $\ket{\psi_m}$. 



-  Schrödinger's equation governs the evolution of a state $\ket{\psi(t)}$ through $i\hbar \frac{\partial}{\partial t} \ket{\psi(t)} = H\ket{\psi(t)}$, where $H$ is the system's Hamiltonian operator. Solving this equation for an arbitrary $H$ is no easy task, 



- Only finite-dimensional spaces will be considered, and of utmost importance will be the properties that, $\forall \lvert \psi \rangle, \lvert \phi \rangle, \lvert \xi \rangle \in \mathcal{H}^d,$ (i) $\alpha \lvert \psi \rangle + \beta \lvert \phi \rangle \in \mathcal{H}^d$, where $\alpha, \beta \in \mathbb{C}$, (ii) $\langle \xi \rvert \left( \alpha \lvert \psi \rangle + \beta \lvert \phi \rangle \right) = \alpha \langle \xi \vert \psi \rangle + \beta \langle \xi \vert \phi \rangle$ and (iii) $\langle \psi \vert \phi \rangle = \langle \phi \vert \psi \rangle^*$. Their physical meaning will become apparent in due course.



- If the $\lvert e_i \rangle$ are furthermore orthonormal, then $\langle \psi \vert \psi \rangle = 1 \Longrightarrow \sum_i \lvert c_i \rvert^2 = 1$. 



- Given $\rho_1, \rho_2 \in \mathcal{D}(d)$, any convex combination $w \rho_1 + (1 - w) \rho_2$ is also a valid density operator.



- Because any unitary operator is invertible --- with it's inverse being $U^\dagger$, --- quantum dynamics is reversible. And because $\left( U\ket{\psi} \right)^\dagger = \bra{\psi}U^\dagger$, then $\braopket{\psi}{U^\dagger U}{\psi} = 1$, which means we are indeed taking a pure state onto another. Although this is the only time I'll mention Schrödinger's equation, it is in order to recall that unitary evolution arises from it and that, conversely, any evolution given by a continuous family of unitary transformations $U(t)$ can be described by Schrödinger's equation with a suitable Hamiltonian operator.