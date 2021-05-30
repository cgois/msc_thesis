# Classicality of preparations
But we are interested in a much more general question than that of certifying whether or not a \emph{behavior} is classical. Namely, that of certifying if the set $\mathcal{S}$ of quantum preparations is \emph{always} classically reproducible. Brute-forcing our way into the answer is off the table, for this would amount to testing the behaviors of $\mathcal{S}$ for \emph{all} (i.e., infinitely many) possible measurements.

This problem is similar to that of finding local hidden variable models for entangled states in Bell scenarios \cite{lhv,better-lhv}, for which a method guarateeing sufficient conditions has recently been proposed \cite{metodos-lhs}. We now adapt it to the prepare-and-measure scenario.

Suppose that, for a finite set $\mathcal{M} = \{ E_{b \mid y} \}_{b,y}$ of $Y$ measurements, the classical model~\eqref{eq:pam-classical-sr} exists, i.e., that
$$
\tr{\rho_x E_{b\mid y}} = \int_{\Lambda} \sum_{m = 1}^{d} \pi(\lambda) \condprob{m}{x,\lambda} \condprob{b}{m,y,\lambda} d\lambda \quad\forall b,x,y .
\label{eq:preparation-classicality-model}
$$
For any convex sum of effects,
$$
\trb{\rho_x \left( w E_{b\mid y} + (1-w) E_{b^\prime \mid y^\prime} \right)} = w\tr{\rho_x E_{b\mid y}} + (1-w) \tr{\rho_x E_{b^\prime \mid y^\prime}},
$$
classicality will also hold. Then, $\mathcal{S}$'s behaviors are classical under all measurements in $\conv{\mathcal{M}}$, and in particular for all measurements whose effects are inside the largest ball we can inscribe in $\conv{\mathcal{M}}$ (fig. \ref{fig:measurements-hull-2d}). Letting $0 \leq \eta \leq 1$ be its radius, \todo{Modify this to explain max eta is only one if we normalize the gell-mann representation} this ball is nothing but a depolarized Bloch ball $\eta \, \blochballd{d}$. This suggests that by probing the preparations with but a finite number of measurements and (possibly) finding a classical model, we can nevertheless certify classicality for the infinite amount of measurements whose effects are in $\eta \, \blochballd{d}$. They can be written as
$$
\Phi_\eta(E_{b \mid y}) = \eta E_{b \mid y} + (1 - \eta) \frac{ \tr{E_{b \mid y}} }{d} \id \equiv E_{b \mid y}^\eta,
$$
but they are still not all possible measurements. As an example, unless $\eta = 1$, many rank-1 projective measurements (those on the sphere, as discussed in sec. \ref{sec:gell-mann}) will be left out.

The work-around is to consider the dual map $\Phi_\eta^\dagger$ applied to the preparations. This will result in each
$$
\rho_x \mapsto \Phi_\eta^\dagger(\rho_x) = \frac{1}{\eta} \left[ \rho_x - (1 - \eta) \frac{\id}{d} \right] \equiv O_x .
$$
Analyzing the behavior of the $O_x$ under the $E_{b \mid y}^\eta$ tells us that
$$
\tr{O_x E_{b \mid y}^\eta} = \text{tr}\left\{ \frac{1}{\eta} \left[ \rho_x - (1 - \eta) \frac{\mathbf{1}}{d} \right]  \left[ \eta E_{b \mid y} + (1 - \eta) \frac{ \tr{E_{b \mid y}} }{d} \id \right] \right\}
$$
$$
= \tr{\rho_x E_{b \mid y}} - \frac{1 - \eta}{d} \tr{ E_{b \mid y}} + \frac{ 1 - \eta }{ d \eta } - \frac{ (1 - \eta)^2 }{ d \eta } .
$$
If all effects $E_{b \mid y}$ are rank-1 projectors, then $\tr{E_{b \mid y}} = 1$ (sec. \ref{sec:gell-mann}), making it true that  $\tr{O_x E_{b \mid y}^\eta} = \tr{\rho_x E_{b \mid y}}$. From now on, let's call these rank-1 projections $\Pi_{b \mid y}$ to avoid misunderstandings.

