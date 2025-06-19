---
layout: post
title: Reparameterizations of Contact Flows on 3-manifolds
tags:
  - dynamics
  - geometry
categories:
  - Dynamics
  - Geometry
---

In this post, we survey results on reparameterizations of contact flows on 3-manifolds.

**Warning:** This is still a work in progress!
# Preliminaries

We start by recalling some of the standard definitions. Throughout this post, $N$ will denote an oriented closed $3$-manifold, and $\mathfrak{X}(N)$ will denote the collection of smooth vector fields on $N$ which are nowhere vanishing. Given $X \in \mathfrak{X}(N)$, we will use $X^t : N \rightarrow N$ to denote its corresponding smooth flow. We will also equip $N$ with some Riemannian metric $\|\cdot\|$.
## Anosov flows

We say that a nowhere vanishing vector field $X \in \mathfrak{X}(N)$ is *Anosov* there is a dense orbit for $X^t$ as well as a $dX^t$-invariant splitting $TN = E^s_X \oplus \mathbb{R}X \oplus E^u_X$ and constants $C, \lambda > 0$ such that for all $x \in N$, $v \in E^s_X(x)$, $w \in E^u_X(x)$, and $t \geq 0$, we have

$$ \|d_x X^t(v)\| \leq C e^{-\lambda t} \text{and} \|d_x X^{-t}(w)\| \leq C e^{-\lambda t}.$$

We denote the collection of Anosov vector fields on $N$ by $\mathfrak{X}_A(N)$. 

Recall that a $3$-form $\mu$ on $N$ is a *volume form* if it is nowhere vanishing, and we denote the collection of volume forms on $N$ by $\Omega_{vol}^3(N)$.  and we say that $X \in \mathfrak{X}(N)$ is *volume preserving* if there exists a $\mu \in \Omega_{vol}^3(N)$ such that 

$$ \frac{d}{dt} (X^t)_*(\mu) = \mathcal{L}_X(\mu) = 0,$$

and we denote the collection of volume preserving Anosov flows by $\mathfrak{X}_A^{vol}(N)$. Finally, we refer to the plane field $x \mapsto E^s_X(x) \oplus E^u_X(x)$ as the *Anosov structure*.

## Contact geometry and dynamics

Let $\Omega^1(N)$ be the collection of $1$-forms on $N$. We say that $\alpha \in \Omega^1(N)$ is a *contact form* if $\alpha \wedge d\alpha$ is a volume form, and we denote the collection of contact forms by $\Omega^1_{con}(N)$. 

The *contact structure* associated to the contact form is $\xi := \ker(\alpha)$. We say that a vector field $X$ is *contact* if there exists a contact form $\alpha$ which is invariant under the flow, and we denote the collection of contact flows by $\mathfrak{X}^{con}(N)$. 

Given a contact form $\alpha \in \Omega^1_{con}(N)$, if $X \in \mathfrak{X}(N)$ is such that $\iota_X \alpha = 1$ and $\iota_X d\alpha = 0$, then we refer to $X$ as a *Reeb vector field*. 

As an easy warm up, let's observe the following.

**Claim:** We have $\mathfrak{X}^{con}_A(N) \subseteq \mathfrak{X}^{vol}_A(N)$.

**Proof:** Let $X \in \mathfrak{X}^{con}_A(N)$, and let $\alpha$ be the contact $1$-form it preserves. Defining $\mu := \alpha \wedge d\alpha$, observe 

$$ \mathcal{L}_X(\mu) = \mathcal{L}_X(\alpha) \wedge d\alpha + \alpha \wedge \mathcal{L}_X(d\alpha) = \alpha \wedge (d(\iota_X d\alpha)).$$

Now, recall

$$ 0 = \mathcal{L}_X(\alpha) = \iota_X d\alpha + d\iota_X\alpha,$$

so we can write

$$ \mathcal{L}_X(\mu) =  \alpha \wedge (d(\iota_X d\alpha))= - \alpha \wedge (dd\iota_X\alpha) = 0.$$

The result follows. $\square$ 

