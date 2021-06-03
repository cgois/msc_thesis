# Witnessing and self-testing entanglement

Understanding the relationships between some figure of merit and the underlying resources is a commonplace question in device independent scenarios. Important ones for the prepare-and-measure formulation of dense coding are which bounds the amount of entanglement in $\rho$ or its local dimensions imply on $\psuc$, and whether violating them witness or even self-tests some property of $\rho$. 

Brunner et al. \cite{dimensionwitnesses} considered similar questions in the quantum state discrimination scenario. Similarly to ours, their scenario allowed for a single measurement, and their figure of merit was equivalent to $\psuc$. However, the devices were independent, and their investigation focused on what could be inferred about quantum versus classical preparations. In chap. \ref{chap:pam}'s terminology, they were interested in analysing $\psuc$ in $\mathcal{C}_d$ against $\mathcal{Q}_d$, mainly for $Y=1$. Interestingly, they found out both classical and quantum bounds for $\psuc$ are equal to $d_A / N$. Therefore, while that success probability can be used as a dimension witness, it cannot witness the type of preparations.

Our first result generalizes theirs in the following way
%
\begin{result}
	Let $\rho$ be a shared resource with Schmidt number $s$ and local dimension $d_A$ on Alice's side. If she chooses one out of $N$ preparations, and Bob performs a single measurement with $N$ outcomes on the joint state, then
	\begin{equation}
		\psuc \leq \min \left( \frac{d_A s}{N}, 1 \right) .
	\end{equation}
	When $N \geq d_A s$, the bound is tight.
\end{result}
%
Separable states ($s=1$) thus recover the bound $\psuc \leq d_A / N$ from \cite{brunnerdimwit}. For this reason, whenever the transmitted state's dimension is knowingly $d_A$, a $\psuc > d_A / N$ witness entanglement. Because only local operations are used to prepare the $\rho_x$, and those cannot increase $s$, any $\psuc > d_A s / N$ unambiguously certifies that $\rho \notin S_s$, so providing a lower bound on its Schmidt number.

A particular instance of ineq. \ref{eq:result-1} can also be used for self-testing of maximally entangled states.
%
\begin{result}
​	In dense coding instances ($N=d_A^2$) of the prepare-and-measure scenario with $s=d_A$, saturation of ineq. \ref{eq:result-1} certifies, up to a local unitary transformation, that the shared state $\rho$ is maximally entangled.
\end{result}

Interestingly, this has implications for quantum key distribution protocols in the prepare-and-measure dense coding scenario. Suppose Alice does not actually share a maximally entangled pair with Bob, but rather with a third, malicious party that wants to eavesdrop on their communication. Let us suitably call her Eve. Apart from sharing a maximally entangled pair $\rho_{AE}$ with Alice, she intercepts Alice's communication of her share of $\rho_x$. From result \ref{res:self-testing-maximally-entangled}, she reads out $x$ with $\psuc = 1$, thus perfectly learning Alice's message. Because, at the end of the day, it will be Alice and Bob who share data to infer their $\psuc$, Eve must share a second maximally entangled pair $\rho_{EB}$ with Bob, which she exploits to reencode $x$ and transmit to Bob. In this way, Alice and Bob's $\psuc$ will saturate, tricking them into believing they share a maximally entangled pair. As Eve succeeds in eavesdropping without being detected, the prepare-and-measure dense coding protocol is not cryptographically secure.

Historically, dense coding was introduced as a perfect encoding protocol. Relaxing this condition can shine more light on the role of entanglement assistance. Sharing pure entangled states, as the following result shows, is always advantageous over having only classical correlations (in the form of separable states).

\begin{result}

​	Sharing a pure entangled state, which we write in the Schmidt decomposition $\ket{\psi} = \sum_{i = 0}^{s-1} \eta_i \ket{i} \otimes \ket{i}$, the best probability of success in the encoding of $N = d_A^2$ dits is lower bounded as
$$
\psuc \geq \min \left( \frac{1 + \Gamma}{d_A}, \,1 \right),
$$
where $\Gamma \equiv \sum_{i \neq j} \eta_i \eta_j \geq 0$. As, from result \ref{res:1}, $N = d_A^2$ with $\rho \in \text{SEP}$ implies that $\psuc \leq 1 / d_A$, and as an entangled state is such that $\Gamma > 0$, all pure entangled states provide quantum advantage in the dense coding protocol.

\end{result}

As a corollary, we have an amusing alternative proof to the possibility of perfectly encoding two dits in a qudit: a maximally entangled state has all $\eta_i = 1 / \sqrt{d_A}$ (c.f. sec. \ref{sec:states}), by which $\Gamma = d_A - 1$, thus $\psuc = 1$.

