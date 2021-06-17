Solving an arbitrary instance of eq.~\eqref{eq:optimization-problem} is a hard problem, and general methods only exist for special instances of optimization programs. Convex optimization (\texttt{conv}) --- which happens when all the $f_i$ are convex functions --- is one of the largest classes of programs that can be efficiently solved to global optimality. Even though $\texttt{LIN} \subset \texttt{SDP} \subset \texttt{CONE} \subset \texttt{CONV}$, specialized algorithms for subsets of convex optimization, such as conic (\texttt{cone}), semidefinite (\texttt{sdp}) and linear (\texttt{lin}) programming, renders even larger instances of those pratical. Although we will not discuss them, the main reference for convex programming is the textbook \cite{boyd_vanderberghe}, and a good reference for cone programming, tuned to quantum information, is \cite{uola}. All of these are important tools in quantum information.

Because of their use in the industry, ready-to-use solvers for optimization problems are broadly accessible. I will mention them in due time, but algorithms will not be discussed (see, e.g., \cite{papadimitriou,gartner} for linear programming, \cite{vanderberghepaper,gartnersdp} for SDPs and \cite{boyd} for convex optimization).

## Linear programming
Linear programming happens when all $f_i$ are linear functions. Recalling eq.~\eqref{eq:optimization-program}, you will se that the feasible region $\mathcal{F}$ is thence an intersection of halfspaces --- a polyhedron. Apart from being widely used in the industry to optimize supply chains, workforce allocation and delivery routes, it is also useful to search for probability distributions satifying a set of constraints. The significance of this problem will become clearer in chap. \ref{chap:pam-classical}.

Being linear, the objective function $f_0 : \mathbb{R}^n \mapsto \mathbb{R}$ can conveniently be written as $c^\intercal x$, where $c = (c_1, \ldots, c_n)$ is a constant vector in $\mathbb{R}^n$ defining the quantity to be maximized. Minimizing $c^\intercal x$ is the same as maximizing $-c^\intercal x$, so the discussion holds both ways. For an \emph{unconstrained} problem, that is all --- in this case, unless $f_0$ is constant, the program would end up being \emph{unbounded}, though. Things get more interesting when $x$ is constrained to be in a subset $\mathcal{F} \subset \mathbb{R}^n$. We can do that by saying $0 \leq x_i \leq 1, \,\forall i$, for instance, and then we would be optimizing $c^\intercal x$ over some hypercube. More generally, we allow the constraints to be of the form $a_i^\intercal x \leq b_i$, where $a_i \in \mathbb{R}^n$ and $b_i \in \mathbb{R}$. There is no need to consider equality conditions separately, as we can just use two inequalities with inverted directions. So we do not have to write all constraints separately, a shorthand notation is to build an $m \times n$ matrix $A = [a_1 \; \ldots \; a_m]^\intercal$ and a vector $b = [b_1 \; \ldots \; b_m]^\intercal$ of bounds so that

\todo{LP general}

becomes a general linear program. When $\mathcal{F} = \emptyset$, the program is \emph{unfeasible}, meaning there are no vector $x$ that satisfies the constraints. Requiring that $x_i \geq 1$ and $x_i \leq -1$ would certainly put you in that situation. If $\mathcal{F}$ is not empty, then the program may either have a solution, called $p^*$ and happening at $x^*$, or be unbounded. To understand why the latter may be the case, notice that $\mathcal{F}$ is a polyhedron. As such, it may itself be unbounded. Consider, for instance, $x \in \mathbb{R}^2$ with $\mathcal{F} = \{ 0 \leq x_1 \leq 1, x_2 \geq 0 \}$. If $c = [c_1 \; c_2]$, with $c_2 > 0$, the optimal value $p^*$ would go to infinity. On the other hand, $c_2 \leq 0$ would be alright. When $\mathcal{F}$ is a (nonempty) polytope, there is always some solution to the program. A solution is either unique (only a single $x^*$ leads to $p^*$) or there infinitely many solutions yielding the same $p^*$. To understand why this is so, consider the \emph{fundamental theorem of linear programming}, which states that every feasible, bounded linear program has an optimal solution on a vertex of $\mathcal{F}$. If optimal solutions happen at two different vertices, then any $x$ in the line segment between them results in $p^*$. 

Linear programs are efficiently solvable in practice. The simplex method, proposed by George Dantzig in 1947 \cite{}, builds upon the fact that optimal solutions occur in vertices. Starting from any basic feasible solution (a corner of $\mathcal{F}$), it smartly hops to neighboring vertices along edges that increase $f_0$. If you end up at a basic feasible solution connected with no edges that increase the objective value, or if you visit an unbounded edge, you are done. A rigorous presentation and complexity analysis of it can be found in \cite{papadimitriou}. Interestingly, the simplex method is \emph{not} of polynomial time complexity. Rather, there are families of linear programs for which it performs poorly. Nevertheless, it is a reliable and efficient method in practice, and is widely used (in several variations) up to this day. There are provably polynomial time algorithms in theory, of which the ellipsoid algorithm, published in 1980, was the first \cite{}. Even so, it is not efficient in practice. The more recent interior-point methods are provably polynomial in theory, and fast in practice \cite{}.

