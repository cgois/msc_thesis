Catenaries, Fermat's principle of least time and thermodynamic equilibrium are well known examples of extremum principles applied to the description of nature. On the opposite side, multiple essential modern technologies, such as network routing, logistics and integrated circuit design rely on finding good solutions to optimization problems. No matter whether you are minimizing a Gibbs free energy under constant $T$ and $P$, or searching for the best arrangement of electronic components on a chip to reduce its footprint while satisfying heat dissipation and fabrication constraints, this is what an optimization problem looks like
$$
	p^* = \max \big\{ f_0(x) \mid f_i(x) \leq b_i, \,\forall i \in \{1, \ldots, m\} \big\} .
$$
Solving it means finding some $x^* \in \mathbb{R}^n$ such that the value of the \emph{objective function} $f_0(x^*) \leq f_0(x), \,\forall x \in \mathcal{F}$, where
$$
\mathcal{F} = \big\{ x \mid f_i(x) \leq b_i , \,\forall i \in \{1, \ldots, m\} \big\}
$$
is the \emph{feasible set}. The objective function represents the quantity to be minimized (the free energy; the footprint), while $\mathcal{F}$ imposes the constraints (constant temperature and pressure; rate of heat dissipation and limitations of the fabrication procedure).

Finding global optima for nonlinear programs is difficult, and no general methods to do so are known. That is why one usually consider subsets of eq.~\ref{eq:optimization-program} where some special stucture is imposed on the $f_i$. Our objective for this chapter is to learn how to recognize the special structures of linear and semidefinite programs, which requires some groundwork on convexity. Furthermore, polytopes --- a special type of convex sets ---, are ubiquitous in the geometry of correlation scenarios, and will make an appearance in later chapters. This will be our starting point.