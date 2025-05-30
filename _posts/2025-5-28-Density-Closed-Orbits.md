---
layout: post
title: Effective density of closed orbits for SFTs
tag:  dynamics
categories: ["Dynamics"]
---

In this post, we discuss the density of closed orbits of a prescribed length for an SFT and a suspension flow over an SFT.

# Main motivation

Let $\sigma : X_A \rightarrow X_A$ be an SFT (see the next section for the precise definition). It is well-known that the collection of periodic points $P$ for $\sigma$ is dense in the space. In this post, we are interested in quantifying that rate of density. For a compact metric space $(X,d)$, we will say that a subset $U \subseteq X$ is *$\eta$-dense* if for each $x \in X$, we have $d(x, U) \leq \eta$ (in other words, the set $U$ approximates all of $X$ at scale $\eta$). The goal is to show that there are constants $C, \delta > 0$ such that if we look at the collection of periodic points with period at most $n$, then it is $\eta$-dense in the entire space, where $\eta \leq C e^{-n\delta}$. Thus, not only is $P$ dense, but it becomes exponentially dense as we look at more and more closed orbits. I'll refer to this as the *effective density of closed orbits*. Furthermore, we will also show that the same holds true for suspension flows.
# Preliminaries

## Perron-Frobenius theorem

We briefly recall the famous *Perron-Frobenius theorem*.

**Theorem:** If $A$ is a $k \times k$ real-matrix with entries $A(i,j) > 0$, then
1. there is a unique $1$-dimensional eigenspace $E$ such that $E \cap \{(x_1, \ldots, x_n) \in \mathbb{R}^n : x_i > 0\} \neq \varnothing$, and
2. the corresponding eigenvalue $\lambda_E$ is positive and satisfies the condition that $\vert \lambda_E \vert > \vert \lambda \vert$ for all other eigenvalues $\lambda$.

