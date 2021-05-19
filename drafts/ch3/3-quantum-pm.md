## Quantum preparations

In going from eq.~\eqref{eq:pam-classical-independent} to eq.~\eqref{eq:pam-classical-sr}, we have lifted the assumption of uncorrelated devices. To further generalize our discussion, let us also remove the assumption of classical preparations.

In that case, $\mathcal{S}$ will be a finite subset of $\mathcal{D}(\hilb)$ and $y$ a choice of quantum measurement. Employing Born's rule, we rewrite the behaviors as $\mathbf{p}_Q = \{ \tr{\rho_x E_{b \vert y}} \}_{b,x,y}$. Here, all $\rho_x \in \mathcal{S}$ and $\{ E_{b \mid y} \}_b$ is a POVM for each $y$.

To include the dimension bound, let $\text{dim}(\mathcal{S}) = \text{dim} \sum_{\rho_x \in \mathcal{S}}\text{supp}\left( \rho_x \right)$ be the smallest Hilbert space dimension needed to represent all density operators in $\mathcal{S}$. In direct analogy to the classical behaviors sets, for any fixed $X$ and $Y$, we define $\mathcal{Q}_d$ as the set of behaviors like $\mathbf{p}_Q$ but where $\text{dim}(\mathcal{S}) = d$.

Allowing for shared randomness introduces a slight change in the elements of the behaviors. Using the same notation as before, they turn into $\condprob{b}{x,y} =  \int_\Lambda \pi(\lambda) \tr{\rho_x^\lambda E_{b \vert y}^\lambda}$, making it true that $\mathcal{Q}_d^\lambda = \conv{\mathcal{Q}_d}$.


Lastly, and most importantly for chap. \ref{chap:pam-quantum}, Alice and Bob may share a quantum system $\rho \in \hilb_A \otimes \hilb_B$ and use it as a resource to improve their quantum communication. Most generally, Alice can use her share of $\rho$ in her strategy for encoding her choice of $x$. The way to do it is by applying a local CPTP map $\Lambda_x$. As we must bound the communication to $d$-dimensional systems, $\Lambda_x : \mathcal{L}(\hilb_A) \rightarrow \mathcal{L}(\hilb_C)$, where $\hilb_C \simeq \mathbb{C}^d$. This system in $\hilb_C$ is then sent to Bob, who will then hold $\rho_x = \left( \Lambda_x \otimes \id_B \right) \rho$. His measurements' effects act on $\hilb_C \otimes \hilb_B$ (fig. \ref{fig:pam-ea-quantum}). Behaviors compatible with this are in the set $\mathcal{Q}^\rho_{d}$.

Sometimes, it is a reasonable assumption to make $\hilb_A \simeq \hilb_C$ (see sec. \ref{sec:dense-coding} and chap. \ref{chap:pam-quantum}). Bear in mind, though, that it can lead to some loss of generality. Recently, Tavakoli et al. \cite{tavakoli-ea} considered a qubit communication protocol where $4$-dimensional entanglement shows advantage over having only a $2$-dimensional entangled resource. To the best of my knoledge, those, together with Moreno et al.'s (\cite{moreno} and chap. \ref{chap:pam-quantum}), were the first results considering this most general quantum communication scenario.

As a side note, although I have presented entanglement-assisted quantum communication scenarios as the most general kind of PM scenario, there are still further possible generalizations if we allow Alice's and/or Bob's inputs $x$ and $y$ to also be quantum variables \cite{guerini}. These are interesting and little explored scenarios, but dealing with them is out of our scope.


Clearly, any of the sets $\mathcal{Q}$, $\mathcal{Q}^\lambda$ and $\mathcal{Q}^\rho$ is contained in their respective larger-dimensional counterparts. Thence, the same observations made before make it possible to also derive \emph{quantum} dimension witnesses \cite{}.

Whereas witnessing dimension for classical or quantum preparations is already of practical and fundamental interest, we ideally want to also distinguish between classical and strictly quantum behaviors. To that end, it is useful to recognize that a set of pair-wise commuting density operators can only generate classically reproducible statistics \cite{dallarno}. More precisely, if $\mathcal{S}_C$ is a set of $X$ $d$-dimensional states such that $\left[ \rho_i, \rho_j \right] = 0, \,\forall \rho_i, \rho_j \in \mathcal{S}_C$, then its behavior under any set of measurements can be mimicked with dits. \review{Not so sure about this justification for "classical states" and whether this is valid for any situation like with SR, without SR etc...}


As not all quantum states commute, it turns out that $\mathcal{C}_d \subset \mathcal{Q}_d$, and similarly for the sets allowing for shared randomness and entanglement-assistance. Collecting the aforestated set relationships, we find that 

$$
\mathcal{C}_d \subset \mathcal{Q}_d \subset \mathcal{Q}_d^\lambda \subset \mathcal{Q}_d^\rho ,
$$

$$
\mathcal{C}_d \subset \mathcal{C}_d^\lambda \subset \mathcal{Q}_d^\lambda \subset \mathcal{Q}_d^\rho,
$$

$$
\mathcal{C}_d \subset \mathcal{C}_d^\lambda \subset \mathcal{C}_d^\rho \subset \mathcal{Q}_d^\rho ,
$$




showing it is thus also possible to build nonclassicality witnesses for the prepare-and-measure scenario, c.f. \cite{varios}.



---




In recent years, a multitude of dimension and nonclassicality witnesses for prepare-and-measure scenarios have been proposed \cite{} and some of them experimentally tested \cite{}. More stringent conditions can also be used to perform self-testing of states and measurements, which can be used to certify the use of mutually unbiased bases, nonprojective measurements, and specific sets of states \cite{varios,email-jed}. The prepare-and-measure scenario and its sequential \cite{} and prepare-transform-and-measure \cite{} variations are also expected to serve as building blocks for quantum networks \cite{}. Complementing their versatility, they can also be seen as a physical implementation of many paradigmatic communication protocols such as random access coding and dense coding, which I now briefly introduce.





