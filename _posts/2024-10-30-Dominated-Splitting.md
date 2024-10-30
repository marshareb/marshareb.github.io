---
layout: post
title: Flows with Dominated Splittings
tag: geometry, dynamics
categories: ["Geometry", "Dynamics"]
---

In this post, we discuss a question about flows with dominated splittings.

# Set up and main question

Let $$M$$ be a smooth manifold. Recall that a flow $$\varphi_t : M \rightarrow M$$ with infinitesimal generator $$X$$ has a *dominated splitting* if there exists constants $C > 0$, $$\rho \in (0,1)$$, and a continuous flow-invariant subbundles $$E,F$$ such that $$TM = E \oplus \mathbb{R} X \oplus  F$$ and such that 

$$ \| D \varphi_t |_{E(v)}\| \cdot \| D \varphi_{-t}|_{F(\varphi_t(v))} \| \leq C \lambda^t \text{ for all } v \in M \text{ and } t \geq 0.$$

It is clear that flows which are Anosov have a dominated splitting, but flows which just exhibit the dominated splitting condition are not as well-understood. In the case where $$\dim(M) = 3$$, it is immediate that at least one of the bundles has exponential behavior at any given point. However, it is not as clear as to whether this behavior is constant, or what can even be said about the behavior of the other bundle at a given point. Furthermore, it is not even clear as to what can be said about the topology of manifolds that admit flows with dominated splittings. For example, one question that is open to my best knowledge is the following:

**Question:** Does there exist a flow on the unit tangent bundle of the sphere which has a dominated splitting?

I would wager that the answer to this question is no, but it is entirely possible that I am wrong. We say that the flow has an *exponential dominated splitting* if both bundles exhibit exponential behavior. Notice that this implies that the bundle $$F$$ grows faster than the bundle $$E$$, but it is possible that the bundle $$E$$ is growing or decaying exponentially fast as well. One can easily show using the arguments from [here](http://www.pdmi.ras.ru/~svivanov/papers/bbi-parthyp.pdf) to establish the following:

**Observation:** If the manifold $$M$$ has trivial first homology, then there are no flows on which have an exponential dominated splitting.

For example, this says that there are no flows on the unit tangent bundle of the sphere which have an exponential dominated splitting. As a follow up, it is still unclear whether there exists a flow on the unit tangent bundle of the sphere for which one bundle has exponential behavior and the other one has subexponential behavior. It is possible that one can construct this using a thermostat. Furthermore, even assuming that this is impossible, one can imagine a case where the bundles switch behaviors at points; this has to also be ruled out somehow.