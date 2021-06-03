# Optimizing the probability of success

Up until now, we have focused on what can be inferred about $\rho$ from the observable statistics. In practice, $\rho$ is sometimes treated as a resource to be consumed in the protocol, and it may be of interest to obtain the preparations $\rho_x$ and measurement $\mathcal{M} = \{ E_b \}$ that make the best use of it to achieve the largest $\psuc$. More formally, we are interested in solving

\todo{otimização}

For an arbitrary $\rho$, this is a daunting task to approach analytically. Even numerically, the objective function is nonlinear, and optimizing over CPTP constraints is not directly a linear constraint. This lends little hope to the problem of efficiently finding global maxima. It is nevertheless possible to formulate an alternated semidefinite optimization procedure (also called a see-saw method) that solves to local extrema.

Using channel-state duality (sec. \ref{sec:states}), the CPTP map $\Lambda_x$ can be cast as a bipartite state, for which the constraints of positive semidefinitess and unit-trace are amenable in semidefinite programming. Eq.~\eqref{eq:psuc-base-program} is then equivalent to

\todo{otimizacao com channelstate}

From here on, it is just a matter of sampling an initial measurement $\mathcal{M}^0$, fixing it for the time being, and running

\todo{otimizacao sobre mapas}

where the $L_x \in \mathcal{L} (\hilb_A \otimes \hilb_B)$ correspond to the preparations $\Lambda_x$. 

With the optimal (w.r.t. $\mathcal{M}_0$) $L_x$ from this first iteration, which we call $L_x^1$, fixed, optimizing over the measurements is also a semidefinite program:

\todo{otiizacao sobre medicoes}

resulting in $\mathcal{M}^1$. Together, $\mathcal{M}^1$ and $L_x^1$ are the result of the first iteration, and provide a lower bound on the best $\psuc$. After $N$ iterations, convergence can be tested through some heuristic criterion, such as checking whether $\psuc \left( \mathcal{M}^N, L_x^N \right) - \psuc \left( \mathcal{M}^{N-1}, L_x^{N-1} \right) \approx 0$. Different samples of $\mathcal{M}_0$ can lead to distinct results. As this is a computationally inexpensive procedure, one can run it for several initial samples and take the best result. There will be no formal guarantee of achieving a global maximum, but trustable numerical evidence can be reached. And, of course, one might as well start by sampling a $L_x^0$ and inverting the order of the programs.

To see it in action, consider the Werner states (sec. \ref{sec:states}) parametrized as
$$
\rho_W ( \alpha ) = \frac{\id - \alpha S}{d^2 - \alpha d} ,
$$
where $d$ is the local dimension, $-1 \leq \alpha \leq 1$, and $S = \sum_{i,j=0}^{d-1} \ketbra{ij}{ji}$ is the swap operator. For $N = d^2$ preparations and a measurement with $N$ outcomes, we optimize the dense coding probability of success for $d \in \{2, \ldots, 5\}$ and a linear range over $\alpha$. Results are shown in fig. \ref{fig:werner-dense-coding-psuc}. All values of $\alpha \lesssim (d-1)/d$ saturate the classical (i.e., $s=1$) bound of $1/d$ from result \ref{res:1}, and every larger $\alpha$ violates it. In the inset, a comparison of $\psuc$ with the classical bound $1/d$, for $\alpha = 1$, suggests that Werner states of larger dimension provide smaller quantum advantages in dense coding.

\todo{insert fig}

