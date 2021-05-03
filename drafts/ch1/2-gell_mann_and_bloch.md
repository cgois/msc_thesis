# Gell-Mann operators and Bloch vectors

In sec. \ref{sec:density-operator} we argued that any quantum state is a linear, positive semi-definite, unit-trace $d$-dimensional density operator $\rho$, and that any such $\rho$ is a quantum state. Thus we define the set of density operators as
$$
\mathcal{D}(d) = \{ \rho \in \mathcal{L}(\mathcal{H}^d) \mid \text{tr}\rho=1, \rho \succeq0 \} ,
$$
where $\mathcal{L}(\mathcal{H}^d)$ is the set of linear operators in $\mathcal{H}^d$. This definition implies that $\rho^\dagger = \rho$ and $\text{tr}(\rho^2) \leq 1$, with equality only holding for pure states.

When describing a quantum state, it is often convenient to choose some basis for $\mathcal{H}^d$ and define $\rho$ through a vector. A widely used choice of basis in $\mathcal{H}^2$ are the Pauli matrices $\{\sigma_x, \sigma_y, \sigma_z\}$. They are Hermitian, traceless operators that, together with the identity, form a basis in which any $2 \times 2$ Hermitian matrix can be written. Letting $v = (v_x, v_y, v_z) \in \mathbb{R}^3$ and $\sigma = (\sigma_x, \sigma_y, \sigma_z)$, it's easy to see that
$$
\rho = \frac{\mathbf{1}_2}{2} + v \cdot \sigma
$$
is any unit-trace Hermitian operator. Restricting to $\rho \succeq 0$ further requires that $\lvert v \rvert \leq 1$. Thus, any element of the ball $\mathcal{B}(2) = \{ x \in \mathbb{R}^3 \mid \lvert x \vert \leq 1 \}$ is a $2$-dimensional quantum state and, conversely, any $2$-dimensional quantum state can be associated to a $3$-dimensional real vector $v$ with $\lvert v \rvert \leq 1$. Also importantly, $\lvert v \rvert = 1$ if and only if the state is pure, as can be verified by constraining $\text{tr}(\rho^2) = 1$. We'll call $\mathcal{B}(2)$ the *Bloch ball*, its surface the *Bloch sphere*, and any $v \in \mathcal{B}(2)$ a *Bloch vector* \cite{bloch-ball}. This geometric interpretation of qubit states will prove to be incredibly convenient.

Generalizing these concepts to $\mathcal{H}^d$ can be done in a similar fashion, but will lead us to an important caveat. Our starting point will be picking a basis. While there are a bunch of useful choices \cite{bertlmann}, the most adequate for our future endeavors will be the generalized Gell-Mann matrices. The (standard) Gell-Mann matrices naturally extend the Pauli matrices from $\text{SU}(2)$ to $\text{SU}(3)$, and they are likewise traceless and Hermitian. As these are the most important properties we will want to preserve in our applications, it is sensible to choose the standard $\text{SU}(d)$ generators when moving on to $\mathcal{H}^d$. Apart from the identity operator, we will need another $d^2 - 1$ operators to span $\mathcal{H}^d$. These generalized Gell-Mann matrices can be conveniently written as $\sigma = \{ \sigma^{(s)}_{jk}, \sigma^{(a)}_{jk}, \sigma^{(d)}_l \}$, where
$$
\sigma^{(s)}_{jk} = \lvert j \rangle \langle k \rvert + \lvert k \rangle \langle j \rvert, \quad 1 \leq j < k \leq d
$$
$$
\sigma^{(a)}_{jk} = -i\lvert j \rangle \langle k \rvert + i\lvert k \rangle \langle j \rvert, \quad 1 \leq j < k \leq d
$$

$$
\sigma^{(d)}_{l} = \sqrt{\frac{2}{l (l+1)}} \left( \sum_{j=1}^l \lvert j \rangle \langle j \rvert - l\lvert l + 1 \rangle \langle l + 1 \rvert \right), \quad 1 \leq l \leq d - 1
$$