The procedure to test $\mathcal{S}$ for classicality follows from precisely this trace equality relation. We start out by defining an operator $O_x$ for each state $\rho_x \in \mathcal{S}$. The second step is probing the $O_x$ with some set $\mathcal{M} = \{ \Pi_{b \mid y} \}_{b,y}$ of rank-1 projective measurements. If model~\\eqref{eq:pam-classical-sr} exists for $\mathcal{S}$ and $\mathcal{M}$, from the preceding discussion it also exists for all measurements in $\conv{\mathcal{M}}$. It will then be true that $\mathbf{p} = \Big\{ \tr{O_x \Pi_{b \mid y}^\eta} \Big\}_{b,x,y}$ is a classical behavior for \emph{all} projections that can be written as $\Pi_{b \mid y}^\eta$. In turn, $\tr{O_x \Pi_{b \mid y}^\eta} = \tr{\rho_x \Pi_{b \mid y}}$ implies that the $\rho_x$ admit a classical model for all $\Pi_{b \mid y}$, which are all rank-1 projections. Measurement results for projections of larger rank can be inferred from rank-1 projections through coarse graining (classical post-processing), hence the result is valid for all projective measurements.

To cast this procedure as an optimization problem, recall that the deterministic strategies $\lambda$ can be enumerated as discussed in the previous section. That being done, the integral in~\eqref{eq:preparation-classicality-model} turns into a finite sum. Further observing that the maximally mixed state $\id/d$ is trivially classical, we write

\todo{Maximization program}

where a result of $\alpha = 1$ certifies a sufficient condition to preparations in $\mathcal{S}$ admiting a classical model for all projective measurements, and any $\alpha < 1$ certifying the preparations $\mathcal{S} = \{ \alpha \rho_x \}_x$ are classical. This criterion turns necessary and sufficient only when $\eta \rightarrow 1$, which is only approchable by increasing $Y$.

Being a linear program (sec. \ref{sec:linear-programming}), it can be efficiently solved up to numerical precision. Regardless of linear programming complexity, an instance of program~\eqref{eq:preparation-optimization} has $N_\lambda$ variables. As already noted, $N_\lambda \propto (B-1)^{dY}$ thus the program size scales exponentially with the number of measurements. It will always be of interest to maximize $\eta$, and consequently, to maximize $Y$. With $X=4$ preparations, a common desktop computer can usually only handle less than $Y = 12$ projective qubit measurements. This limitation can be circumvented through the iterative optimization procedure described in sec. \ref{ap:pam-classical-computational}, which was used for all upcoming results.

