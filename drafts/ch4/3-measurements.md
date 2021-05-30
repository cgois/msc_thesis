# Classicality of measurements
In the absence of entanglement, one must look for other quantum features to explain nonclassical behaviors. Measurement incompatibility (sec. \ref{sec:measurements}) is usually at the center of many interesting quantum phenomena, and from a more practical perspective they may be seen as resources for informational tasks \cite{}. It is then natural to wonder whether non-joint measurability is necessary, or even sufficient, for the arisal of classically irreproducible behaviors in the prepare-and-measure scenario. Reframing the question, we ask: given a set of incompatible measurements, is there \emph{always} some set of preparations that leads to nonclassicality?

The question at hand has been answered for quantum steering \cite{} and Bell nonlocality \cite{}, but only partial results exist for prepare-and-measure scenarios \cite{teiko}. Interestingly, this problem is similar to what we have just dealt with, but while we were previously interested in certifying some set of preparations is classical for all measurements, we now move on to certify there exists no set of \emph{preparations} such that a fixed set of measurements unveils nonclassicality. We will soon see the previous method is straightforwardly adaptable. Even so, regarding the existing literature, this is a more innovative approach. As pointed out, sec. \ref{sec:preparation-classicality} develops a procedure akin to known results for different correlation scenarios \cite{rabelo,hirsch} but, to the best of my knowledge, the method we now present has not been considered elsewhere.

Starting with a measurement set $\mathcal{M} = \{ E_{b \mid y} \}_{b,y}$ of our interest, we build the operators
$$
O_{b \mid y} = \eta E_{b \mid y} + (1 - \eta)\frac{\tr{E_{b \mid y}}}{d} \id .
\label{eq:polarized-measurements}
$$
$\eta$ will soon be defined.

For some set $\mathcal{S} = \{ \rho_x \}_x$ of \emph{pure} preparations, we consider the behavior $\mathbf{p} = \{ \tr{O_{b \mid y} \rho_x } \}$. If, for all $b$, $x$ and $y$, classicality (in the sense of eq.~\eqref{eq:pam-classical-sr}) holds, then it also does for every preparation in $\conv{\mathcal{S}}$. In particular, this will be true for all quantum states in the largest sphere inscribed in the convex hull of $\mathcal{S}$. We write $\eta$ for its radius, and $\rho_x^\eta$ for any preparation in it. A key difference from sec. \ref{sec:preparation-classicality} is that the $\eta$ defining the $O_{b \mid y}$ is now the radius with respect to $\conv{\mathcal{S}}$, as opposed to $\conv{\mathcal{M}}$.

A similar trace equality, $\tr{ O_{b \mid y} \rho_x^\eta} = \tr{E_{b \mid y} \rho_x}$, holds whenever the $E_{b \mid y}$ are rank-1 projectors, as can be seen by direct calculation.

Our working hypothesis is that
$$
\tr{ O_{b \mid y} \rho_x} = \int_{\Lambda} \sum_{m = 1}^{d} \pi(\lambda) \condprob{m}{x,\lambda} \condprob{b}{m,y,\lambda} d\lambda \quad\forall b,x,y .
$$
From the discussion in the previous section, this would imply the collection of $\tr{ O_{b \mid y} \rho_x^\eta}$ is also classical for \emph{every} preparation in the $\eta$-sphere. The right hand side of the trace equality then tells the measurements in $\mathcal{M}$ leads to classicality for every possible $\rho_x$. Recalling we started with pure preparations, this procedure reveals that a set of rank-1 projective measurements is classical in regard to all pure states. Pure states are the extremal points in the set of quantum states, thence, any state is a convex combination of those. This shows the result is valid for all states. Moreover, coarse graining of rank-1 projective measurements simulates PVMs with all larger ranks, proving our procedure works for all projective measurements.

A slight modification of program~\eqref{eq:preparation-classicality-program} implements this criterion as the linear program

\todo{Measurements classicality program}

