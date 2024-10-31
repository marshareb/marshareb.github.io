---
layout: post
title: Freire-Mane Conjecture 
tag: geometry, dynamics
categories: ["Geometry", "Dynamics"]
---

In this post, we discuss the Freire-Mane conjecture.

# Set up 

To start, let $$g$$ be a metric without conjugate points on a closed Riemannian manifold.
Denote its corresponding geodesic flow on the unit tangent bundle by $$g_t : SM \rightarrow SM.$$
Recall that the *Lyapunov exponent* of a vector $$\xi \in T_vSM$$ is the quantity

$$ \chi(v, \xi) := \limsup_{t \rightarrow \infty} \frac{1}{t} \log \| d_v g_t(\xi)\|.$$

Since the metric is without conjugate points, we can form the so-called *Green bundles.* More precisely, let $$\mathbb{V}(v) := \{\xi \in T_vSM \ | \ d_v\pi(\xi) = 0\}$$. Then it is well-known that the *stable Green bundle* is the limit:

$$ G^s(v) := \lim_{t \rightarrow \infty} d_v g_{-t}(\mathbb{V}(g_t(v))).$$

The *unstable Green bundle* is defined similarly, but in backwards time. 
In the setting of an Anosov geodesic flow, these bundles correspond to the unstable and stable bundles respectively; however, in general, they need not correspond to anything related to hyperbolic dynamics.
In fact, using a correspondence between vectors in $$T_vSM$$ and Jacobi fields along the geodesic $$\gamma_v(t) := \pi \circ g_t(v),$$ one can show that the unstable and stable Green bundles correspond to Jacobi fields which never vanish.
For the purposes of this note, we restrict our viewpoint to an oriented surface; however, these results work much more generally than this using Jacobi tensors. 

A *Jacobi field* is a vector field along $$\gamma_v(t)$$ which satisfies the so-called *Jacobi equation:*

$$ \ddot{J}(t) + R(J(t), \dot{\gamma}(t)) \dot{\gamma}(t) = 0.$$

Since we are on an oriented surface, there is a well-defined vector field $$\dot{\gamma}_v^\perp(t)$$ along $$\gamma_v(t)$$ which comes from rotating the vector by $$\pi/2$$. 
Note that $$\{\dot{\gamma}_v(t), \dot{\gamma}_v^\perp(t)\}$$ forms an orthonormal basis at $$T_{\gamma_v(t)}M$$, and so every vector field can be expressed as $$J(t) = x(t) \dot{\gamma}_v(t) + y(t) \dot{\gamma}_v^\perp(t).$$
Since we in such a nice setting, we see that the Jacobi equation transforms into a system of equations:

$$ \ddot{y}(t) + K(t) y(t) = 0, \quad \ddot{x}(t) = 0,$$

where $$K$$ is the Gaussian curvature, and $$K(t) := K(\gamma_v(t))$$. Notice that $$T_vSM$$ gets identified with the space of Jacobi fields $$(x(t), y(t))$$ where $$x(t)$$ is constant. Moreover, the flow can be pushed to this setting naturally, and we have $$d_v g_t(x(0), y(0)) = (x(t), y(t)).$$ With this in mind, the Lyapunov exponents now become 

$$\chi(v,\xi) = \limsup_{t \rightarrow \infty} \frac{1}{t} \log(C + \mid y(t) \mid) = \limsup_{t \rightarrow \infty} \frac{1}{t} \log \mid y(t) \mid.$$

Notice also that if $$\xi$$ and $$\eta$$ differ by a constant scaling, then their Lyapunov exponents are the same. 
In other words, Lyapunov exponents are well-defined on subspaces.
Hence, we can write $$\chi^{s/u}(v)$$ to be the Lyapunov exponent of the (un)stable Green bundle.

Now, one advantage of choosing a vector in the Green bundle is that the $$y$$ component never vanishes. We can then define the associated function $$r(t) = \dot{y}(t)/y(t)$$, which can also be seen as the derivative of $$\log(y(t))$$. Notice that $$r(t)$$ satisfies a *Riccati equation:*

$$\dot{r}(t) + r(t)^2 + K(t) = 0.$$

Taking advantage of this, it is not too hard to see from the fundamental theorem of Calculus that 

$$\chi^{s/u}(v) = \lim_{t \rightarrow \infty} \frac{1}{t} \int_0^t r^{s/u}(\tau) d\tau,$$

where $$r^{s/u}$$ is any choice of a solution to the Riccati equation for a vector in the stable/unstable Green bundle.
Using Oseledet's theorem, Ruelle's inequality, and the Birkhoff ergodic theorem, it follows that for any Borel measure $$\mu$$ which is invariant under the geodesic flow, we have 

$$ h_\mu(g_t) \leq \int_{SM} \chi^{u}(v) d\mu(v) = \int_{SM} r^{u}(v) d\mu(v),$$

where we define a (Borel) measurable function $$r^{u}$$ on $$SM$$ by setting $$r^{u}(v)$$ to be the corresponding Riccati equation at time zero (I am being vague, but there is a procedure that makes this all well-defined).
If one uses the variational principle here, we get 

$$ h_{\text{top}}(g) \leq \sup_\mu \int_{SM} r^{u}(v) d\mu(v).$$

This was (essentially) proven in full generality by Freire and Mane, building on the work of Hopf and Green.

# Conjecture

It is conjectured by Freire and Mane that if $$g$$ is a metric without conjugate points, then the only way that the topological entropy is zero is if the curvature is zero. If the curvature is zero, it is easy to see that the only solutions to the Jacobi equation are $$\ddot{y}(t) = 0,$$ which forces the (un)stable Riccati equations to be zero, and hence the topological entropy is zero by the above.

On the other hand, it is not so clear what you should do if you only assume the topological entropy is zero. 
For surfaces, one can use Hopf's theorem to deduce that the genus of the surface must be two if the metric is not flat. 
In this case, a result by Katok shows us that the topological entropy has to be positive, proving the contrapositive.
For higher dimensions, we lack this entropy result of Katok (at least to the best of my knowledge). 

Another way to see the contrapositive in the case of surfaces is that if the topological entropy is zero, then the volume entropy is also zero. If the volume entropy is zero, then Avez tells us that the fundamental group grows subexponentially; for surfaces, we know that this only happens for the sphere and the torus (in fact, this is one way of showing that the only surfaces that admit Anosov flows have genus at least two; see the paper by Plante and Thurston). Since the metric has no conjugate points, this rules out the sphere, and then Hopf tells us that the metric must be flat. Part of this argument still carries through to higher dimensions, but I believe there is no result that says the fundamental group grows subexponentially for the torus. Still, if one can use topological means to reduce the situation to the torus, then Burago and Ivanov's result tells us that the metric must be flat. 

It is suprising to me that there is still a gap; I suspect that this can be proven using more modern techniques.