Representing an element of $\mathcal{H}^d$ asks for $d^2$ coefficients. However, because we fix $\text{tr}(\rho) = 1$, there's a redundancy that will leave us with only $d^2 - 1$ free parameters. Preserving the previous notation we then propose that
$$
\rho = \frac{\mathbf{1}_d}{d} + v \cdot \sigma = \frac{\mathbf{1}_d}{d} + \sum_{i = 1}^{d^2 - 1} v_i \sigma_i ,
\label{eq:gell-mann-representation}
$$
where with the summation we made it explicit that now $v \in \mathbb{R}^{d^2 - 1}$, and by $\sigma_i$ we mean the elements of $\sigma$ defined above. This is, again, clearly a unit-trace and Hermitian operator. The condition $\text{tr}(\rho^2) \leq 1$ further imposes that $\lvert v \rvert \leq \sqrt{\frac{d - 1}{2d}}$. Our next step would be to characterize $\mathcal{B}(d)$ and consequently the (generalized) Bloch vectors. Unfortunately, finding a structure on $v$ that guarantees that $\rho \succeq 0$ is not as straightforward as in the $2$-dimensional case. Naively trying to associate any vector in a $d$-dimensional ball with a density operator won't take us far, as we'll soon find out that many choices lead to operators having negative eigenvalues. Albeit the complete characterization of Bloch vectors for arbitrary dimensions has been done \cite{kimura}, and in-depth investigations of the structure of $\mathcal{B}(3)$ and $\mathcal{B}(4)$ have been performed \cite{}, it does not lead to a natural parameterization such as in the $2$-dimensional case. Although we will keep calling any $\mathcal{B}(d)$ a Bloch "ball", it is important to keep in mind that are not balls at all, for there will in general be holes where there are no Bloch vectors.

Even being more complex than for qubits, this geometric interpretation is still fruitful. For one, its inverse map has quite an intuitive interpretation inside of quantum theory. We have so far been interested in defining which Bloch vectors lead to a density operator, but haven't mentioned the converse problem --- the one of determining $v$ from $\rho$ --- at all. The answer, which can be straightforwardly verified, is that $v_i = \text{tr}(\sigma_i \rho)$. Hence, each component of $v$ is the expectation value of an observable $\sigma_i$ that can, at least in principle, be experimentally obtained. Luckily, this is the mapping we will usually worry about.

Another useful consequence of this geometric description is that the effect of operations on a state can be interpreted visually. An specific example that will later become important is that of depolarizing channels. These channels are worst-case scenario noise models describing the situation where information on a state $\rho$ is, with some probability $p$, completely lost. Thus $\rho \mapsto (1 - p) \rho + p \frac{\mathbf{1}_d}{d}$, where $\mathbf{1}_d/d$ is the maximally mixed state (the "noise"). Letting $v_\rho$ be the Bloch vector associated to $\rho$, and observing that $v = 0$ defines the maximally mixed state, we are led to the conclusion that a depolarizing channel "shrinks" $\rho$'s Bloch vector towards the origin of the Bloch sphere.

Regarding measurements, our first observation is that not all measurement effects can be written as in eq. \ref{eq:gell-mann-representation}, because they are not required to have unit-trace. However, as any measurement effect is a positive-semidefinite operator, those of which do have unit-trace can also be described through Bloch vectors. As already pointed out, projective measurements are an important class of measurements where every effect is a projection. For any projection $\Pi$, it is true that $\text{tr}(\Pi) = \text{rank}(\Pi)$. Therefore, all rank-1 projective measurements can be described by a set of Bloch vectors, each associated to one of its effects. As all projections with larger rank can be simulated by rank-1 projections and coarse-graining, we conclude that all projective measurements can be interpreted through Bloch vectors together with post-processing. Because, by definition, $\Pi^2 = \Pi$, then $\text{tr}(\Pi^2) = \text{tr}(\Pi) = 1$, which means that a rank-1 projection operator's Bloch vector is actually on the Bloch sphere. Finally, as a measurement's effects must sum to the identity, a nice interpretation of projective measurements on qubits arises: given one of the effect's Bloch vector, the other must be its antipodal.

