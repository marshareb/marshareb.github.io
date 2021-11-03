---
layout: post
title: Partially Hyperbolic Example
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss fibered partially hyperbolic diffeomorphisms.

# Definitions

For this example we'll be using a strong definition for partial hyperbolicity. Recall that if $$V$$ is a normed vector space and $$L : V \rightarrow V$$ is linear then we can define two quantities: the **norm,** which is given by

$$ \|L\| := \sup \left\{\frac{\|Lv\|}{\|v\|} : v \neq 0 \right\},$$

and the **conorm**, which is given by

$$ m(L) := \inf \left\{\frac{\|Lv\|}{\|v\|} : v \neq 0 \right\}.$$

Observe that

$$ 1 = \|L \circ L^{-1}\| \leq \|L\| \|L^{-1}\|,$$

so in particular we have

$$ m(L)^{-1} \leq \|L^{-1}\|.$$

Let $$M$$ be a compact Riemannian manifold. We say that a map $$f : M \rightarrow M$$ is **partially hyperbolic** if there are constants

$$ 0 < \lambda_1 \leq \mu_1 < \lambda_2 \leq \mu_2 < \lambda_3 \leq \mu_3$$

with $$\mu_1 < 1 < \lambda_3$$ and an invariant splitting

$$TM = E^s \oplus E^c \oplus E^u$$

with

$$ \lambda_1 \leq m(D_xf \mid_{E^s}) \leq \|D_xf \mid_{E^s}\| \leq \mu_1,$$

$$ \lambda_2 \leq m(D_xf \mid_{E^c}) \leq \|D_xf \mid_{E^c}\| \leq \mu_2,$$

$$ \lambda_3 \leq m(D_xf \mid_{E^u}) \leq \|D_xf \mid_{E^u}\| \leq \mu_3.$$

We call $$E^s$$ the **stable** distribution, $$E^u$$ the **unstable** distribution, and $$E^c$$ the **center** distribution.

**Remarks:** (1) Much like with hyperbolicity, there's a way to make sense of this on invariant sets $$\Lambda$$ and also a way to define this in terms of sets, but we'll avoid this technicality for now.

(2) This definition is independent of norm by compactness.


Recall that a **fiber bundle** is a tuple $$(E, M, F, \pi)$$ (sometimes denoted $$\pi : E \rightarrow M$$) which satisfies the property that $$E$$, $$F$$, and $$M$$ are topological spaces, and $$\pi$$ is a continuous surjection which is **locally trivial**. Recall that locally trivial just means that around each $$x \in M$$ there is a neighborhood $$U \subseteq M$$ so that $$\pi^{-1}(U) \cong U \times F$$. We call $$F$$ the **fiber** (hence the name).

# Example

## Set Up

The goal of this is to show that if we have a fiber bundle $$\pi : E \rightarrow M$$ with fibers $$F$$, we have a partially hyperbolic $$f : M \rightarrow M$$, and we have a lift $$F : E \rightarrow E$$ so that we have

$$ \max_{x \in M} \|D_x f \mid_{E^s(x)}\| < \min_{x \in M} \min_t m(D_t F_x) \leq \max_{x \in M} \max_t \| D_t F_x\| <\min_{x \in M} m(D_xf \mid_{E^u(x)}),$$

then we get that $$F$$ is also partially hyperbolic. The key to understanding this example is going to be the so-called **cone-criterion.**

## Cone Criterion

Let $$V$$ be a vector space with an inner product $$\langle \cdot, \cdot \rangle$$. We can define the **angle** between two vectors by

$$\theta(v,w) := \frac{\langle v,w \rangle}{\|v\|\|w\|}.$$

The intuition comes from the dot product -- recall that

$$ v \cdot w = \|v\| \|w\| \cos(\theta),$$

so this isolates $$\cos(\theta)$$. Really we should be applying an $$\arccos$$ to our value to get the angle, but to some degree this is good enough to measure angles.

With this in mind, given a subspace $$W \subseteq V$$ we can define the angle between the subspace and a vector $$v \in V$$ by setting

$$\theta(v,W) := \inf\{ \theta(v,w) : w \in W\}.$$

We define the **$$\alpha$$-cone** to be the set of vector in $$V$$ satisfying the following condition:

$$C(W, \alpha) := \{v \in V : \theta(v,W) < \alpha \}.$$

In the same way, we can define this on tangent spaces. Given a distribution $$E \subseteq TM$$ we can define the **cone** with respect to $$E$$ and some angle $$\alpha$$ by setting

$$C(x, E, \alpha) := \{v \in T_xM : \theta(v,E) < \alpha\}.$$

Cones are useful objects for identifying hyperbolicity (and really for identifying dominated splittings). This is highlighted in the following proposition.

**Proposition:** A map $$f : M \rightarrow M$$ is partially hyperbolic if and only if there are families of stable, unstable, center-stable, and center-unstable cones defined by

