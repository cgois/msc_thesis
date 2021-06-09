This subsection closely follows the exposition in \cite{rockafellar,grumbaum,ziegler,boyd}, where most of the alluded proofs can be found. Unless otherwise specified, all sets are subsets of $\mathbb{R}^d$.

Let $x_1 \neq x_2$ be two elements of some set.
$$
\alpha x_1 + (1 - \alpha) x_2, \quad\alpha \in \mathbb{R}
$$
is the \emph{line} passing through $x_1$ and $x_2$. A set $A$ containing all lines passing through its elements is an \emph{affine set}. The real line and the Cartesian plane are affine sets, but a sphere and a cube are not.

Finite induction shows that, for $x_1, \ldots, x_n \in A$ and $\sum_i \alpha_i = 1$, the point $x = \sum_i \alpha_i x_i \in A$.  Such a sum is an \emph{affine combination} of the $x_i$.

When $A_i$ are all affine sets, $A = \bigcap_i A_i$ is also affine. Intersections can only decrease cardinality. Hence, if we take some (not necessarily affine) set $S$ and intersect all $A_i \supseteq S$, we will get the smallest affine set containing $S$. This is called an \emph{affine hull}, and denoted $\aff{S}$. Equivalently, it can be shown that
$$
\aff{S} = \Big\{ \sum_i \alpha_i x_i \mid \sum_i \alpha_i = 1, \, x_i \in S \Big\} .
$$

The affine hull of two points in $\mathbb{R}^n$ is the line through them, and for three noncollinear points we get a plane.

Vector spaces and affine sets are close siblings: any vector space is an affine set, but the converse is not true, for the latter may not contain the $0$ vector. Furthermore, each affine set $A$ is parallel to a unique vector space $V$. Taking any $x_0 \in A$, we can translate $A - x_0 = V$. The \emph{dimension} of an affine space $A$ is the dimension of its parallel vector space $V$. In $\mathbb{R}^n$, dimensions $0, 1, 2$ and $n-1$ corresponds to points, lines, planes and hyperplanes.

Any hyperplane $H$ can be represented as the set
$$
H = \{ u \mid \braket{u}{b} = \beta \} ,
$$
where $b \in V$, $\beta \in \mathbb{R}$ are constants, and $\braket{\cdot}{\cdot}$ is an inner product on $V$. Switching from equality to $<, >, \leq$ or $\geq$, we get either open or closed \emph{halfspaces}. Halfspaces contain halflines, so they are not affine sets. Rather, they are convex sets.

Convex sets are somewhat similar to affine sets. But, instead of lines, a convex set $C$ must contain all \emph{line segments}
$$
\alpha x_1 + (1 - \alpha) x_2, \quad\alpha \in [0,1]
$$
passing through any $x_1, x_2 \in C$. Any affine set is trivially convex, but a sphere and a cube also are.

Convex combinations are affine combinations with the extra condition that the $\alpha_i \geq 0$. Likewise, it can be shown that a set $C$ is convex if and only if it contains all convex combinations of its elements. They are also closed under intersections, and the convex hull of a (not necessarily convex) set $S$ is the smallest convex set containing $S$,
$$
\conv{S} \equiv \bigcap \big\{ C \supseteq S \mid C \text{ is convex} \big\} .
$$
Equivalently, it is also the set of all convex combinations of $S$'s elements,
$$
\conv{S} = \Big\{ \sum_i \alpha_i x_i \mid \alpha_i \geq 0, \sum_i \alpha_i = 1, \, x_i \in S \Big\} .
$$

Convex sets can be further divided into extremal and nonextremal points. An $x \in C$ is an \emph{extreme point} of $C$ when it is not in the relative interior of any segment of $C$. Respectively, when $x = \alpha y + (1 - \alpha) z \,\Rightarrow\, x=y=z$ for any $y, z \in C$ and $\alpha \in (0, 1)$.

\emph{Polyhedra} are intersections of \emph{finitely} many closed halfspaces. Any polyhedron $L \subset \mathbb{R}^d$ can thus be written as
$$
L(A, b) = \big\{ x \in \mathbb{R}^d \mid Ax \leq b \big\} ,
$$
where $A \in \mathbb{R}^{d \times m}$ and $b \in \mathbb{R}^m$ specify a set of linear inequalities. A single halfspace, which is obviously unbounded, fits the definition. If a polyhedron $L$ is furthermore bounded (i.e., has no rays), it is a convex \emph{polytope}, denoted by $P$. They are also the convex hull of finitely many points. One way to test if $x \in L$ or $x \in P$ is to check whether it does not violate any of the inequalities defining the halfspaces. Polyhedrons and polytopes inherit their dimensions from their affine hull's.

As much as cubes have vertices, edges and faces, polytopes have $k$-faces. Any \emph{face} $F$ of a polytope $P$ is a set
$$
F = P \,\cap\, \{ x \in \mathbb{R}^d \mid c^\intercal x = b \} ,
$$
where $c \in \mathbb{R}^d$ is a column-vector, $b \in \mathbb{R}$, and any $x \in P$ is such that $c^\intercal x \leq b$. Visually, a face is any intersection of $P$ with a closed halfspace that touches $P$ but is not inside of it. The dimension $k$ of the affine hull of $F$ goes into the name $k$-face. Faces of dimension $0$ and $1$ are vertices and edges, while faces of dimension $\text{dim} (P) - 1$ are especially named \emph{facets}. For a cube ($\mathbb{R}^3$), the facets would be the common faces.

Our previous definitions of polyhedra and polytopes are sometimes termed $\mathcal{H}$-polyhedra and $\mathcal{H}$-polytopes. An alternative definition that will later become important is that of $\mathcal{V}$-polytopes, which are the convex hull of a \emph{finite} set of points. After the hull is performed, they become the extremal points of the convex set.

$\mathcal{H}$ and $\mathcal{V}$ representations are mathematically equivalent (theorem 1.1 in \cite{ziegler}) but, computationally, the choice of description may significantly matter. As will be made explicit in chaps. \ref{chap:pam} and \ref{chap:pam-classicality}, classicality in prepare-and-measure scenarios can be interpreted as the belonging of a behavior in a polytope. Conversely, nonclassicality may be witnessed through the violation of some inequality defining its facets. The $\mathcal{H}$-description of these polytopes is preferable for being much more economical and ergonomic. Much work in other correlation scenarios is also dedicated to finding all inequalities defining the facets of some polytope. In Bell scenarios, for instance, they are the celebrated Bell inequalities. However, no general methods to directly build them are known. On the other hand, it is conceptually easy to enumerate all extremal points of classicality polytopes (the \mathcal{V}-description). Casting one to the other can be done through specialized, user-friendly softwares such as PORTA, PANDA, lrs and cdd \cite{} but, unfortunately, this a computationally expensive problem that can only be done for the very simplest cases of interest.

The remainder of this chapter will be dedicated to defining linear and semidefinite programs. Linear programming happens over polyhedron-shaped feasible sets, so we are now equipped to tackle them.

# Refs
### Polyhedra
(Ziegler, H-polyhedron)
![[Pasted image 20210607145310.png]]

## Politopos
### Definitions
(Ziegler, def. V-polytope and H-polytope)
![[Pasted image 20210607144538.png]]
(Ziegler, polytope dimension)
![[Pasted image 20210607144710.png]]

### Equivalence of representations
(Ziegler, equiv. das representações H e V)
![[Pasted image 20210607145406.png]]