Apropos of mixed states, a similar relation holds. Making use of the singlet fraction $\zeta(\rho)$, which, in a loose sense, measures how much of a maximally entangled state is in $\rho$ (sec. \ref{sec:states}), it is true that

\begin{result}

​	\begin{equation}

​		\psuc \geq \zeta(\rho) ,

​	\end{equation}

​	where $\zeta$ is the singlet fraction.

\end{result}

Particularly, an isotropic state
$$
\chi(\alpha) = \alpha \ketbra{\Phi^+}{\Phi^+} + (1 - \alpha) \frac{\id}{d_A^2} ,
$$
which is separable only in the range $\alpha \leq \frac{1}{d_A + 1}$, has the singlet fraction
$$
\zeta\left[ \chi(\alpha) \right] = \alpha + \frac{1 - \alpha}{d_A^2} ,
$$
which monotonically decreases with decreasing $\alpha$. As
$$
\zeta \left[ \chi \left( \frac{1}{d_A + 1} \right) \right] = \frac{1}{d_A}
$$
is the classical bound for $\psuc$ (result \ref{res:1}), it follows that $\psuc \geq \zeta(\rho)$ can witness entanglement for all isotropic states.

As pointed in sec. \ref{sec:states}, isotropic states are a common benchmark for quantum informational protocols. In particular, there are entanglement witnesses in the Bell nonlocality and quantum steering scenario that can certify a $\chi(\alpha)$ is entangled from some critical visibility $\alpha_{\text{crit}}$ upwards. Before contrasting them to our result, it is important to justify whether the comparison is fair. In the case of Bell nonlocality, it is not. Any prepare-and-measure scenario allow for communication, and all our witnesses rely on local dimension bounds, thus being only semi-device independent. Contrastingly, Bell nonlocality is built on a causal structure with no direct relations between the parties, and is fully device independent. Therefore, we expect any witness in this scenario to perform more poorly. The answer for quantum steering is not so clear-cut. While it also forbids communication, it does rely on local tomography for one of the parties. This presupposes full characterization of one measurement device, and hence also knowledge on the state dimension. Nevertheless, as made evident in fig. \ref{fig:singlet-witnesses} it does perform rather badly in comparison to our singlet fraction witness. The tests used were the Collins-Gisin-Linden-Massar-Popescu inequality \cite{} and Wiseman et al.'s truncated harmonic series relation \cite{} (also stated in sec. \ref{sec:states}). Neither is proven optimal, and for specific dimensions better ones are known \cite{}. \todo{Na verdade, o Otfried recomendou um teste melhor no caso de steering. Atualizar a figura e o texto depois...}

- \todo{Faithful entanglement state witness tmb}

Taking first step towards the study of more general entanglement assisted prepare-and-measure scenarios, we extend another result from the state discrimination task studied in \cite{brunnerdimwit}. In it, the authors allowed there to be $Y = N (N-1)/2$ dichotomic measurement choices, where $N$ is the number of preparations. Each measurement is labeled as the pair $(x, x^\prime)$, where $x > x^\prime$ with $x, x^\prime \in \posrange{N-1}$, and the behaviors now have elements $\condprob{b}{x,y}$. Their result states that, for uncorrelated parties, the expression
$$
V_N \equiv \sum_{x > x^\prime} \abs{ \condprob{b=1}{x, (x, x^\prime)} - \condprob{b=1}{x^\prime, (x, x^\prime)} }^2 \leq \frac{N^2}{2} \left( 1 - \frac{1}{\min(d_A,N)} \right)
$$
is a quantum dimension witness for any communication dimension $d_A < N$, and can also distinguish between quantum and classical systems (in the sense of pair-wise mutually commuting preparations, explained in sec. \ref{sec:pam-quantum}) for any $N$ which is not a multiple of $d$. By allowing for an entangled resource of Schmidt number $s$ betweenthe parties, we found the following generalization.

\begin{result}

​	Given a shared bipartite resource with Schmidt number $s$, a prepare-and-measure scenario with $N$ $d_A$-dimensional preparations labeled by $x \in \posrange{N-1}$, and $N (N-1)/2$ dichotomic measurements labeled as $(x, x^\prime)$ for $x > x^\prime$ is such that
$$
V_N \equiv \sum_{x > x^\prime} \abs{ \condprob{b=1}{x, (x, x^\prime)} - \condprob{b=1}{x^\prime, (x, x^\prime)} }^2 \leq \frac{N^2}{2} \left( 1 - \frac{1}{\min(d_A s,N)} \right) .
$$
​	If $s = d_A$, and $N < d_A^2$ or $N$ is an integer multiple of $d_A^2$, the inequality is tight.

\end{result}

For fixed $N$ and $d_A$, $V_N$ can witness whether $\rho \in S_s$ or not.