There is a nice proof by [Kohlberg and Pratt](https://pubsonline.informs.org/doi/10.1287/moor.7.2.198) which we sketch without details below. First, we recall the *contracting mapping principle*. 

**Theorem:** Let $0 < C < 1$ and let $f : X \rightarrow X$ be a mapping of a compact metric space such that $d(f(x), f(y)) \leq C d(x,y)$ for all $x,y \in X$. There exists a unique $x \in X$ such that $f(x) = x$.

**Remark:** If a map $f$ satisfies the assumption of this theorem, then we call it a *contracting map*.

The aim is to construct this eigenspace using the contracting mapping principle. To that end, let 

$$ \Delta_1^+ := \left\{(x_1, \ldots, x_n) \in \mathbb{R}^n \mid \sum_{i=1}^n x_i = 1 \text{ and }  x_i \geq 0\right\},$$

and

$$ B := \{ (x_1, \ldots, x_n) \in \mathbb{R}^n \mid x_i \geq 0 \text{ and } x_i = 0 \text{ for some } 1 \leq i \leq n\}.$$

**Observation:** Given $v, w$ in the interior of $\Delta_1^+$, there is a unique $v', w' \in B$ such that $v, v', w, w'$ are all collinear, $v'$ is the closest to $v$, and $w'$ is the closest to $w$.

We can use this observation to define the *Hilbert metric* on $\Delta_1^+$ by

$$ d(v,w) := \log \frac{\|w - v'\| \cdot \|v - w'\|}{\|v - v'\| \cdot \|w - w'\|}. $$

**Observation:** The Hilbert metric is actually an honest metric.

Finally, we observe the following (which is essentially due to compactness).

**Lemma:** If $f : \Delta_1^+ \rightarrow \Delta_1^+$ is a continuous map such that $\overline{f(\Delta_1^+)} \subseteq \text{Int}(\Delta_1^+)$, then there is a uniform $C < 1$ such that $d(f(v), f(w)) \leq C d(v,w)$ for all $v,w \in \Delta_1^+$.

With this, we now have the tools to prove the Ruelle-Perron theorem.

**Sketch of Proof:** We will prove the result assuming $A$ is symmetric. Consider the map

$$  \hat{A} : \Delta_1^+ \rightarrow \Delta_1^+, \quad \hat{A}v := \frac{Av}{\|Av\|_1}.$$

Since $A$ has all positive entries, we have $\overline{\hat{A}(\Delta_1^+)} \subset \text{Int}(\Delta_1^+)$, so by the previous lemma it is a contracting map. By the contracting mapping principle, there must be a unique fixed point. This unique fixed point corresponds to a subspace $E$, and so this gives us an eigenspace for $A$. Let $\lambda_E$ be the corresponding eigenvalue. We now finish the proof in four steps. Let $v \in E$ be an eigenvector with all positive entries.

*Step 1.* We need to show that if $w$ is also an eigenvector for $A$ corresponding to $\lambda_E$, then $w \in E$. If $w$ is such an eigenvector and not in $E$, then there must be (at least) one entry of $w$ which is not strictly positive. Consider now the vector $z = v + tw$ for $t \in \mathbb{R}$. Since these are both eigenvectors, we have that $z$ is an eigenvector. Furthermore, if we choose $t$ small enough, then $z$ will have all positive entries, and hence must lie in $E$ by the contracting mapping principle. Since $E$ is a subspace, this forces $w$ to lie in $E$, a contradiction. Thus, $\lambda_E$ is a simple eigenvalue.

*Step 2.* Let's first show that for any other eigenvalue $\lambda$, we have $\vert \lambda_E \vert \geq \vert \lambda \vert$. Let $w$ be such that $Aw = \lambda w$. Notice that 

$$\lambda w_i = (Aw)_i = \sum_{j=1}^k A(i,j) w_j.$$

Now taking the absolute value of both sides, we have

$$ \vert \lambda \vert \vert w_i \vert \leq \sum_{j=1}^k A(i,j) \vert w_j \vert.$$

Let $z = (\vert w_1 \vert, \ldots, \vert w_k \vert)^T$. This shows us that for each $i$, we have $\vert \lambda \vert z_i \leq (A z)_i$. Let $v$ be the left eigenvector corresponding to $\lambda_E$ with all positive entries. We see that for each $j$ we have


$$ \vert \lambda \vert z_i \cdot v_i \leq \sum_{j=1}^k A(i,j) z_j \cdot v_i.$$
Summing over $i$, we get

$$ \vert \lambda \vert v z \leq vAz = \lambda_E vz.$$

*Step 3.* We will show that if $\vert \lambda \vert = \lambda_E$, then $z$ (which is the vector whose components are the absolute value of the components of $w$) must lie in $E$. Notice that 

$$ 0 = vAz - \vert \lambda \vert vz = v \left(Az - \vert \lambda \vert z \right).$$
Since the entries of $v$ are all positive, we must have $Az = \vert \lambda \vert z$. If $\vert \lambda \vert = \lambda_E$, then this implies that $z \in E$. Since $A$ is symmetric, this shows us that $z = C v^T$ for some $C > 0$.

*Step 4.* We now need to show that if $\vert \lambda \vert = \lambda_E$, then $\lambda = \lambda_E$. In the previous step, we had shown that $z \in E$. Using Cauchy-Schwarz, we have

$$ \left\vert \sum_{j=1}^k w_j v_j\right\vert^2 \leq \left(\sum_{j=1}^k v_j^2\right) \left( \sum_{j=1}^k z_j^2 \right),$$

with equality if and only if $v$ and $w$ are linearly dependent. Thus, we aim to show that

$$ \left\vert \sum_{j=1}^k w_j v_j\right\vert = C\left(\sum_{j=1}^k v_j^2\right),$$
 
Observe that

$$ \sum_{j=1}^k w_j v_j =  v w = \lambda_E^{-1} vAw = \lambda_E^{-1} \sum_{i=1}^k \sum_{j=1}^k v_iA(i,j) w_j.$$

Taking the absolute value,

$$ \left\vert \sum_{j=1}^k w_j v_j \right\vert = \lambda_E^{-1} \left\vert \sum_{i=1}^k v_i \sum_{j=1}^k A(i,j)w_j \right\vert. $$

Now, using previous step, we know that 

$$  \sum_{j=1}^k A(i,j) \vert w_j \vert = \sum_{j=1}^k A(i,j) z_j = \lambda_E z_i =\vert \lambda \vert z_i =  \vert (Aw)_i \vert = \left \vert \sum_{j=1}^k A(i,j) w_j \right\vert, $$

so multiplying by $v_i,$ using the $v_i$ are positive, and adding yields

$$ \left\vert \sum_{j=1}^k w_j v_j \right\vert = \lambda_E^{-1} \left\vert \sum_{i=1}^k v_i \sum_{j=1}^k A(i,j)w_j \right\vert = \lambda_E^{-1} \sum_{i=1}^k v_i \sum_{j=1}^k A(i,j) z_j = \lambda_E^{-1} v A z = vz = C \sum_{i=1}^k v_i^2, $$

as desired. This shows that $w$ must lie in $E$, and so $\lambda = \lambda_E$. $\square$

**Remark:** The steps are mostly the same for the non-symmetric case, but one has to take more care in Steps 2 and 3.
## Shifts of finite type

We briefly recall the set up for symbolic dynamics and what an SFT is. Many of the details follow the first chapter of [Parry and Pollicott's book](https://www.numdam.org/item/AST_1990__187-188__1_0.pdf) as well as the beautiful notes by [Lalley](https://galton.uchicago.edu/~lalley/Courses/312/MarkovChains.pdf).

We will use the notation $\mathbb{N} := \{1, \ldots\}$, and we let $X := \{1, \ldots, k\}^\mathbb{N}$. Given $x \in X$, we will write $x = (x_1, \ldots)$ for the projections onto the respective spaces. The *shift map* is given by 

$$ \sigma : X \rightarrow X, \quad \sigma(x) = y, \text{ where } y_i = x_{i+1}.$$

Recall that if we give $\{1, \ldots, k\}$ the discrete topology and $X$ the product topology, then the product topology on $X$ is generated by the collection of all sets of the form

$$[x_1, \ldots, x_n] := \{y \in X : y_i = x_i \text{ for } 1 \leq i \leq n \}. $$

We call these sets the *cylinders*, and the *length* of the cylinder is the number of coordinates that are being fixed. 

We now recall how this can be connected to a metric. For $\theta \in (0,1)$, we adopt the convention $\theta^\infty = 0$. Given $x, y \in X$, we let $n(x,y) := \min\{n \in \mathbb{N} \cup \{\infty\} \mid x_n \neq y_n\}$, and for $\theta \in (0,1)$ we can define a metric by $d_\theta(x,y) = \theta^{n(x,y)}$. It is easy to check that this is a metric, and furthermore the topology generated by this metric coincides with the topology on $X$. 

Let $A$ be a $k \times k$ matrix whose $(i,j$)-entry is given by $A(i,j) \in \{0,1\}$. We say that the matrix $A$ is *irreducible* if for each $(i,j)$, there is an $m \geq 1$ such that $A^{m}(i,j) > 0$. As an example, the matrix

$$ A = \begin{pmatrix}1 & 0 \\ 1 & 1 \end{pmatrix} $$

will be irreducible, while the matrix

$$ A = \begin{pmatrix}1 & 0 \\ 0 & 0 \end{pmatrix}$$

is clearly not irreducible. 

**Standing assumption 1:** All matrices $A$ will be irreducible.

Let

$$ X_A := \{x \in X : A(x_i, x_{i+1}) = 1 \text{ for } i \geq 0\}.$$

It is easy to see that $X_A$ is invariant for the shift map, and so from now on we will work with the shift on the level of $X_A$, say, $\sigma : X_A \rightarrow X_A$.

One may also be interested in mixing properties of the shift map, which leads us to the notion of period. The *period map* for $A$ is the map
$$ p : \{1, \ldots, k\} \rightarrow \mathbb{N}, \quad p(i) := \text{GCD}(\{n \in \mathbb{N} : A^n(i,i) > 0\}).$$
We will say that $A$ is *aperiodic* if the greatest common divisor of $\{p(1), \ldots, p(k)\}$ is $1$, and one can show that this is equivalent to checking that $\text{GCD}(\{n \in \mathbb{N} : A^n(i,i) > 0 \text{ and } i \in \{1,\ldots, k\}\}) = 1$. 

While not every matrix is aperiodic, one can decompose $X_A$ into a finite union of invariant subsets along which the (corresponding) matrix *is* aperiodic, and so the next standing assumption is not so outrageous.

**Standing assumption 2:** All matrices $A$ will be aperiodic.

From now on, given $A$ satisfying our standing assumptions, we say that $\sigma : X_A \rightarrow X_A$ is a *shift of finite type*, or SFT for short. Note that not all cylinders are non-empty anymore; for example, if $A(x_0, x_1) = 0$, then the cylinder $[x_0, x_1] = \varnothing$. We write $\mathcal{C}(n)$ for all cylinders of length $n$ which are non-trivial. The *topological entropy* of the SFT is then given by 

$$h := \lim_{n \rightarrow \infty} \frac{1}{n} \log(\# \mathcal{C}(n)).$$

**Remark:** Notice that 

$$\# \mathcal{C}(n) = \sum_{1 \leq i,j \leq k} A^{n-1}(i,j) = 1^T A^{n-1} 1,$$ 

where $1$ is the vector of all ones. Using the Perron-Frobenius theorem, we have that

$$\# \mathcal{C}(n) \sim c \lambda^{n-1},$$

where $\lambda$ is the dominant eigenvalue. This shows that this limit exists, and, in fact, the entropy corresponds to the dominant eigenvalue coming from the Perron-Frobenius theorem.  

Moreover, we will say that a finite sequence $(x_1, \ldots, x_n)$ is *admissible* if $[x_1, \ldots, x_n] \in \mathcal{C}(n)$, or, in other words, $A(x_i, x_{i+1}) = 1$ for all $1 \leq i < n$. 

One key property that we will need is the *specification* property, which we describe in the following lemma.

**Lemma:** There is a uniform constant $M > 0$ such that $A^M(i,j) > 0$ for all $i,j \in \{1, \ldots, k\}$.

In particular, this has the following (important) consequence.

**Observation:** Given finite sequences $(x_1, \ldots, x_n)$ and any symbol $z \in \{1, \ldots, k\}$, there is a finite sequence $(x_{n+1}, \ldots, x_{n+R})$, where $R \leq M$, such that $(x_1, \ldots, x_{n+R}, z)$ is admissible.

Finally, we set


$$P(n) := \bigcup_{k \leq n} \text{Fix}(\sigma^k), \text{ and } P := \bigcup_{n \geq 0} P(n).$$

**Remark:** We will not take the time to write it in detail, but essentially all of the same details and definitions hold if we replace $X$ with the set $\{1, \ldots, k\}^{\mathbb{Z}}$. It will be clear from context which set we decide to work with.
## Suspension flows

A function $r : X_A \rightarrow \mathbb{R}$ is *$\theta$-Lipschitz* if there is a constant $C > 0$ such that we have $d_\theta(r(x), r(y)) \leq C d_\theta(x,y)$ for all $x,y \in X_A$. We also adopt the notation

$$r^n(x) := \sum_{k=0}^{n-1} r(\sigma^k(x)).$$

Given a $\theta$-Lipschitz map $r$, which we will call the *roof function*, we can define the *suspension space* corresponding to the roof function as

$$X_A^r := \{(x,t) : x \in X_A, 0 \leq t \leq r(x)\}/\sim$$

where $(x, r(x)) \sim (\sigma(x), 0)$. We equip this space with the metric

$$ d_\theta((x,t),(y,s)) := d_\theta(x,t) + \vert t-s \vert.$$

The *suspension flow* is then the flow on $X_A^r$ with corresponding vector field $\partial/\partial t$. However, we can state it more precisely -- it is the flow $\sigma^t : X_A^r \rightarrow X_A^r$ given by $\sigma^t(x,s) := (x, s+t)$ for small $t$. A *closed orbit* for the suspension flow is then a curve $\gamma(t) := \sigma^t(x,s)$ such that $\gamma(0) = \gamma(T)$ for some $T > 0$. The smallest such $T$ is the *period* of the flow. 

We observe that every closed orbit must pass through the roof function at some point (since the vector field is only pointing up). As a consequence, given a closed orbit $\gamma$, we can associate to it a point $(x,0) \in X_A^r$. Observe that $\sigma^T(x,0) = (x,0)$ happens if and only if $r^n(x) = T$ and $\sigma^n(x) = x$. Thus, the collection of points on closed orbits with length up to $T$, $P(T)$, has some correspondence to the set

$$ \Gamma(T) := \{ x \in X_A^r : r^n(x) \leq T \text{ and } \sigma^n(x) = x\}.$$

The correspondence is that $\Gamma(T)$ is the projection of $P(T)$ onto the base $X_A \times \{0\}$ along orbits. Furthermore, the flow is isometric in the second coordinate (by construction), and so we have the following.

**Observation:** The set $P(T)$ is $\eta$-dense in $X_A^r$ with respect to $d_\theta$ if and only if $\Gamma(T)$ is $\eta$-dense in $X_A$ with respect to $d_\theta$.


## Markov partitions

We now turn to the smooth setting, following the notes by [Walkden](https://personalpages.manchester.ac.uk/staff/charles.walkden/magic/lecture10.pdf). Let $M$ be a closed manifold equipped with some Riemannian metric, and let $f : M \rightarrow M$ be a $C^\infty$-diffeomorphism (note that lower regularity is allowed in other texts, but for todays purposes we'll just ignore this). We say that $f$ is *Anosov* if there is a $df$-invariant splitting of the tangent bundle $TM = E^s \oplus E^u$ and constants $C, \lambda > 0$ such that for all $n \geq 0$, if $v \in E^s(x)$, then $\|d_xf^n(v)\| \leq C e^{-n\lambda}$, and if $v \in E^u(x)$ then $\|d_xf^n(v)\| \geq C e^{n\lambda}$. 

**Remark:** While we need to equip $M$ with some metric so that this is well-defined, the property of being Anosov is independent of the metric.

The classical example of an Anosov diffeomorphism is *Arnol'd's cat map*, which is the diffeomorphism on $\mathbb{T}^2$ corresponding to the matrix

$$ A = \begin{pmatrix} 2 & 1 \\ 1 & 1\end{pmatrix}.$$

It turns out that, if we are only interested in Holder properties of SFT's, then we can translate these to statements about Anosov diffeomorphisms through a nice covering of our manifold $M$. We make this a little more precise, although the details are technical. 

Let $\epsilon > 0$ be small. The *local stable manifold* of radius $\epsilon > 0$ centered at $x \in M$ is the set

$$ W^{s}_\epsilon(x) := \{y \in M : d(f^n(x), f^n(y)) \leq \epsilon \text{ for all } n \geq 0\}.$$

Similarly, the *local unstable manifold* of radius $\epsilon > 0$ centered at $x \in M$ is the set

$$ W^{u}_\epsilon(x) := \{y \in M : d(f^{-n}(x), f^{-n}(y)) \leq \epsilon \text{ for all } n \geq 0\}.$$

The *local stable/unstable manifold theorem* says there is a uniform $\epsilon > 0$ such that the local stable and unstable manifolds are actually smoothly embedded disks for all $x\in M$ (and hence the "manifold" part of the name is not arbitrary). Also important is the following: There is a uniform $\eta > 0$ such that if $d(x,y) < \eta$, then 

$$\#( W^u_\epsilon(x) \cap W^s_\epsilon(y)) = 1.$$ 

We denote this unique intersection point by $[x,y]$, and we call this the *Bowen bracket* of the two points.

A subset $R \subseteq M$ is a *rectangle* if $x,y \in R$ implies that $[x,y] \in R$. We will be dealing with *proper rectangles*, which just means that $R$ is proper in the topological sense (i.e., it is equal to the closure of its interior). If $R$ is a proper rectangle and $x \in R^\mathrm{o}$, then we write $W^{s/u}(x,R) := W^{s/u}_\epsilon(x) \cap R$. Finally, a *Markov partition* of $M$ is a family of proper rectangles $\mathcal{R} = \{R_1, \ldots, R_k\}$ which satisfies the following:
1. we have $\bigcup_{i=1}^k R_i = M$,
2. $R_i^{\mathrm{o}} \cap R_j^{\mathrm{o}} = \varnothing$ if $i \neq j$,
3. if $x \in R_i^{\mathrm{o}}$ and $f(x) \in R_j^{\mathrm{o}}$, then $f(W^s(x,R_i)) \subseteq W^s(f(x), R_j)$, and
4. if $x \in R_i^{\mathrm{o}}$ and $f^{-1}(x) \in R_j^{\mathrm{o}}$, then $f^{-1}(W^u(x,R_i)) \subseteq W^u(f(x), R_j)$.
The *diameter* of the Markov partition will be $\sup_{1\leq i \leq k} \text{Diam}(R_i)$.

The famous theorem (which is due to [Sinai]() and later expanded on by [Bowen](https://www.jstor.org/stable/2373370?seq=1)) says that these partitions always exist.

**Theorem:** If $f : M \rightarrow M$ is an Anosov diffeomorphism, then there exists a Markov partition $\mathcal{R}$ with arbitrarily small diameter.

With this Markov partition, we define the $k \times k$ matrix by $A(i,j) = 1$ if and only if $f(R_i^{\mathrm{o}}) \cap R_j^\mathrm{o} \neq \varnothing$. Let $X_A$ be the associated sequence space to this matrix (which are bi-infinite sequences), and define 

$$ \pi : X_A \rightarrow M, \quad \pi(x) = \bigcap_{i=-\infty}^\infty f^{-i}(R_{x_i}). $$

**Theorem:** The map $\pi : X_A \rightarrow M$ is 
1. Holder continuous (for some $\alpha \in (0,1)$) and surjective,
2. injective on a set of full measure and on a dense residual set,
3. bounded-to-one, and
4. $f \circ \pi = \pi \circ \sigma$.

**Remark:** The same thing can be said for Anosov flows, which we will not get into for times' sake. 
# Main result

With the preliminaries out of the way, we now dive in to analyzing the density of closed orbits with a prescribed length.
## Shifts of finite type

The goal of this section is to prove the following.

**Theorem:** Let $\theta \in (0,1)$ and $\sigma : X_A \rightarrow X_A$ be a shift of finite type. There exists constants $C, \delta > 0$ such that for every $n$ large enough, we have $P(n)$ is $\eta$-dense, where $\eta \leq C e^{-n \delta}$. Furthermore, $\delta$ depends only on $\theta$, and $C$ depends only on $\sigma$.

**Proof:** Let $M$ be our specification constant. Supposing that $n$ is large enough, we can use the specification property to show that for any finite admissible sequence $(x_1, \ldots, x_{n-M-1})$,  we can add on more symbols to get a sequence $(x_1, \ldots, x_{n-M}, x_{n-M+1}, \ldots, x_1)$ which is admissible. This shows that for every cylinder in $C \in \mathcal{C}(n-M-1)$, we have $C \cap P(n) \neq \varnothing$. From this, we deduce that for every $x \in X_A$, we have $d_\theta(P(n), x) \leq \theta^{n-M-1} = \theta^{-M-1} e^{n\log(\theta)}.$ Let $\delta := - \log(\theta)$ and $C := \theta^{-M-1}$. $\square$

An easy corollary is the following (well-known) observation.

**Corollary:** If $\sigma : X_A \rightarrow X_A$ is a shift of finite type, then $P$ is dense.

We claim that this also extends to Anosov diffeomorphisms through Markov partitions. Let 

$$ P(n) := \bigcup_{k \leq n} \text{Fix}(f^k).$$

**Corollary:** Let $f : M \rightarrow M$ be an Anosov diffeomorphism. There are constants $C, \delta > 0$ such that for every $n$ large enough, we have $P(n)$ is $\eta$-dense, where $\eta \leq C e^{-n\delta}$.

**Proof:** Let $\pi : X_A \rightarrow M$ be the coding map coming from our Markov partition construction. Let $p \in M$ be arbitrary. We can write $p = \pi(x)$ where $x \in X_A$. Using the theorem, we have that there is a $z \in P(n)$ such that $d_\theta(x, z) \leq C e^{-n \delta}$, so $d(\pi(x), \pi(z)) \leq C' d_\theta(x,z)^\alpha \leq C' \cdot C^\alpha e^{-n \alpha \delta}.$ The result now follows if we can show that $\pi(z) \in P(n)$. Since $z \in P(n)$, we have $\sigma^k(z) = z$ for some $k \leq n$, so $f^k(\pi(z)) = \pi(\sigma^k(z)) = \pi(z)$, and hence $\pi(z) \in P(n)$. $\square$ 

Another interesting corollary is the following.

**Corollary:** Let $r : X_A \rightarrow \mathbb{R}$ be Lipschitz continuous, and let $\sigma^t : X_A^r \rightarrow X_A^r$ be a suspension over a shift of finite type. There exists constants $C, \delta > 0$ such that for every $n$ large enough, we have $P(T)$ is $\eta$-dense, where $\eta \leq C e^{-n \delta}$. 

**Proof:** We use the fundamental observation from that section, which is that we can reduce the study of $P(T)$ to the study of $\Gamma(T)$. Now let $M := \|r\|_\infty$, and notice that if $x \in P(\lfloor T/M \rfloor)$, then for $k$ such that $\sigma^k(x) = x$, we have $r^k(x) \leq k M \leq T$. Thus, $P(\lfloor T/M \rfloor) \subseteq \Gamma(T)$, and from this we can deduce that $\Gamma(T)$ is $\eta$-dense, where $\eta \leq C e^{-(T/M - 1)\delta}$ and $C$ and $\delta$ are from the theorem. The result now follows. $\square$   

Finally, nearly the same argument extends this from the suspension case to the case of Anosov flows.
## Follow up remarks

- Since we are using Markov partitions, one could directly jump to Axiom A diffeomorphisms and flows, but for the sake of presentation we don't get into that.
- It would be interesting to see what an optimal choice of $\delta$ is. For example, using more geometric means, Butt was able to get a similar result for Anosov geodesic flows in [Lemma 2.9](https://arxiv.org/abs/2203.12128).
- It might be interesting to see how this would follow from an effective equidistribution result (in the vein of Kadyrov in [here](https://arxiv.org/abs/1608.01767), and later improved by O'Hare in [here](https://arxiv.org/abs/2310.20027)). 