More generally, a *contact structure* on $N$ is a plane field $x \mapsto P(x)$ which is non-integrable (recall that a plane field is simply a smooth assignment of $2$-dimensional subspaces of the tangent bundle). The following is the content of [Frobenius' theorem](https://en.wikipedia.org/wiki/Frobenius_theorem_(differential_topology)) (which could be taken as a definition).

**Theorem:** A plane field $P$ is integrable if and only for any vector fields $X, Y$ which are tangent to $P$, we have $[X,Y]$ is tangent to $P$.

Locally, we can express the plane field as the kernel of a $1$-form, label this $1$-form by $\alpha_P$. As a corollary of the Frobenius theorem we deduce the following *contact theorem*.

**Corollary:** A plane field $P$ is non-integrable if and only if for each local $1$-form $\alpha_P$, we have $\alpha_P \wedge d\alpha_P$ is nowhere vanishing.

Now, an interesting question is when we can go from a contact structure to a contact form. We say that the plane field $P$ is *co-orientable* if there is a nowhere vanishing vector field $X$ such that $X(x) \notin P_x$ for all $x \in N$. In this case, using a partition of unity, we deduce the following.

**Corollary:** All non-integrable co-orientable contact structure are in one-to-one correspondence with contact forms.

We now make a few easy observations. First, let's show there is always a unique Reeb vector field.

**Claim:** If $\alpha \in \Omega^1_{con}(N)$, then there there exists a unique Reeb vector field.

**Proof:** First, define 

$$ \ker(d_x\alpha) = \{w \in T_xN \mid d_x\alpha(w, v) = 0 \text{ for all } v \in T_xN \}.$$

Observe that if $\ker(d_x\alpha) \cap \ker(\alpha_x) = 0$, so $\alpha_x : \ker(d_x\alpha) \rightarrow \mathbb{R}$ is an isomorphism. In particular, we can define a smooth vector field $X$ such that $\alpha_x(X(x)) = 1$, and this satisfies the definition for being a Reeb vector field. Furthermore, it is clear from this construction that it must be unique. $\square$ 

Next, let's show that a Reeb vector field is a contact vector field.

**Claim:** If $X$ is the Reeb vector field for $\alpha \in \Omega^1_{con}(N)$, then $X \in \mathfrak{X}^{con}(N)$. 

**Proof:** Observe that $\mathcal{L}_X(\alpha) = d\iota_X \alpha + \iota_X d\alpha = 0$. $\square$

Finally, let's show that every contact flow is the Reeb vector field of some contact form.

**Claim:** If $X \in \mathfrak{X}^{con}(N)$ is such that there is a contact from $\theta$ which is invariant under the flow of $X$ and $X$ is nowhere tangent to $\ker(\theta)$, then there exists a contact form $\alpha$ such that $X$ is the Reeb vector field of $\alpha$.

**Proof:** Consider $\alpha := \theta/\theta(X)$. Observe that $\alpha \wedge d\alpha = (1/\theta(X))^2 \theta \wedge d\theta$, so $\alpha$ is a contact form. Furthermore, the contact structure for $\alpha$ and $\theta$ are the same, so we have $\mathcal{L}_X(\alpha) = \phi \alpha$ for a smooth potential $\phi$. Finally, notice that 

$$\phi = \iota_X \mathcal{L}_X(\alpha) = \iota_X( d\iota_X \alpha + \iota_X d\alpha) = d\alpha(X,X) = 0.$$

Thus, 

$$ 0 = \mathcal{L}_X(\alpha) = \iota_X d\alpha + d\iota_X \alpha = \iota_X d\alpha,$$

and we get that $X$ is the Reeb vector field for $\alpha$. $\square$ 

It is easy to see that the last claim can be upgraded to an if and only if, so Reeb vector fields are precisely those contact flows which are nowhere tangent to some contact structure. 

We will mostly be interested in those contact flows which are also Anosov; we denote the collection of corresponding vector fields by $\mathfrak{X}_A^{con}(N)$. In light of the above observations, we deduce the following.

**Theorem:** Let $X \in \mathfrak{X}^{con}_A(N)$. If the Anosov structure is non-integrable, then $X$ is the Reeb vector field for a contact form $\alpha_X$.

Recall that $X \in \mathfrak{X}(N)$ is *mixing* if for any two non-empty open sets $U,V \subseteq N$, there exists a $T_0 > 0$ such that for all $t \geq T_0$, we have $X^t(U) \cap V \neq \varnothing$. The following is straightforward.

**Theorem:** Every $X \in \mathfrak{X}^{con}_A(N)$ is mixing.

Plante proved the following alternative in [this](https://www.jstor.org/stable/pdf/2373755.pdf) paper 

**Theorem:** Let $X \in \mathfrak{X}_A^{vol}(N)$. We have that $X$ is not mixing if and only if the Anosov structure is jointly integrable.

Thus, combining the above two theorems, we deduce that every $X \in \mathfrak{X}^{con}_A(N)$ can be realized as the Reeb vector field for a contact form $\alpha_X$ such that $\ker(\alpha_X) = E^s \oplus E^u$. We call this $1$-form the *Anosov form* associated to $X$. 

## Dynamical invariants

Before moving on, let's recall some dynamical invariants that will be of interest. Throughout, let $X \in \mathfrak{X}_A(N)$, and let $\mathcal{M}(X)$ be the collection of Borel probability measures on $N$ which are invariant under the flow of $X$. 

### Metric entropy, topological entropy, and pressure

Our first stop will be the metric entropy. Recall that defining this for flows is a little tricky. First, fixing $\mu \in \mathcal{M}$, let's examine $T := X^t : N \rightarrow N$, where $t > 0$ is arbitrary. We see that $(N, T, \mu)$ defines an invertible probability measure preserving transformation, and so we can discuss entropy for this. Let's outline the ingredients.
- A *finite partition* of $N$ is a finite set of disjoint, measurable sets whose union is $N$. We will just assume that $\mu(A) > 0$ for all $A \in \xi$.
- Given a finite partition $\xi$, the *metric entropy* of this partition is $H_\mu(\xi) := - \sum_{A \in \xi} \mu(A) \log(\mu(A))$. 
- Given two finite partitions $\xi_1$ and $\xi_2$, we define their *refinement* to be $\xi_1 \vee \xi_2 := \{A \cap B \mid A \in \xi_1 \text{ and } B \in \xi_2\}$. We also write $T(\xi) := \{T(A) \mid A \in \xi\}$; this gives rise to a finite partition of $N$, and the same works for iterates of $T$.
- Given a finite partition $\xi$ of $N$, we write $\xi_n := \xi \vee T^{-1}(\xi) \vee \cdots \vee T^{-n+1}(\xi)$. 
- We can define the *entropy of a finite partition* to be $h_\mu(T, \xi) := \lim_{n \rightarrow \infty} \frac{1}{n} H_\mu(\xi_n).$ This limit exists thanks to Fekete's lemma.
- Finally, the *metric entropy* is $h_\mu(T) := \sup_\xi h_\mu(T,\xi)$, where the supremum is taken over all finite partitions of $N$.

In light of this, it is easy to check that for all $t \in \mathbb{R}$, we have $h_\mu(X^t) = \vert t \vert h_\mu(X^1)$, so the entropy of the time $1$ map essentially determines the entropy of the flow. We write $h_\mu(X) := h_\mu(X^1)$. Finally, we define the *topological entropy* to be $h_{top}(X) := \sup_\mu h_\mu(X)$, where the supremum is over $\mu \in \mathcal{M}(X)$. 

Finally, given a Holder potential $\varphi$ on $N$, we define its *metric pressure* by 

$$ \mathcal{P}_X(\varphi, \mu) := h_\mu(X) + \int_N \varphi \,d\mu,$$

and its *topological pressure* by 

$$\mathcal{P}_X(\varphi) := \sup_\mu \mathcal{P}_X(\varphi, \mu),$$ 

where the supremum is over $\mu \in \mathcal{M}(X)$. An amazing fact thanks to Bowen is the following.

**Theorem:** For every Holder potential $\varphi$, there is a unique measure $\mu_\varphi \in \mathcal{M}(X)$ such that $\mathcal{P}_X(\varphi) = \mathcal{P}_X(\varphi, \mu_\varphi).$ 

We call this measure the *equilibrium state* of the potential. Finally, recall that a measure $\mu \in \mathcal{M}(X)$ is *ergodic* if $X^{t}(A) = A$ for all $t \in \mathbb{R}$ implies that $\mu(A) \in \{0,1\}$, and let $\mathcal{M}_e(X) \subseteq \mathcal{M}(X)$ be those measures which are ergodic. Then the supremum in both of the above definitions can be taken over $\mathcal{M}_e(X)$ instead of $\mathcal{M}(X)$, and every equilibrium state.
### Lyapunov exponents

The idea behind Lyapunov exponents is that they give quantitative estimates on how fast the system is expanding or contracting on an exponential level. We now switch perspectives back to $X \in \mathfrak{X}(N)$. Oseledet's multiplicative ergodic theorem tells us that for $\mu \in \mathcal{M}_e(X)$, the limit

$$ \chi(x,v) := \lim_{t \rightarrow \infty} \frac{1}{t} \log \|d_xX^t(v)\|$$

exists for $\mu$-almost every $x \in N$ and non-zero vector $v \in T_xN$. We can then decompose our space as 

$$ T_xN = E^s_X(x) \oplus E^c_X(x) \oplus E^u_X(x),$$

where $E^s(x)$ are those vectors such that $\chi(x,v) < 0$, $E^c(x)$ are those vectors such that $\chi(x,v) = 0$, and $E^u(x)$ are those vectors such that $\chi(x,v) > 0$. Furthermore, these spaces are $dX^t$-invariant.

In the setting where the flow is Anosov, we do not have to restrict down to this measure theoretic setting. In particular, we can define 

$$ \chi^u_X(x) := \lim_{t \rightarrow \infty} \frac{1}{t} \log \|d_xX^t|_{E^u(x)}\|,$$

and similarly with the stable. Furthermore, we have $\chi^s_X < 0 < \chi^u_X$.

# Reparameterizations and orbit equivalences

With the above set up, we are now ready to try to understand how reparameterizations of contact flows behave. We will follow [Parry](https://projecteuclid.org/journals/communications-in-mathematical-physics/volume-106/issue-2/Synchronisation-of-canonical-measures-for-hyperbolic-attractors/cmp/1104115700.full) as well as the paper by [Gelfert and Motter](https://arxiv.org/pdf/1010.1791)
## Reparameterizations

Let $X \in \mathfrak{X}(N)$. A *cocycle* over $X$ is a function of the form $\Phi : N \times \mathbb{R} \rightarrow \mathbb{R}$ which satisfies the *cocycle identity* for all $x \in N$ and $t,s \in \mathbb{R}$:

$$ \Phi(x,t+s) = \Phi(x,t) + \Phi(X^t(x), s).$$

Furthermore, we will assume that $\Phi(x,t) >0$ if $t > 0$, and that $\Phi(x,t)$ is differentiable in the flow direction. A *reparameterization* of the flow $X^t$ is a flow given by 

$$ Z^t(x) = X^{\Phi(x,t)}(x),$$

where $\Phi$ is a cocycle over $X$. Let $\varphi(x) := \frac{d}{dt} \Big|_{t=0} \Phi(x,t)$. Notice that 

$$ Z(x) = \frac{d}{dt}\Big|_{t=0} Z^t(x) = \frac{d}{dt} \Big|_{t=0} X^{\Phi_\varphi^X(x,t)}(x) = \varphi(x) X(x),$$

which proves the following.

**Claim:** If $X \in \mathfrak{X}(N)$ and $Z$ is a reparameterization of $X$ given by $\varphi$, then $Z = \varphi X$.

From now on, we will write reparameterizations in terms of their vector fields. Notice that if we set $\varphi(x)$ to be the $t$-derivative of $\Phi(x,t)$, then 

$$ \int_0^t \varphi(X^\tau(x))\,d\tau = \Phi(x,t). $$

We call $\varphi$ the *generator* of the cocycle. Since our cocycles are differentiable in the flow direction, such a generator always exists, and in the context of reparameterizations this generator will always be a positive function. In order to keep track of the flow and the generator, we now introduce the notation

$$ \Phi_\varphi^X(x,t) := \int_0^t \varphi(X^\tau(x))\,d\tau.$$

Since this is a strictly monotone function in $t$, it's inverse is well-defined. In this case, it arises very naturally through the flow $Z^t$. For convenience, let $\psi(x) := 1/\varphi(x)$.

**Claim:** We have $\Phi_\varphi^X(x, \Phi^Z_\psi(x,t)) = t = \Phi_\psi^Z(x, \Phi^X_\varphi(x,t)).$ Moreover, we have $\varphi(X^{\Phi_\psi^Z(x,t)}(x)) = 1/\psi(Z^t(x)).$ 

**Proof:** Notice that $Z^{t}(x) = X^{\Phi_\varphi^X(x,t)}(x)$, and since $\psi X = Z$, we have $X^t(x) = Z^{\Phi_\psi^Z(x,t)}(x).$ Putting these together, 
$$ Z^t(x) =  X^{\Phi_\varphi^X(x,t)}(x) = Z^{\Phi_\psi^Z(x,\Phi_\varphi^X(x,t))}(x),$$

proving one direction. The other direction is the same. Finally, take a derivative with respect to $t$ to get

$$ 1 = \frac{d}{dt} \Phi_\varphi^X(x, \Phi^Z_\psi(x,t)) = \varphi(X^{\Phi^Z_\psi(x,t)}(x)) \cdot \psi(Z^t(x)).$$
The identity follows $\square$

If we now assume that $X \in \mathfrak{X}_A(N)$, then an interesting question is when a reparameterization $Z$ must also lie in $\mathfrak{X}_A(N)$. This leads us to the following, which is due to [Anosov and Sinai](https://iopscience.iop.org/article/10.1070/RM1967v022n05ABEH001228) (see also [Parry](https://link.springer.com/article/10.1007/BF01454975) and [de la Llave, Marvo, and Moriyon](https://www.jstor.org/stable/1971334?seq=1)).

**Theorem:** If $Z = \varphi X$ is a $C^1$-reparameterization of $X \in \mathfrak{X}_A(N)$, then $Z \in \mathfrak{X}_A(N)$.

Before proving this, we need the following two identities, which should be compared to Proposition 1 in the [Gelfert and Motter](https://arxiv.org/pdf/1010.1791) paper.

**Claim:** We have

$$ d_x Z^{t}(v) = d_x X^{\Phi_\varphi^X(x,t)}(v) - \varphi(X^{\Phi_\varphi^X(x,t)}(x))X(X^{\Phi_\varphi^X(x,t)}(x)) \int_0^{\Phi_\varphi^X(x,t)} d_x(\psi \circ X^\tau)(v) \,d\tau. $$

**Sketch of Proof:** To help with notation, fix $(x,v) \in TN$, and let $z(t) := d_xZ^t(v)$ and $x(t) := d_x X^t(v)$. One can show that the curve $x$ satisfies the following variational differential equation

$$ \frac{Dx}{dt} = \nabla_{x(t)} X(X^t(x)),$$

where here $\nabla$ is the Levi-Civita connection. Let $\gamma(t) = x(\Phi_\varphi^X(x,t))$. Note that it is *not* true that $\gamma(t) = z(t)$; instead, there is some function $\kappa(t)$ such that $z(t) = \gamma(t) + \kappa(t) Z(Z^t(x))$. The game is to try to determine what this $\kappa$ is. From this relationship, we know that

$$ \frac{Dz}{dt} = \frac{D\gamma}{dt} + \dot{\kappa}(t) Z(Z^t(x)) + \kappa(t) \nabla_{Z(Z^t(x))} Z(Z^t(x)).$$

It is not hard to verify that 

$$ \frac{D\gamma}{dt} = \nabla_{\gamma(t)} Z(Z^t(x)) + \varphi(Z^t(x))^2 d_{Z^t(x)}\psi(Z(Z^t(x))),$$

and using the variational differential equation for $z$, we can deduce that 

$$ \dot{\kappa}(t) = - \varphi(Z^t(x)) d_{Z^t(x)} \psi(\gamma(t)).$$

Since $\kappa(0) = 0$, we can integrate this to get 

$$ \kappa(t) = -\int_0^t d_{Z^\tau(x)}\log(\psi)\left(\gamma(\tau) \right)\,d\tau$$

To finish the proof, we preform a change of variables $s = \Phi_\varphi^X(x,\tau)$, so $ds = \frac{d\tau}{\psi(Z^\tau(x))}$.  This then yields

$$ \kappa(\Phi^X_\varphi(x,t)) = - \int_0^{\Phi^X_\varphi(x,t)} d_x(\psi \circ X^s) \,ds,$$

as desired. $\square$

**Proof of Theorem:** For $(x,v) \in E^s_X$, set

$$ \kappa^s(x,v) := -\varphi(x)\int_0^\infty d_x(\psi \circ X^\tau)(v)\,d\tau.$$

First, observe that this integral converges, since $v \in E^s_X(x)$. Next, using that $Z(x) = \varphi(x) X(x)$ and $\varphi(x) > 0$, observe that we can write

$$ d_xZ^t(\kappa^s(x,v) X(x)) = \frac{\varphi(Z^t(x))}{\varphi(x)} \kappa^s(x,v) X(Z^t(x)).$$

In particular, if we take $v \in E^s_X(x)$, then the $X(Z^t(x))$ component of $d_xZ^t(v + \kappa^s(x,v)X(x))$ becomes

$$ \frac{\varphi(Z^t(x))}{\varphi(x)}\kappa^s(x,v) -\varphi(Z^t(x)) \int_0^{\Phi_\varphi^X(x,t)}  d_x(\psi \circ X^\tau)(v)\,d\tau,$$

which simplifies to 

$$ \varphi(Z^t(x)) \int_{\Phi_\varphi^X(x,t)}^\infty  d_x(\psi \circ X^\tau)(v)\,d\tau = \kappa^s(X^{\Phi_\varphi^X(x,t)}(x), d_xX^{\Phi_\varphi^X(x,t)}(v)).$$

In particular, this proves that for $v \in E^s_X(x)$, we have

$$d_x Z^{t}(v +  \kappa^s(x,v)X(x)) = d_x X^{\Phi_\varphi^X(x,t)}(v) +  \kappa^s(X^{\Phi_\varphi^X(x,t)}(x), d_xX^{\Phi_\varphi^X(x,t)}(v)) X(Z^t(x)),  $$

so the bundle

$$ E^s_Z(x) := \{v + \kappa^s(x,v) X(x) \mid v \in E^s_X(x) \}$$

is $Z^t$-invariant. To see that the estimates hold, simply notice that the tails of $\kappa^s(x,v)$ converge to zero exponentially fast. Finally, the same game in reverse time gives the unstable bundle. $\square$

**Remark:** A useful criterion highlighted by de la Llave, Marco, and Moriyon is that the bundle $E^s_Z(x) = \{v + \kappa^s(x,v)X(x) \mid v \in E^s_X(x)\}$ is invariant under the flow of $Z$ if and only if 

$$ \mathcal{L}_X(\psi \kappa^s(x,v)) = \psi^2 d\varphi. \square$$

### Dynamical invariants under reparameterizations


### The contact setting

Now let $X \in \mathfrak{X}^{con}_A(N)$. We say that $Z = \varphi X$ is a *special time change* of $X$ if $\varphi$ is of the form

$$ \varphi(x) = \frac{1}{C + \iota_X \omega}, $$

where $\omega$ is a closed $1$-form on $N$ and $C \in \mathbb{R}$. This definition is motivated by the following (see also Lemma 2.1 in [Fang's paper](https://arxiv.org/pdf/math/0503191)).

**Proposition:** Let $X \in \mathcal{X}^{con}_A(N)$ and let $Z = \varphi X$ be a smooth reparameterization. We have that $Z \in \mathfrak{X}^{con}_A(N)$ if and only if $Z$ is a special reparameterization.

**Proof:** We first assume that $Z$ is contact, and let $\alpha_Z$ be its Anosov form. Observe that 

$$ 1 = \iota_Z \alpha_Z = \varphi \iota_X \alpha_Z,$$

so $\psi(x) = \iota_X \alpha_Z.$ Similarly, $\iota_X \alpha_X = 1$ implies that $\iota_Z \alpha_X = \varphi(x)$. Next,

$$\iota_Z d\alpha_Z = \varphi \iota_X d\alpha_Z = 0. $$

Since $\varphi > 0$ (as this is a reparameterization), we must have $\iota_Z d\alpha_Z = 0$. With this,

$$ \mathcal{L}_X(d\alpha_Z) = d\iota_X d\alpha_Z + \iota_X dd\alpha_Z = 0.$$

Thus, we have $d\alpha_Z$ is invariant under the flow. We now claim that $\mu := \alpha_X \wedge d\alpha_Z$ is invariant under the flow. Indeed, this just follows from the calculation

$$\mathcal{L}_X(\mu) = \mathcal{L}_X(\alpha_X) \wedge d\alpha_Z + \alpha_X \wedge \mathcal{L}_X(d\alpha_Z) = 0.$$

Since the top de Rham cohomology is one dimensional, there is a smooth potential on $N$ such that $f \mu = \mu_X$. Notice that 

$$ 0 = \mathcal{L}_X(\mu_X) = X(f) \mu + f \mathcal{L}_X(\mu) = X(f) \mu.$$

Now observe that 

$$\iota_Z \mu = \varphi(x) d\alpha_Z, $$

so it is easy to see $\mu$ is a volume form. Thus, we have that $X(f) = 0$, which implies that $f$ is constant, say $f \equiv C$. In particular, we observe that this implies there is a closed $1$-form $\omega$ on $N$ such that $\alpha_Z = C \alpha_X + \omega$. Contracting both sides by $X$, we have 

$$ \psi = \iota_X \alpha_Z = C + \iota_X \omega, $$

and so this is a special reparameterization.

Now assume that $Z$ is a special reparameterization, so $\psi = C + \iota_X \omega$. We claim that the smooth $1$-form $\alpha_Z := C \alpha_X + \omega$ is the canonical $1$-form for $Z$. We break this up into three steps.

Step 1: To see that $\iota_Z \alpha_Z = 1$, notice that $Z = \varphi X = X/\psi$, so 

$$  \iota_Z \alpha_Z = C \iota_Z \alpha_X + \iota_Z \omega = \frac{C + \iota_X\omega}{C + \iota_X \omega} = 1.$$

Step 2: Since $\omega$ is closed, we have $d \alpha_Z = C d\alpha_X$, so $\iota_Z d\alpha_Z = C\varphi \iota_X d\alpha_X = 0.$

Step 3: We now need to show that $\ker(\alpha_Z)$ is the Anosov structure. Observe that

$$ \mathcal{L}_X \left( -\psi \left(\frac{\omega}{C + \iota_X\omega}\right) \right) = -\mathcal{L}_X(\omega) = \psi^2 d\varphi,$$

so by integrating we have 

$$ -\frac{\omega_x(v)}{C + \iota_X\omega(x)} =  - \varphi(x) \int_0^\infty d_x(\psi \circ X^\tau)(v) \,d\tau,$$

and this proves that 

$$ \omega_x(v) = \int_0^\infty d_x(\psi \circ X^\tau)(v) \,d\tau.$$

Using the $\kappa^s$ defined in the Anosov-Sinai theorem, this shows us that $\alpha_Z(v + \kappa^s(x,v) X(x)) = 0$ for all $v \in E^s_X(x)$. The same argument works with the unstable, and we deduce that $Z \in \mathfrak{X}_A^{con}(N)$. $\square$

**Remark:** If $Z$ is a special reparameterization of $X$, then we have that 

$$ \mu_Z = \alpha_Z \wedge d\alpha_Z = C^2 \mu_X+ Cd(\omega \wedge \alpha_X).$$

## Orbit equivalences

We'll now stick with the Anosov setting. Given $X,Y \in \mathfrak{X}_A(N)$, we say that they are *orbit equivalent* if there is a positive continuous potential and a homeomorphism  such that 

$$ h \circ Y^t(x) = X^{\Phi_\varphi^X(x,t)} \circ h(x).$$

We say that they are *conjugate* if $\varphi \equiv 1$. We now make the following easy observation.

**Claim:** If $Z = \varphi X$ is a reparameterization of $X$ and $\varphi - 1 = Xu$ for some continuous potential $u$ which is differentiable in the flow direction, then $X$ and $Z$ are conjugate.

**Proof:** First, by integrating, we have the relationship 

$$ \Phi_\varphi^X(x,t) + u(x)= u(X^t(x)) + t. $$

Letting $h(x) := X^{u(x)}(x)$, observe that 

$$ h \circ X^t(x) = X^{u(X^t(x)) + t}(x) = X^{\Phi_\varphi^X(x,t) + u(x)}(x) = Z^t \circ h(x).$$

Thus, the flows are conjugate. $\square$

We say that a continuous potential $\varphi$ is a *coboundary* if there is a continuous potential $u$ which is differentiable in the flow direction and which satisfies $\varphi = Xu$. Furthermore, given two continuous potentials $\varphi$ and $\psi$, we say that they are *cohomologous* if $\varphi - \psi$ is a coboundary. The above claim then translates to the following.

**Claim:** If $Z = \varphi X$ is a reparameterization of $X$ and $\varphi$ is cohomologous to $1$, then $X$ and $Z$ are conjugate.