$$C^{\sigma}(x, \alpha) := C(x, E^{\sigma}(x), \alpha), \ \ \sigma \in \{s, u, cs, cu\}$$

and constants $$0 < \mu_1 < \lambda_2 \leq \mu_2 < \lambda_3$$ with $$\mu_1 < 1 < \lambda_3$$ satisfying the following conditions:

(1) $$D_xf^{-1}(C^s(x,\alpha)) \subseteq C^s(f^{-1}(x), \alpha),$$

(2) $$D_xf^{-1}(C^{cs}(x,\alpha)) \subseteq C^{cs}(f^{-1}(x), \alpha),$$

(3) $$D_xf^(C^u(x,\alpha)) \subseteq C^u(f(x), \alpha),$$

(4) $$D_xf(C^{cu}(x,\alpha)) \subseteq C^{cu}(f^{-1}(x), \alpha),$$

(5) $$\|D_xf \mid_{C^s(x,\alpha)}\| \leq \mu_1,$$

(6) $$\|D_xf \mid_{C^{cs}(x,\alpha)}\| \leq \mu_2,$$

(7) $$m(D_xf \mid_{C^u(x,\alpha)}) \geq \lambda_3,$$

(8) $$m(D_xf \mid_{C^{cu}(x,\alpha)}) \geq \lambda_2.$$

## Fibered Partially Hyperbolic Maps

With this, we have the ingredients to establish our result. Since our original system is partially hyperbolic, we already have all of the cones for said system. The idea is to lift them to the fiber bundle in a coherent way. A natural guess is to try something like

$$ \tilde{C}^\sigma(x,t, \alpha) := \{ (v,0) \in T_{x,t}E : \theta(v, E^\sigma) < \alpha\}, \ \ \sigma \in \{s, u\},$$

$$ \tilde{C}^\sigma(x,t, \alpha) := \{ (v,w) \in T_{x,t}E : \theta(v, E^\sigma) < \alpha\}, \ \ \sigma \in \{cs, cu\}.$$

Here $$\theta$$ is with respect to the space downstairs and viewing $$v$$ as living in $$T_xM$$. We're also assuming a nice metric on $$E$$ already, which is we're assuming a box metric with whatever metric was given on $$F$$ and with the metric from $$M$$. This assumption is fine to make, since partial hyperbolicity is independent of the choice of metric and so it suffices to just find one that works.

### Checking the Stable Cone

Take $$(v,w) \in \tilde{C}^s(x,\alpha)$$. Observe that

$$ D_{(x,t)}F^{-1}(v,0) = (D_xf^{-1}(v), D_t F_x^{-1}(0)) = (D_xf^{-1}(v), 0).$$

Since the angle only really cares about the first component anyways, it follows by the result in $$T_xM$$ that we have

$$D_{(x,t)}F^{-1}(\tilde{C}^s(x,t,\alpha)) \subseteq \tilde{C}^s(F^{-1}(x,t), \alpha).$$

Next let's check the constant. Let $$(v,w) \in \tilde{C}^s(x,\alpha)$$ again. Apriori we know that

$$ \|D_xf(v)\| \leq \mu_1.$$

Now notice that

$$ \|D_{(x,t)} F(v,0)\| = \|D_xf(v)\| + \|D_t F_x(0)\| \leq \mu_1 < 1.$$



### Checking the Unstable Cone


Take $$(v,0) \in \tilde{C}^u(x,\alpha)$$. Observe that

$$ D_{(x,t)}F(v,0) = (D_xf(v), D_t F_x(0)) = (D_xf(v), 0).$$

Since the angle only really cares about the first component anyways, it follows by the result in $$T_xM$$ that we have

$$D_{(x,t)}F(\tilde{C}^u(x,\alpha)) \subseteq \tilde{C}^u(F(x,t), \alpha).$$

Next let's check the constant. Let $$(v,0) \in \tilde{C}^u(x,\alpha)$$ again. Apriori we know that

$$ \|D_xf(v)\| \geq \lambda_3 > 1.$$

Now notice that

$$ \|D_{(x,t)} F(v,0)\| = \|D_xf(v)\| + \|D_t F_x(0)\| = \|D_xf(v)\| \geq \lambda_3.$$

Thus we see that

$$m(D_xF \mid_{\tilde{C}^s(x,\alpha)}) \geq \lambda_3 > 1.$$


### Checking the Center-Stable Cone

Now take $$(v,w) \in \tilde{C}^{cs}(x,\alpha)$$. Observe that since the angle only cares about the first component anyways we have

$$D_{(x,t)}F^{-1}(\tilde{C}^{cs}(x,\alpha)) \subseteq \tilde{C}^{cs}(F^{-1}(x,t), \alpha).$$

We now check the constant. Let $$(v,w) \in \tilde{C}^{cs}(x,\alpha)$$. Apriori we know that for any $$v \in E^{cs}$$ we have

$$ \|D_xf(v)\| \leq \mu_2 \|v\|.$$

Now notice that