Running it amounts to choosing a suitable set of pure probes $\mathcal{S} = \{ \rho_x \}_x$, finding its corresponding $\eta$, generating the deterministic strategies $\{ \lambda \}$, and querying for the maximum $\alpha$ such that the projective measurements in $\mathcal{M}$ are classical. As before, $\alpha = 1$ certifies they are classical, while $\alpha < 1$ tells us only that the measurements $\mathcal{M}_\alpha = \{ \Phi_\alpha \left( E_{b \mid y} \right) \}_{b,y}$ are. From self-duality of the depolarizing map $\Phi$, another valid interpretation is that $\mathcal{M}$ is classical for all preparations at least as mixed as $\Phi_\alpha \left( \rho_x \right)$.

Once more in full analogy to the preparation classicality case, we may use concepts of projective simulatability to extend this criterion to POVMs. Letting $t$ be a depolarization parameter that turns a POVM set $\mathcal{M}$ projective-simulatable, and recalling that $\trb{ \phi_t( E_{b \mid y}) \rho^t } = \trb{ E_{b \mid y} \phi_t(\rho) }$, we conclude that testing $\mathcal{M}$ for classicality is equivalent to certifying $\Phi_t \left( \mathcal{M} \right)$ is classical with respect to a set
$$
\mathcal{S}^t = \{ \rho_x^t \}_x = \Bigg\{ \frac{1}{t} \left[ \rho_x - \frac{1-t}{d} \mathbf{1} \right] \Bigg\}_x
$$
of probe preparations. Starting from a set $\mathcal{S}$ of pure probes, program~\eqref{eq:measurement-classicality} can be undemandingly modified to implement this criterion.

To demonstrate the usefulness of our method, we solve an important question on the relation between measurement incompatibility and classicality in the PM scenario.


## Measurement incompatibility is insufficient for nonclassicality in the prepare-and-measure scenario

Non-joint measurability is an important concept of measurement incompatibility with a clear operational interpretation (sec. \ref{sec:measurements}). Withal, incompatibility robustness is an useful measure of the extent to which a set of measurements is non-jointly measurable, and it can be efficiently computed through semidefinite programming (sec. \ref{sec:incompatibility-robustness}). Employing our measurement classicality certification procedure, we now prove measurement incompatibility is insufficient for nonclassicality in prepare-and-measure scenarios.

Define the $Y=3$ parametrized mirror-symmetric projective measurements defined as in fig. \ref{fig:mirror-symmetric-measurements}. For each value of $\theta$, their incompatibility robustness is given by
$$
\begin{equation}
		\chi^*_\mathcal{M} = \sup_{\substack{\chi \,\in\, [0, 1]\\ \{ N_{b \mid y}\} \,\in\, \textbf{N}( \mathcal{M} )}} \Big\{ \chi \mid \chi \{ E_{b \mid y} \} + (1 - \chi) \{ N_{b \mid y} \} \in \textbf{JM} \Big\} ,
\end{equation}
$$
where $\mathbf{N}(\mathcal{M})$ is a choice of noise model, generally dependant on the desired application. Unbiased (or white) noise $N_{b|y} = \mathbf{1}/\abs{\mathcal{B}}$ is a common choice when one wants to model experimental imperfections that affect all degrees of freedom undiscriminately. Under white noise, the lower curve in fig. \ref{fig:incompatibility-vs-classicality} stands for $\chi^*_{\mathcal{M}(\theta)}$, and it is a tight upper bound up to numerical precision. Consequently, any value of $\chi$ above it defines a non-jointly measurable measurement set.

\todo{fig}

Program~\eqref{eq:measurement-classicality} was used to generate the upper curve in the same figure. The probe preparations were disposed as the vertices of a rhombicuboctahedron, leading to $\eta \approx 0.86$, and the deterministic strategies were iteratively explored following the algorithm described in appendix \ref{ap:computational-details}. For each $\theta$, the obtained $\alpha$ is a lower bound on the visibility of $\mathcal{M}$ such that a classical model exists for all preparations. In other words, anything below the classicality curve defines a measurement set which cannot generate nonclassical behaviors. A non-empty region between these two curves certifies there are plenty of incompatible measurements which are classical. Accordingly, non-joint measurability is insufficient for nonclassicality in the prepare-and-measure scenario.


