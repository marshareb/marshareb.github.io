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

A **connection** $$K$$ is choice of $$2$$-dimensional subspace $$K_{(x,v)}$$ inside of $$T_{(x,v)}SM$$ such that the following holds:

(1) $$T_{(x,v)}SM = K(x,v) \oplus \mathbb{V}(x,v)$$.

(2) If we interpreted $$\theta \in S^1$$ as a map $$\theta : SM \rightarrow SM$$ defined by $$\theta(x,v) = (x, \theta \cdot v)$$, then we have $$d_{(x,v)}\theta : T_{(x,v)}SM \rightarrow T_{(x,\theta \cdot v)}SM$$ will satisfy $$d_{(x,v)}\theta(K(x,v)) = K(x, \theta \cdot v).$$

(3) The choice of $$K(x,v)$$ is smooth in the sense that for each $$(x,v) \in SM$$ we can find an open set $$U$$ of $$(x,v)$$ and smooth vector field $$X$$ and $$Y$$ defined on $$U$$ so that $$\{X,Y\}$$ span $$K(x,v)$$ at each point of $$U$$.

_____

**Observation:** There is a natural choice of a smooth vector field $$V$$ on $$SM$$ such that $$V$$ spans $$\mathbb{V}(x,v)$$ at each point. If we fix $$(x,v) \in SM$$, we see that it defines a map

$$A_{(x,v)} : S^1 \rightarrow SM, \ \ A_{(x,v)}(\theta) := (x, \theta \cdot v).$$

There's also the usual unit tangent vector field on $$S^1$$ denoted by $$\frac{\partial}{\partial \theta}.$$ We define the vector field $$V$$ by

$$V(x,v) := dA_{(x,v)}\left(  \frac{\partial}{\partial \theta}\right).$$

Alternatively, we can define a flow $$\rho_t : SM \rightarrow SM$$ by

$$\rho_t(x,v) = (x, t \cdot v).$$

Then the vector field $$V$$ is defined by

$$ V(x,v) := \frac{d}{dt} \rho_t(x,v) \bigg|_{t=0}.$$

The vector field $$V$$ is called the **vertical vector field**.

_____

The **connection form** is the $$1$$-form $$\psi$$ defined on $$SM$$ in the following way. Let $$q$$ be the projection map:

$$q_{(x,v)} : T_{(x,v)}SM = K(x,v) \oplus \mathbb{V}(x,v) \rightarrow \mathbb{V}(x,v).$$

Then $$\psi_{(x,v)}(\xi) := \lambda$$ where $$q_{(x,v)}(\xi) = \lambda V(x,v).$$

The following claim gives us a characterization of connection forms.

**Claim:** Suppose $$\psi$$ is a $$1$$-form on $$SM$$ so that

(1) for all $$\theta \in S^1$$, $$\theta^*(\psi) = \psi$$,

(2) $$\psi(V) \equiv 1$$,

then $$\psi$$ is the connection $$1$$-form for $$K := \psi_{(x,v)}^{-1}(0)$$.

**Proof:** We have that $$\psi_{(x,v)} : T_{(x,v)}SM \rightarrow \mathbb{R}$$, so its kernel must be two dimensional by the above. Let $$K(x,v) := \ker(\psi_{(x,v)}).$$ By rank-nullity, we get

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

**Claim:** Suppose we have a connection $$K$$ and a connection $$1$$-form $$\psi$$. Then $$\{\alpha, \beta, \psi\}$$ forms a basis for $$T^*SM$$. This basis is called **Cartan's moving coframe**.

**Proof:** Since $$T_{(x,v)}^*SM$$ has dimension $$3$$, it suffices to show that $$\alpha, \beta, \psi$$ are linearly independent. We claim it suffices to show that there is no element in all kernels simultaneously. Suppose that $$\ker(\alpha) \cap \ker(\beta) \cap \ker(\psi) = \{0\}$$. To show linear independence, we need to show that we cannot find smooth functions $$a,b,c : SM \rightarrow \mathbb{R}$$ so that

$$ a \alpha + b \beta + c \psi = 0.$$

Fixing $$(x,v) \in SM$$, we study the following:

$$ a(x,v) \alpha_{(x,v)} + b(x,v)\beta_{(x,v)} + c(x,v) \psi_{(x,v)} = 0.$$

To show linear independence, it suffices to show that that $$a(x,v) = b(x,v) = c(x,v) = 0$$. Choose $$\xi, \eta, \kappa$$ so that

