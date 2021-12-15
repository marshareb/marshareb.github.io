---
layout: post
title: Cartan's Moving Frame
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss Cartan's moving frame on a surface.

# Set Up

**EDIT (12/15):** This is an unfinished article.

Throughout let $$M$$ be an oriented surface equipped with a metric $$g$$. The goal of this article is to construct Cartan's moving frame and prove Cartan's structure equations, following Section 7.2 of [Singer and Thorpe](https://www.amazon.com/Elementary-Topology-Geometry-Undergraduate-Mathematics/dp/0387902023).

# Cartan's Moving Frame

## Connections

We'll be working with the **circle bundle**, denoted by

$$SM := \{ (x,v) \in TM : \|v\| = 1\}.$$

We also refer to this as the **unit tangent bundle**. The reason for the name circle bundle is because the circle "acts" on $$SM$$ in the following sense. First if we restrict to the space $$S_xM$$ we are looking at all unit vectors based at $$x$$. This is a vector space with a metric $$g_x$$ on it. As such, we can define rotation in terms of this metric -- just view the space to be $$\mathbb{R}^2$$ and rotate it as a vector in this space. Consequently we get a group action

$$ S^1 \times SM \rightarrow SM, \ \ \theta \cdot (x,v) := (x, \theta \cdot v).$$

Recall we generally view $$S^1$$ to be the set $$[0,2\pi)$$ equipped with the group operation $$+$$ which is understood to be addition modulo $$2\pi$$. It is not hard to see it is an honest group action -- rotation by $$0$$ gives you back the same thing and if we rotate by $$\theta_0$$ and then $$\theta_1$$ it is the same thing as rotating by $$\theta_0 + \theta_1$$. It's also clear that this is going to be a free action.

Fix $$(x,v) \in SM$$ and consider $$T_{(x,v)}SM$$. Let $$\pi : SM \rightarrow M$$ be the footprint map, so $$\pi(x,v) = x$$. Notice that $$d_{(x,v)}\pi : T_{(x,v)}SM \rightarrow S_xM$$ is going to be some linear map. We can define the **vertical space at $$(x,v)$$** by

$$\mathbb{V}(x,v) := \{ \xi \in T_{(x,v)}SM : d_{(x,v)}\pi(\xi) = 0\}.$$

A **connection** $$K$$ is choice of $$2$$-dimensional subspace $$K_{(x,v)}$$ inside of $$T_{(x,v)}SM$ such that the following holds:

(1) $$T_{(x,v)}SM = K(x,v) \oplus \mathbb{V}(x,v)$$.

(2) If we interpreted $$\theta \in S^1$$ as a map $$\theta : SM \rightarrow SM$$ defined by $$\theta(x,v) = (x, \theta \cdot v), then we have $$d_{(x,v)}\theta : T_{(x,v)}SM \rightarrow T_{(x,\theta \cdot v)}SM$$ will satisfy $$d_{(x,v)}\theta(K(x,v)) = K(x, \theta \cdot v).

(3) The choice of $$K(x,v)$$ is smooth in the sense that for each $$(x,v) \in SM$$ we can find an open set $$U$$ of $$(x,v)$$ and smooth vector field $$X$$ and $$Y$$ defined on $$U$$ so that $$\{X,Y\}$$ span $$K(x,v)$$ at each point of $$U$$.

**Observation:** There is a natural choice of a smooth vector field $$V$$ on $$SM$$ such that $$V$$ spans $$\mathbb{V}(x,v)$$ at each point. If we fix $$(x,v) \in SM$$, we see that it defines a map

$$A_{(x,v)} : S^1 \rightarrow SM, \ \ A_{(x,v)}(\theta) := (x, \theta \cdot v).$$

There's also the usual unit tangent vector field on $$S^1$$ denoted by $$\frac{\partial}{\partial \theta}.$$ We define the vector field $$V$$ by

$$V(x,v) := dA_{(x,v)}\left(  \frac{\partial}{\partial \theta}\right).$$

Alternatively, we can define a flow $$\rho_t : SM \rightarrow SM$$ by

$$\rho_t(x,v) = (x, t \cdot v).$$

Then the vector field $$V$$ is defined by

$$ V(x,v) := \frac{d}{dt} \rho_t(x,v) \bigg|_{t=0}.$$

The vector field $$V$$ is called the **vertical vector field**.

The **connection form** is the $$1$$-form $$\psi$$ defined on $$SM$$ in the following way. Let $$q$$ be the projection map:

$$q_{(x,v)} : T_{(x,v)} = K(x,v) \oplus \mathbb{V}(x,v) \rightarrow \mathbb{V}(x,v).$$

Then $$\psi(x,v, \xi) := \lambda$$ where $$q_{(x,v)}(\xi) = \lambda V(x,v).$$

The following claim gives us a characterization of connection forms.

**Claim:** Suppose $$\psi$$ is a $$1$$-form on $$SM$$ so that

(1) for all $$\theta \in S^1$$, $$\theta^*(\psi) = \psi$$,

(2) $$\psi(V) \equiv 1$$,

then $$\psi$$ is the connection $$1$$-form for $$K := \psi_{(x,v)}^{-1}(0)$$.

**Proof:** We have that $$\psi_{(x,v)} : T_{(x,v)}SM \rightarrow \mathbb{R}$$, so its kernel must be two dimensional by the above. Let $$K(x,v) := \psi_{(x,v)}.$$ By rank-nullity, we get

$$T_{(x,v)}SM = K(x,v) \oplus \mathbb{V}(x,v).$$

Notice that for any $$\theta \in S^1$$ we have

$$d_{(x,v)}\theta(K(x,v)) = d_{(x,v)}\theta(\psi^{-1}(0)) = \psi^{-1}(0) = K(x,v).$$

The smoothness follows since it is a $$1$$-form. $$\blacksquare$$

Let $$U$$ be a coordinate neighborhood in $$M$$. Notice that

$$\pi^{-1}(U) = S(U) = U \times S^1.$$

Let $$\{e_1(x), e_2(x)\}$$ be the orthonormal basis for $$T_xU$$. Let $$B : U \times S^1 \rightarrow \pi^{-1}(U)$$ be the map defined by

$$B(x, \theta) := (x, \theta \cdot e_1(x)).$$

Then we define

$$K_1(x,v) := d_{(x, \theta)}B( T_{(x,\theta)}(U \times \{\theta\})), $$

where $$\theta \in S^1$$ is such that $$\theta \cdot e_1(x) = v.$$

**Claim:** We have that $$K_1$$ is a connection on $$U$$.

**Proof:** We need to show orthogonality with the vertical vector space. Notice that

$$ d_{(x,v)} \pi (K_1(x,v)) = d_{(x,\theta)} (\pi \circ B)(T_{(x,\theta)}(U \times \{\theta\}) ) = T_{(x,\theta)}(U \times \{\theta\}) \cong T_x U.$$

So this is an isomorphism and in particular we see that $$V \notin K_1$$ since $$d\pi(V) = 0$$. $$\blacksquare$$

The $$1$$-form of this connection is given by

$$\phi := (B^{-1})^*(p^*(d\theta)),$$

where $$p : U \times S^1 \rightarrow S^1$$ is the projection map and $$d\theta$$ is the $$1$$-form dual to $$\partial/\partial \theta$$. We call this the **special connection**.

**Remark:** Since there are no non-zero $$2$$-forms on $$S^1$$ we get that $$d\phi = 0$$.

Finally we need the following result.

**Lemma:** Let $$K_1, K_2$$ be two connections on $$SM$$ with connection $$1$$-forms $$\psi_1, \psi_2$$. The following hold.

(1) $$(\psi_1 - \psi_2)(V) = 0$$.

(2) $$\theta^*(\psi_1 - \psi_2) = \psi_1 - \psi_2$$ for all $$\theta \in S^1$$.

(3) $$\psi_1 - \psi_2 = \pi^*(\tau)$$ for some smooth $$1$$-form $$\tau$$ on $$M$$.

**Sketch of Proof:** We see that (1) follows since $$\psi_1(V) = \psi_2(V) = 1$$. (2) follows since pullbacks are linear. Suppose we have some form $$\kappa$$ satisfying the property that $$\kappa(V) = 0$$ and $$\theta^*(\kappa) = \kappa$$ for all $$\theta \in S^1$$. The goal is to define $$\tau$$ in the following way: taking some $$(x,v) \in TM$$, let $$(x,v_0) \in \pi^{-1}(x) \subseteq S_xM$$ be such that we can find $$w \in T_{(x,v_0)}SM$$ so that $$d_{(x,v)}\pi(w) = v$$. Define $$\tau_x(v) = \psi_{(x,v_0)}(w)$$. We claim this is well-defined. If we had some other $$w_0 \in T_{(x,v)}SM$$ so that $$d_{(x,v)}\pi(w_0) = v$$, then $$d_{(x,v)}\pi(w - w_0) = 0$$ so $$w - w_0 = \lambda V(x,v)$$, and so $$\psi_{(x,v)}(w - w_0) = 0$$. Hence the choice of representative doesn't matter here. Now suppose we had two $$(x,v_0)$$ and $$(x,v_1)$$ which satisfied this condition. Then $$v_1 = \theta \cdot v_0$$ for some $$\theta \in S^1$$. Let $$w \in T_{(x,v_0)}SM$$ be such that $$d_{(x,v_0)}\pi(w) = v_0$$. Then $$d\theta(w) \in T_{(x,v_1)}SM$$ is such that $$d(\pi \circ \theta)(w) = v_1$$, and

$$\psi_{(x,v_1)}(d\theta(w)) = \theta^*(\psi)_{(x,v_0)}(w) = \psi_{(x,v_0)}(w).$$

Thus we've constructed such a $$\tau$$. Smoothness is an easy thing to check in coordinates. $$\blacksquare$$


## Cartan's Moving (Co)frame


On our circle bundle $$SM$$ we can define two more one forms. Let

$$\alpha_{(x,v)}(\xi) := g_x( d_{(x,v)}\pi(\xi), v),$$

$$\beta_{(x,v)}(\xi) := g_x( d_{(x,v)}\pi(\xi), iv),$$

where $$iv$$ is the vector $$\pi/2 \cdot v$$; that is, the vector obtained by rotating by $$\pi/2$$.

This leads us to the following claim.

**Claim:** Suppose we have a connection $$K$$ and a connection $$1$$-form $$\psi$$. Then $$\{\alpha, \beta, \psi\}$$ forms a basis for $$T^*SM$$.

**Proof:** Since $$T_{(x,v)}^*SM$$ has dimension $$3$$, it suffices to show that $$\alpha, \beta, \psi$$ are linearly independent. We claim it suffices to show that there is no element in all kernels simultaneously. Suppose that $$\ker(\alpha) \cap \ker(\beta) \cap \ker(\psi) = \{0\}$$. To show linear independence, we need to show that we cannot find smooth functions $a,b,c : SM \rightarrow \mathbb{R}$$ so that

$$ a \alpha + b \beta + c \psi = 0.$$

Fixing $$(x,v) \in SM$$, we study the following:

$$ a(x,v) \alpha_{(x,v)} + b(x,v)\beta_{(x,v)} + c(x,v) \psi_{(x,v)} = 0.$$

To show linear independence, it suffices to show that that $$a(x,v) = b(x,v) = c(x,v) = 0$$. Choose $$\xi, \eta, \kappa$$ so that

$$d_{(x,v)}\pi(\xi) = v, \ d_{(x,v)}\pi(\eta) = iv, \ \kappa = V(x,v).$$

Then we see the following hold:

$$ \beta_{(x,v)}(\xi) = \psi_{(x,v)}(\xi) = 0,$$

$$ \alpha_{(x,v)}(\eta) = \psi_{(x,v)}(\eta) = 0,$$

$$ \alpha_{(x,v)}(\kappa) = \beta_{(x,v)}(\kappa) = 0.$$

So for example we see that

$$ a(x,v) \alpha_{(x,v)}(\xi) + b(x,v)\beta_{(x,v)}(\xi) + c(x,v) \psi_{(x,v)}(\xi) = a(x,v) = 0.$$

The others also follow from a similar argument, so we get linear independence. $$\blacksquare$$

Given a metric, we can define a connection via parallel transports. This will be the **horizontal bundle**, which can be defined in terms of covariant derivatives.