$$ \|D_{(x,t)} F(v,w)\| = \|D_xf(v)\| + \|D_t F_x(w)\| \leq \mu_2\|v\| + \|D_t F_x(w)\| \leq \|D_tF_x\| (\|v+w\|).$$

In particular, on unit vectors, we get

$$ \|D_{(x,t)} F(v,w)\| \leq \|D_tF_x\|.$$


### Checking the Center-Unstable Cone

Now take $$(v,w) \in \tilde{C}^{cu}(x,\alpha)$$. Observe that since the angle only cares about the first component anyways we have

$$D_{(x,t)}F(\tilde{C}^{cu}(x,\alpha)) \subseteq \tilde{C}^{cu}(F(x,t), \alpha).$$

We now check the constant. Let $$(v,w) \in \tilde{C}^{cu}(x,\alpha)$$. Apriori we know that for any $$v \in E^{cu}$$ we have

$$ \|D_xf(v)\| \geq \lambda_2 \|v\|.$$

Now notice that

$$ \|D_{(x,t)} F(v,w)\| = \|D_xf(v)\| + \|D_t F_x(w)\| \geq \lambda_2\|v\| + \|D_t F_x(w)\| \geq m(D_tF_x) (\|v+w\|).$$

In particular, on unit vectors, we get

$$ \|D_{(x,t)} F(v,w)\| \leq m(D_tF_x).$$

### Putting it All Together

We've checked all of the necessary conditions for our families of cones except for the relationship of constants. Notice that we have $$\mu_1 < 1 < \lambda_3$$ still. By shrinking $$\alpha$$ as necessary, we can get $$\mu_1$$ arbitrarily close to

$$ \max_{x \in M} \|D_x f \mid_{E^s(x)}\|$$

and likewise we can get $$\lambda_3$$ arbitrarily close to

$$ \min_{x \in M} m(D_xf \mid_{E^u(x)}).$$

Consequently we can choose $$\alpha$$ small enough so that

$$ 0 < \mu_1 < \min_{x \in M} \min_{t} m(D_tF_x) \leq \max_{x \in M} \max_{t} \|D_tF_x\| < \lambda_3.$$

This satisfies all of the conditions and so by the cone criterion we have that $$F$$ must be partially hyperbolic as well.

**Remark:** Using a uniqueness result, one can see that if $$TE = \tilde{E}^s \oplus \tilde{E}^c \oplus \tilde{E}^u$$ then we have that $$\tilde{E}^c = d\pi^{-1}(E^c)$$. In particular, we get that $$TN \subseteq \tilde{E}^c$$.

## Applications

With this fibered result, we now give some examples.

(1) (Direct Products) Let $$f : M \rightarrow M$$ be a hyperbolic diffeomorphism (one can also do partially hyperbolic).Let $$g : N \rightarrow N$$ be a diffeomorphism satisfying

$$ \max_{x \in M} \|D_xf \mid_{E^s(x)}\| < \min_{x \in N} m(D_yg) \leq \max_{x \in N} \|D_yg\| < \min_{x \in M} m(D_xf \mid_{E^u(x)}).$$

Then the direct product $$F : M \times N \rightarrow M \times N$$ defined by $$F(x,y) = (f(x), g(y))$$ will be partially hyperbolic by the above result (we can define a fiber bundle taking the product and letting the fibers be $$N$$). For a particular example, take any hyperbolic map and $$g$$ a rotation of $$S^1$$.

(2) (Skew Products) Let $$f : M \rightarrow M$$ be a hyperbolic diffeomorphism (one can also do partially hyperbolic). Let $$g : M \rightarrow \text{Diff}(N)$$ be a family of embeddings which satisfies the following:

$$ \max_{x \in M} \|D_xf \mid_{E^s(x)}\| < \min_{x \in M} \min_{y \in N} m(D_yg_x) \leq \max_{x \in M} \max_{y \in N} \|D_yg_x\| < \min_{x \in M} m(D_xf \mid_{E^u(x)}).$$

In the same way this skew product will be partially hyperbolic since we can form a fiber bundle via this skew product.

(3) (Frame Flows) Let $$N$$ be some closed oriented manifold of negative sectional curvature. Let $$M = SN$$ be the unit tangent bundle of $$N$$. Let $$K$$ be the space of positively oriented orthonormal $$n$$-frames in $$TM$$ (this is essentially collections of orthonormal unit vectors which are oriented correctly). This gives rise to a fiber bundle $$\pi : K \rightarrow M$$ via taking a frame to its first vector. The fibers will be $$SO(n-1)$$ (since rotating a frame and keeping the first vector fixed preserves the fiber). The frame flow is defined by mapping the first vector along the corresponding geodesic flow and taking parallel transports of the remaining vectors. Notice there is a semiconjugacy from this flow to the geodesic flow, whose time $$t$$ map is partially hyperbolic. We can apply the above result to get that the time $$t$$ map of the frame flow is also partially hyperbolic.