Due to its wide applicability in the industry, there are many open source and proprietary linear programming solvers available, such as GLPK \cite{}, Gurobi \cite{}, CPLEX \cite{} and Mosek \cite{}. Most provide user-friendly interfaces to widely used programming languages, such as C, C++, Python and MATLAB. To further aid in using them, there are also modeling languages that can be used to specify programs in a high-level format, and that internally converts and dispatches the problem to specific solvers. YALMIP \cite{} and CVX \cite{} are widely used inside MATLAB, while PICOS \cite{} and CVXPY \cite{} are common choices when working in Python.


## Semidefinite programming
Semidefinite programming is the optimization of a linear function subject to a linear matrix inequality. Largely generalizing linear programming, it has found numerous applications in statistics, economics, control theory, pattern recognition and machine learning, to mention a few (see sec. 2 of \cite{vanderberghe_boyd_1996} and chap. 1 of \cite{boydbook} for a survey). It is also widely used as a tool in approximation algorithms to graph theoretical problems \cite{gartner}, and polynomial and non-commutative polynomial optimization \cite{lasserre,navascues}; the latter being extensively used in quantum information.

Before we define them, recall that
$$
S^n = \{ X \in \mathbb{R}^{n \times n} \mid X = X^\intercal \}
$$
is the set of symmetric matrices, and
$$
S_+^n = \{ X \in S^n \mid X \succeq 0 \}
$$
the one of positive semidefinite matrices. All eigenvalues of a symmetric ($X = X^\intercal$) matrix are real, and the positive semidefiniteness condition ($X \succeq 0$) further requires they must be nonnegative.

Building upon the general linear program~\eqref{eq:linear-program}, we write a semidefinite program (SDP) as

\todo{maxaimize c^Tx s.t. F(x) \succeq 0} .

Here, $F(x) \equiv F_0 + \sum_{i=1}^n x_i F_i$ is what we call a \emph{linear matrix inequality}. The $n + 1$ matrices $F_0, \ldots, F_m$ are in $S^m$, and we maintain $x \in \mathbb{R}^n$. A semidefinite program is thus the optimization of a linear function $c^\intercal x$ under the constraint that $F(x)$ is positive semidefinite.

This may seem like a rather arbitrary definition. To debunk this impression, first notice that if $F(x) \succeq 0$ and $F(x) \succeq 0$, then
$$
F[ \alpha x + (1 - \alpha) y ] = \alpha F(x) + (1- \alpha) F(y) \succeq 0
$$
for all $0 \leq \alpha \leq 1$. Thus, both the objective function and the constraint are convex, and semidefinite programming is a special case of convex optimization. More than that, $S_+^n$ is a convex cone, meaning it is also a special case of conic optimization. Now it seems too specialized, so we further notice that, if we let $F_0 = \text{diag}(b)$ and $F_i = \text{diag}(a_i)$, we recover linear program~\eqref{eq:linear-program}. Hence, $\texttt{LIN} \subset \texttt{SDP} \subset \texttt{CONE} \subset \texttt{CONV}$.

A general $F(x)$ may have a block-diagonal section of the form $\text{diag}(Ax + b)$, and a more general structure in the remainder. Thus, a linear matrix inequality represents an affine section of $S_+^n$, also called an \emph{spectrahedron}. Unlike polyhedra, they may have curved boundaries. A cylinder, for instance, can be parametrized as an $F(x)$ with $4 \times 4$ matrices \cite{https://www.ams.org/notices/201405/rnoti-p492.pdf}. A last, interesting link to linear programming is that $F(x) \succeq 0$ if and only if $z^\intercal F(x) z \geq 0$ for all $z \in \mathbb{R}^m$. These are infinitely many linear constraints on $x$.

SDPs can also be efficiently solved both in theory and in practice. Interior-point methods are usually robust and efficient, and are implemented in some user-friendly solvers such as SDPA \cite{}, SDPT3 \cite{} and Mosek \cite{}.

The usefulness of semidefinite programming in quantum information is hinted by the fact that quantum states and measurement effects are positive semidefinite matrices. As long as the objective function is linear, we can optimize over them, and they have proven to be useful in quantum state discrimination, quantum steering and hierarchies for nonlocal correlations, among other applications. One of them will be shown in chap. \ref{chap:pam-dense-coding}.

A drawback in dealing with density operators of measurement effects is that, while semidefinite programming is, as in here, usually discussed over the real field, quantum objects make use of complex numbers. One can nevertheless embed them in real variables. This can be a cumbersome task to do manually but, luckily, the modeling interfaces mentioned in the last section can do this under the hood before calling the solver.

### Incompatibility robustness
\todo{}


# Refs
(History of optimization @ Encyclopedia of optimization)
![[Pasted image 20210608122201.png]]

https://www.gurobi.com/resource/linear-programming-basics/

https://www.cs.cmu.edu/~15451-f17/lectures/lec18-lp2.pdf

https://stanford.edu/class/ee363/sessions/s4notes.pdf

https://www.ams.org/notices/201405/rnoti-p492.pdf

https://www.newton.ac.uk/files/seminar/20130718093010001-153683.pdf

http://www.math.uni-konstanz.de/~plaumann/LMI13/lmi.pdf

http://plato.asu.edu/ftp/sparse_sdp.html

file:///home/cgois/Downloads/Encyclopedia%20of%20Optimization%20by%20C.A.Floudas,%20P.M.Pardalos%20(Eds.)%20(z-lib.org).pdf