$$d_{(x,v)}\pi(\xi) = v, \ d_{(x,v)}\pi(\eta) = iv, \ \kappa = V(x,v).$$

Then we have the following:

$$ \beta_{(x,v)}(\xi) = \psi_{(x,v)}(\xi) = 0,$$

$$ \alpha_{(x,v)}(\eta) = \psi_{(x,v)}(\eta) = 0,$$

$$ \alpha_{(x,v)}(\kappa) = \beta_{(x,v)}(\kappa) = 0.$$

For example we see that

$$ a(x,v) \alpha_{(x,v)}(\xi) + b(x,v)\beta_{(x,v)}(\xi) + c(x,v) \psi_{(x,v)}(\xi) = a(x,v) = 0.$$

The others also follow from a similar argument, so we get linear independence. $$\blacksquare$$

Given a metric we can define a connection via parallel transports. Recall that we have a **Levi-Civita** connection corresponding to our metric $$g$$, which we denote by $$\nabla$$. Note this connection apriori has nothing to do with our notion of connections above, but we'll see a bridge between the two concepts in a moment. Given a vector $$\xi \in T_{(x,v)}TM$$ we can define a curve $$c : (-\epsilon, \epsilon) \rightarrow TM$$ which is adapted to $$\xi$$, in the sense that $$c(0) = (x,v)$$ and $$\dot{c}(0) = \xi$$. Notice that we can also write $$c$$ as

$$c(t) = (\gamma(t), Z(t)),$$

where $$\gamma(t)$$ is a curve on $$M$$ and $$Z(t)$$ is a vector field along the curve $$\gamma(t)$$. We define a map

$$\mathcal{H}_{(x,v)}(\xi) := \frac{DZ}{dt}(0),$$

where $$\frac{D}{dt}$$ is the covariant derivative. This is a map $$\mathcal{H} : TTM \rightarrow TM$$ which is referred to as the **connection map**. Let

$$K(x,v) := \ker(\mathcal{H}_{(x,v)}).$$

We have the following claim.

**Claim:** $$K$$ defines a connection in the sense of subspaces.

**Proof:** There are two conditions to check for a connection. We need to check that it is complementary to the vertical subspace and that it respects the rotation map. Technically the rotation map is only defined for $$TSM$$, so we'll make a note here that everything we've done above translates to the unit tangent bundle in an analogous fashion and go from there. For the complementary part we can work with just the tangent bundle, so we'll give the more general argument.