Extending our criterion to non-projective measurements is possible projective simulatability of POVMs (c.f. sec. \ref{sec:measurements}). For $B=2$ outcomes, projective measurements are the extremal POVMs, hence no modification is needed. To adapt the procedure to more outcomes, recall that any set of generalized measurements $\mathcal{M} = \{ E_{b \mid y \}_{b,y}_$ becomes projective-simulatable after a certain amount $t$ of depolarization. Noticing that
$$
\trb{\Phi_t(E_{b \mid y}) \rho} = \trb{E_{b \mid y} \Phi_t(\rho)}
$$
leads us to conclude that testing $\mathcal{S} = \{ \rho_x \}_x$ for classicality under all POVMs is the same as certifying that preparations
$$
\rho^\prime_x = \frac{1}{t} \left( \rho_x - \frac{1-t}{d} \id \right)
$$
are classical for all projective measurements, where $t$ is some amount of depolarization such that $\Phi_t(\mathcal{M})$ are projective. Program~\eqref{eq:preparation-classicality} can be easily modified to this case.

\todo{Colocar progrma modificado pra esse caso?}

## Applications
Nonclassicality activation phenomena have been long-known in Bell scenarios, where an entangled state that only behaves locally may have its nonlocality activated, for instance, by local filtering or by exploring multiple copies of the state \cite{}. Very recently, two interesting, similar phenomena were proposed in PM scenarios \cite{} --- one related to increasing the number of allowed measurements, and the other to the number of preparations. Our method can be applied to demonstrate a stronger form of the latter.

### Nonclassicality activation
Let us start by defining $\mathcal{S}(\alpha, \theta) = \{ \rho_{\bm{r_1}}, \rho_{\bm{r_2}}, \rho_{\bm{r_3}}, \rho_{\bm{r_4}} \}$ as the preparation set illustrated in fig. \ref{fig:preparation-set-activation}. They are parametrized by $\alpha$ --- a shrinking factor from the surface of the Bloch sphere ---, and the angle $theta$. For the probe measurements, we will choose the ones parametrized by the Bloch vectors $\bm{q}_1 = - \bm{x}$ and  $\bm{q}_2 = \bm{z}$. Substituting back into inequality $S$ (eq.~\eqref{eq:inequality-s}), we get that $S(\alpha, \theta) = 4\sqrt{2} \alpha \sin \theta \leq 4$. This curve is shown in fig. \ref{fig:nonclassicality-activation}, where any violation of $S=4$ certifies nonclassicality.

Our second step is to take every subset of $3$ preparations from $\mathcal{S}(\alpha, \theta)$ at some $\theta$. For each possibility, we run program~\eqref{eq:preparations-program} and find the largest $\alpha^*$ such that \emph{any} collection of $3$ preparations is classical. Any $\alpha < \alpha^*$ preserves classicality. Running over $\theta$, we obtain the dotted curve shown in fig. \ref{fig:nonclassicality-activation}. The shaded region then corresponds to a situation where all triads of preparations are classical, but taken together they have their nonclassicality activated.

\todo{fig}


### Quantum advantage in random access coding
To illustrate the significance of this result, consider a $\rac{2}{2}{1}$ RAC. Section \ref{sec:racs}) tells us it can me mapped to a $(d,B,X,Y) = (2,2,4,2)$ prepare-and-measure instance, which is exactly the case for inequality $S$. Borrowing from \cite{marcin}, we note that, for this RAC, $p_{\text{avg}}$ \emph{is} the facet $S$. To see that, let's relabel preparations $\left( 1, 2, 3, 4 \right) \mapsto \left(00, 01, 10, 11\right)$ and open up
```
\begin{align*}
            p_{\text{suc}}^{\text{avg}} &= \frac{1}{8} \sum_{\bm{x}, y} p(b = x_y \vert x_0 x_1, y) \\ &= \frac{1}{8} \big[ p(0 \vert 00, 0) + p(0 \vert 00, 1) + p(0 \vert 01, 0) + p(1 \vert 01, 1) + p(1 \vert 10, 0) + p(0 \vert 10, 1) + p(1 \vert 11, 0) + p(1 \vert 11, 1) \big] \\ &= \frac{1}{8} \big[ p(0 \vert 00, 0) + p(0 \vert 00, 1) + p(0 \vert 01, 0) - p(0 \vert 01, 1) - p(0 \vert 10, 0) + p(0 \vert 10, 1) - p(0 \vert 11, 0) - p(0 \vert 11, 1) + 4 \big]
\end{align*}
```
Switching $S$ to full-form and applying normalization, we get
```
\begin{align*}
            S = 2 \left[ p(0 \vert 00, 0) + p(0 \vert 00, 1) + p(0 \vert 01, 0) - p(0 \vert 01, 1) - p(0 \vert 10, 0) + p(0 \vert 10, 1) - p(0 \vert 11, 0) - p(0 \vert 11, 1) \right] ,
\end{align*}
```
and together,
$$
p_{\text{avg}} = \frac{1}{8} \left( \frac{1}{2} S + 4 \right) = \frac{S + 8}{16} \leq \frac{3}{4} ,
\label{eq:s-vs-pavg}
$$
where the classical bound for $S$ was substituted in the last term. This relation means that any violation of $S$ in the $(2,2,4,2)$ PM scenario can be associated with a quantum advantage in the corresponding $\rac{2}{2}{1}$ QRAC. More than that, we have numerically found a lower bound for the maximum quantum violation of $S$ to be $\approx 5.65685$. Substituting into eq.~\eqref{eq:s-vs-pavg}, $p_{\text{avg}} \approx 0.853553$, exactly matching the result found in sec. 3.3.1. of \cite{ambainis}. This also suggests that our bound for $S$ is tight.

Yet more interestingly, this construction shows that the nonclassicality activation phenomenon reported above also transfers to this case, where it can be interpreted as an activation of quantum advantage in a relevant quantum communication protocol. 