We now check that we have $$K(x,v)$$ is complementary to $$\mathbb{V}(x,v)$$. Here we follow [Merry and Paternain](https://www.dpmms.cam.ac.uk/~gpp24/ipgd(3).pdf). The trick is to define a "complementary" map $$\mathcal{L} : TM \rightarrow TTM$$ in the following fashion. Given $$(x,v), (x,w) \in TM$$ we can define a curve $$\gamma : (-\epsilon, \epsilon) \rightarrow M$$ which is adapted to the vector $$(x,w)$$. We can then take the parallel transport of the vector $$v$$ along this curve $$\gamma$$ and this defines a vector field $$Z(t)$$. We then look at the curve

$$c(t) := (\gamma(t), Z(t)) : (-\epsilon, \epsilon) \rightarrow TM$$

and define the map

$$\mathcal{L}_{(x,v)}(w) := \dot{c}(0) \in T_{(x,v)}TM.$$

We check two conditions:

_____

(1) Notice that given $$(x,v), (x,w) \in TM$$ we get

$$ \mathcal{H}_{(x,v)} \circ \mathcal{L}_{(x,v)}(w) = \mathcal{H}_{(x,v)}(\dot{c}(0)).$$

The curve $$c$$ is a curve adapted to $$\dot{c}(0) \in T_{(x,v)}TM$$ so in particular we're taking the covariant derivative of the parallel transport when we evaluate $$\mathcal{H}_{(x,v)}(\dot{c}(0))$$. The parallel transport is defined to have $$0$$ covariant derivative, so we get

$$ \mathcal{H} \circ \mathcal{L} = 0.$$

Furthermore, suppose $$\xi \in T_{(x,v)}TM$$ is such that $$\mathcal{H}_{(x,v)}(\xi) = 0$$. This implies that if we take the curve $$c$$ adapted to it and write $$c(t) = (\gamma(t), Z(t))$$ then we have that

$$\frac{DZ}{dt}(0) = 0.$$

In particular we see $$Z$$ is a parallel transport, so we get that $$\mathcal{L}_{(x,v)}(\dot{\gamma}(0)) = \xi.$$ Thus we have a stronger statement, which is that

$$\ker(\mathcal{H}) = \text{Im}(\mathcal{L}).$$

_____

(2) Given $$(x,v), (x,w) \in TM$$ we get

$$ d_{(x,v)}\pi \circ \mathcal{L}_{(x,v)}(w) = d_{(x,v)}\pi(\dot{c}(0)) = \frac{d}{dt}( \pi \circ (\gamma(t), Z(t))) \bigg|_{t=0} = \dot{\gamma}(0) = w.$$

So we have

$$ d\pi \circ \mathcal{L} = \text{Id}.$$

_____

Let's check we have a splitting

$$ T_{(x,v)}TM = K(x,v) \oplus \mathbb{V}(x,v).$$

We use rank-nullity twice two get

$$ T_{(x,v)}TM \cong K(x,v) \oplus T_xM \cong \mathbb{V}(x,v) \oplus T_xM.$$

Notice the above tells us that $$\dim(\mathbb{V}(x,v)) = \dim(K(x,v)) = \dim(T_xM).$$ If we check that $$\mathbb{V}(x,v) \cap K(x,v) = 0$$, then a dimension argument tells us that $$\mathbb{V}(x,v) \oplus K(x,v) = T_{(x,v)}TM$$ as desired. We check this now.

Let $$\xi \in K(x,v) \cap \mathbb{V}(x,v)$$. Since $$\xi \in K(x,v)$$ we have that $$\xi = \mathcal{L}_{(x,v)}(w)$$ for some $$w \in T_xM$$ by condition (1). Now $$\xi \in \mathbb{V}(x,v)$$, so

$$d_{(x,v)}\pi \circ \mathcal{L}_{(x,v)}(w) = w = d_{(x,v)}\pi(\xi) = 0.$$

Since $$w = 0$$, we have that $$\mathcal{L}_{(x,v)}(0) = 0 = \xi,$$ so the intersection is trivial.

We now check that, after restricting things to the unit tangent bundle, $$K(x,v)$$ respects rotations. Let $$\theta \in S^1$$ define a map $$ \theta : SM \rightarrow SM$$ via rotating a vector by $$\theta$$. Let $$d\theta_{(x,v)} : T_{(x,v)}SM \rightarrow T_{(x, \theta \cdot v)}SM$$ be differential at a point $$(x,v) \in SM$$. Let $$\xi \in K(x,v)$$. We need to check that $$d_{(x,v)}\theta(\xi) \in K(x, \theta \cdot v).$$ To help with notation, let $$w := \theta \cdot v$$. Then we need to check

$$\mathcal{H}_{(x, w)}(d_{(x,v)}\theta(\xi)) = 0.$$

Let $$c : (-\epsilon, \epsilon) \rightarrow TM$$ be the curve adapted to $$\xi$$. We can write

$$c(t) = (\gamma(t), Z(t)),$$

and we see that

$$d_{(x,v)} \theta(\xi) = \frac{d}{dt} (\gamma(t), \theta \cdot Z(t)) \bigg|_{t=0}.$$

In other words, the curve adapted $$d_{(x,v)} \theta(\xi)$$ will just be $$(\gamma(t), \theta \cdot Z(t))$$. Now

$$ \mathcal{H}_{(x, w)}(d_{(x,v)}\theta(\xi)) = \frac{D(\theta \cdot Z)}{dt}(0).$$

However $$\theta$$ is an isometry, so we get

$$ \mathcal{H}_{(x, w)}(d_{(x,v)}\theta(\xi)) = \frac{D(\theta \cdot Z)}{dt}(0) = \theta \cdot \frac{DZ}{dt}(0).$$

Since we apriori know it lies in the kernel, the result follows. A dimension argument gives us the equality we need, and this finishes showing this is a connection. $$\blacksquare$$

_____

**Observation:** (1) As an aside, notice that we have

$$ d_{(x,v)}\pi : K(x,v) \rightarrow T_xM, \ \ \mathcal{H}_{(x,v)} : \mathbb{V}(x,v) \rightarrow T_xM$$

are isomorphisms.

(2) With this set up, we can also restrict to the unit tangent bundle and everything still holds up.

(3) With our decomposition

$$T_{(x,v)}TM = K(x,v) \oplus \mathbb{V}(x,v)$$

we can define the so-called **Sasaki metric** on $$TM$$ by declaring these components to be orthogonal and pulling back the metric on $$TM$$ through the isomorphisms $$d\pi$$ and $$\mathcal{H}$$. Thus the Sasaki metric is defined by

$$\langle \xi, \eta \rangle := \langle \mathcal{H}(\xi), \mathcal{H}(\eta) \rangle + \langle d\pi(\xi), d\pi(\eta) \rangle.$$

We will use the Sasaki metric to help us build a moving frame.

_____

Thus we have that $$K$$ is a connection. Furthermore we get an associated connection form $$\psi$$. As a matter of fact, we can actually explicitly describe $$\psi$$.

**Claim:** The connection form for $$K(x,v)$$ described above is given by

$$\psi_{(x,v)}(\xi) := \langle \mathcal{H}_{(x,v)}(\xi), i v \rangle.$$

**Proof:** By an earlier claim, we just need to check three conditions.

(1) This technically wasn't established as a condition in the claim, but we still need to check it in this scenario. Apriori if we take $$\xi \in K(x,v)$$ then $$\mathcal{H}_{(x,v)}(\xi) = 0$$ so $$\psi_{(x,v)}(\xi) = 0$$ and hence

$$K(x,v) \subseteq \ker(\psi_{(x,v)}).$$

By a dimension argument we see that they have to be equal. Thus if we can show that $$\psi$$ satisfies the other conditions then we get that it is a connection form for $$K$$.

(2) Let $$\theta \in S^1$$. We need to check that $$\theta^*(\psi) = \psi$$. As we observed above, we know that

$$ \theta^*(\psi)_{(x,v)}(\xi) = \psi_{(x, \theta \cdot v)}(d_{(x,v)}\theta (\xi)) = \langle \mathcal{H}_{(x,\theta \cdot v)}(d_{(x,v)}\theta(\xi)), i(\theta \cdot v) \rangle.$$

From our last proof, we also see that $$\theta$$ plays well with the connection map and it is an isometry, so

$$ \theta^*(\psi)_{(x,v)}(\xi) = \langle \theta \cdot \mathcal{H}_{(x, v)}(\xi), \theta \cdot (iv) \rangle = \langle \mathcal{H}_{(x, v)}(\xi), iv \rangle  = \psi_{(x,v)}(\xi).$$

Thus $$\theta^*(\psi) = \psi$$.

(3) We finally need to check that $$\psi(V) \equiv 1$$, where $$V$$ is the vertical vector field. Notice that

$$\mathcal{H}(V(x,v)) = \mathcal{H}\left( \frac{d}{dt} \rho_t(x,v)  \bigg|_{t=0}\right) = \frac{d}{dt} e^{it}v \bigg|_{t=0} = iv.$$

Hence

$$\psi_{(x,v)}(V(x,v)) = \langle iv, iv \rangle = 1.$$

This shows us that $$\psi$$ is a connection $$1$$-form for $$K$$. $$\blacksquare$$

With our moving coframe $$\{\alpha, \beta, \psi\}$$ on $$T^*SM$$ we'd like to build a moving frame on $$TSM$$. We can do so through the Sasaki metric. We'll say a $$1$$-form $$\delta$$ is **dual** to a vector field $$S$$ if

$$\delta_{(x,v)}(\xi) = \langle S(x,v), \xi \rangle,$$

where the metric above is the Sasaki metric.

Define a flow $$h_t : SM \rightarrow SM$$ by

$$h_t(x,v) = (\gamma_{(x, iv)}(t), Z(t)),$$

with $$Z(t)$$ the parallel transport along $$\gamma_{(x, iv)}$$. Then the **horizontal vector field** is defined by

$$H(x,v) := \frac{d}{dt} h_t(x,v) \bigg|_{t=0}.$$

**Claim:** We have that $$\alpha$$ is dual to $$X$$, $$\beta$$ is dual to $$H$$, and $$\psi$$ is dual to $$V$$.

**Proof:** Notice that

$$\alpha_{(x,v)}(\xi) = \langle d_{(x,v)}\pi(\xi), v \rangle = \langle d_{(x,v)}\pi(\xi), d_{(x,v)}\pi(X(x,v)) \rangle.$$

We also notice that

$$\mathcal{H}(X(x,v)) = 0,$$

since the parallel transport of the geodesic flow is $$0$$. Hence

$$\alpha_{(x,v)}(\xi) = \langle d_{(x,v)}\pi(\xi), d_{(x,v)}\pi(X(x,v)) \rangle + \langle \mathcal{H}_{(x,v)}(\xi), \mathcal{H}_{(x,v)}(X(x,v)) \rangle,$$

so we get they are dual. Similarly,

$$\mathcal{H}(H(x,v)) = 0,$$

so we see that

$$\beta_{(x,v)}(\xi) = \langle d_{(x,v)}\pi(\xi), d_{(x,v)}\pi(H(x,v)) \rangle + \langle \mathcal{H}_{(x,v)}(\xi), \mathcal{H}_{(x,v)}(H(x,v)) \rangle.$$

Finally

$$ \psi_{(x,v)}(\xi) = \langle d_{(x,v)}\pi(\xi), d_{(x,v)}\pi(V(x,v)) \rangle + \langle \mathcal{H}_{(x,v)}(\xi), \mathcal{H}_{(x,v)}(V(x,v)) \rangle,$$

since

$$\mathcal{H}(V(x,v)) = iv$$

as we've seen earlier. $$\blacksquare$$

We call $$\{X, H, V\}$$ **Cartan's moving frame**.

## Cartan's Structural Equations

The whole point of working with this frame is that we have a nice series of equations connecting all of our basis elements called the **structural equations**. We define these for the moving coframe first.

**Theorem:** The following equations hold:

(1) $$\psi \wedge \beta = d\alpha,$$

(2) $$\alpha \wedge \psi = d\beta,$$

(3) $$ -(K \circ \pi) \alpha \wedge \beta = d\psi$$, where $$K$$ is the **curvature** of the surface.

**Sketch of Proof:** We follow Singer and Thorpe for this proof. Let $$U$$ be a coordinate neighborhood. Let's first check that there is a nowhere vanishing $$2$$-form on $$U$$, say $$\omega$$, so that on $$U$$ we have

$$ \alpha \wedge \beta = \pi^*(\omega).$$

The trick is to observe that $$\theta^*(\alpha \wedge \beta) = \alpha \wedge \beta$$ and that $$\iota_V(\alpha \wedge \beta) \equiv 0$$. To see the first condition, notice that

$$\theta^*(\alpha)_{(x,v)}(\xi) = \langle d_{(x,v)}(\pi \circ \theta)(\xi), \theta \cdot v \rangle = \langle d_{(x,v)}\pi(\xi), \theta \cdot v \rangle.$$

Now $$\theta \cdot v$$ can be written as $$\theta \cdot v = \cos(\theta)v + \sin(\theta) iv$$, so expanding the above we have

$$ \theta^*(\alpha)_{(x,v)}(\xi) = \cos(\theta) \alpha_{(x,v)}(\xi) + \sin(\theta) \beta_{(x,v)}(\xi).$$

A similar trick gives

$$\theta^*(\beta)_{(x,v)}(\xi) = - \sin(\theta) \alpha_{(x,v)}(\xi) + \cos(\theta) \beta_{(x,v)}(\xi).$$

Thus

$$\theta^*(\alpha \wedge \beta) = \theta^*(\alpha) \wedge \theta^*(\beta) = (\cos^2(\theta) + \sin^2(\theta)) \alpha \wedge \beta = \alpha \wedge \beta.$$

The second condition follows since $$\alpha$$ and $$\beta$$ are not dual to $$V$$ and we have $$\{\alpha, \beta, \psi\}$$ forms a basis. The same kind of proof as in the lemma above establishes that we can find such a form.

Let $$\phi$$ be the special connection on $$U$$. We see that $$\psi$$ descends to a connection on $$U$$ as well. Thus by our earlier lemma and observation, we can write (on the neighborhood $$U$$)

$$d\psi = d\psi - d\phi = d(\psi - \phi) = d(\pi^*(\tau)) = \pi^*(d\tau)$$

for $$\tau$$ some smooth $$1$$-form on $$M$$. Since $$d\tau$$ is a $$2$$-form on $$U$$, there is some function $$K$$ so that $$d\tau = -K \omega$$. Hence we have

$$ d\psi = \pi^*(- K \omega) = -(K \circ \pi) \pi^*(\omega) = -(K \circ \pi) \alpha \wedge \beta.$$

This gives us equation (3). One should check that $$K$$ is the curvature, but in some sense this is how you should define the curvature. We'll leave it vague for now.

Now let's still stay restricted to our coordinate neighborhood $$U$$. Let $$e_1$$ be the unit vector corresponding to $$\frac{\partial}{\partial x}$$ and let $$e_2$$ be the unit vector corresponding to $$\frac{\partial}{\partial y}$$. Let $$\alpha'$$ be dual to $$e_1$$ under the metric and let $$\beta'$$ be dual to $$ie_1$$ under the metric. Define a map

$$c : U \rightarrow \pi^{-1}(U), \ \ c(x) = (x, e_1(x)).$$

It follows that $$d\pi \circ dc = \text{Id}$$ so

$$(c^*(\alpha))_x(v) = \langle v, e_1 \rangle = \alpha'_x(v).$$

As a consequence,

$$\alpha' \wedge \beta' = c^*(\alpha \wedge \beta) =c^*(\pi^*(\omega)) = (\pi \circ c)^*(\omega) = \omega,$$

interpreting $$\omega$$ to be restricted to $$U$$ in the last equality. Now let $$\tilde{\alpha} = \pi^*(\alpha')$$ and $$\tilde{\beta} = \pi^*(\beta')$$. It's an easy calculation to see

$$\tilde{\alpha} \wedge \tilde{\beta} = \alpha \wedge \beta$$

on $$U$$. Furthermore inside $$c(U)$$ we have $$\alpha = \tilde{\alpha}$$ and $$\beta = \tilde{\beta}$$, since

$$\alpha_x(v) e_1(x) + \beta_x(v) i e_1(x) = d_x \pi(v) = \tilde{\alpha}_x(v) e_1(x) + \tilde{\beta}_x(v) ie_1(x).$$

Observe that

$$\theta^*(\tilde{\alpha}) = \theta^* \circ \pi^*(\alpha) = (\pi \circ \theta)^*(\alpha) = \pi^*(\alpha) = \tilde{\alpha}.$$

Hence (when in the right domain)

$$\theta^*(\alpha) = \cos(\theta) \theta^*(\tilde{\alpha}) + \sin(\theta) \theta^*(\tilde{\beta}).$$

We deduce that

$$\alpha = \cos(\theta) \tilde{\alpha} + \sin(\theta) \tilde{\beta}$$

and

$$\beta = -\sin(\theta) \tilde{\alpha} + \cos(\theta) \tilde{\beta}.$$

Thus

$$d\alpha = d\theta \wedge \beta + (a \cos(\theta) + b \sin(\theta)) \alpha \wedge \beta.$$

Taking the special connection on $$U$$, we get

$$ d\alpha = \phi \wedge \beta + (a \cos(\theta) + b \sin(\theta)) \alpha \wedge \beta.$$

We can define a smooth function $$r$$ so that

$$ d\alpha = \phi \wedge \beta + r \alpha \wedge \beta.$$

A similar argument establishes that

$$ d \beta = - \phi \wedge \alpha + s \alpha \wedge \beta.$$

For arbitrary connections $$\phi_1$$ we know that $$\phi - \phi_1 = \pi^*(\tau)$$ for some smooth $$1$$-form $$\tau$$ on $$U$$ which we can write as

$$\tau = c_1 \alpha' + c_2 \beta'.$$

Hence we get that

$$\phi - \phi_1 = \pi^*(c_1 \alpha' + c_2 \beta') = f_1 \alpha + f_2 \beta,$$

where $$f_1, f_2$$ are smooth functions defined on $$\pi^{-1}(U)$$. Thus

$$\phi = \phi_1 + f_1 \alpha + f_2 \beta$$

and hence

$$ d\alpha = \phi_1 \wedge \beta + (f_1 + r) \alpha \wedge \beta, \ \ d\beta = -\phi_1 \wedge \alpha + (f_2 + s) \alpha \wedge \beta.$$

Now it's relatively clear that a connection is defined by the functions $$f_1, f_2$$, so an existence and uniqueness argument gives us that there is a *unique* connection $$\phi_1$$ which satisfies the conditions that

$$d\alpha = \phi_1 \wedge \beta, \ \ d\beta = -\phi_1 \wedge \alpha.$$

It remains to show that the connection we defined earlier satisfies these conditions. One does this with [isothermal coordinates](https://www.dpmms.cam.ac.uk/~gpp24/ipgd(3).pdf) per Merry and Paternain (the calculations get extremely tedious so we'll skip over it). $$\blacksquare$$

______

**Remark:** If one doesn't want to play with isothermal coordinates, one can just take the unique connection form we've found in our proof and use this. We then have to redefine $$V$$ via duality, but for the most part we only are using these coordinates for the structural equations so it's sufficient to play with this frame specifically.

______
