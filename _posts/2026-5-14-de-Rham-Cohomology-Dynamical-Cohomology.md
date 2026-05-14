---
layout: post
title: Dynamical cohomology and de Rham cohomology
tags:
  - dynamics
  - geometry
categories:
  - Dynamics
  - Geometry
---

In this post, we explore how dynamical cohomology and de Rham cohomology interact.

# Problem and Solution


Let $X^t : M \rightarrow M$ be a transitive Anosov flow, let $\theta$ be any $1$-form on $M$, let $u$ be a smooth function on $M$, and suppose that 

$$ \mathcal{L}_X\theta = du.$$

One interesting question is whether this implies that $u$ has to be a coboundary. Recall that $u$ is a *dynamical coboundary* if there is a smooth function $w$ such that $\mathcal{L}_X w = u$. 

We have the following as a preliminary observation.

**Claim:** We have $\iota_X d\theta = 0$.

**Proof:** Using Cartan's magic formula, recall
$$ \iota_X d \theta + d \iota_X \theta = du.$$
Let $\theta_X := \iota_X \theta$ be a smooth function on $M$. Contracting both sides with $X$ yields
$$ \mathcal{L}_X \theta_X = \mathcal{L}_Xu \implies \mathcal{L}_X(\theta_X - u) = 0.$$
Since $X^t$ is transitive, let $x \in M$ have a dense orbit. Observe that for all $T \geq 0$, 
$$  0 = \int_0^T \mathcal{L}_X(\theta_X - u)(X^t(x))\,dt = (\theta_X - u)(X^T(x)) - (\theta_X - u)(x).$$
In particular, this shows that for some $C \in \mathbb{R}$, we have
$$ \theta_X = u + C.$$
Now apply the exterior derivative to both sides:
$$ d \theta_X = d \iota_X \theta = du = \iota_X d\theta + d \iota_X \theta.$$
After rearranging, the result follows. $\square$

This is reminiscent of a Reeb like property. In light of this, we construct two counterexamples.

**Claim:** There are examples where $\mathcal{L}_X \theta = du$ and yet $u$ is not a dynamical coboundary.

**Proof:** The first example is the trivial one. Simply take $\theta = 0$, and note that any constant function does the trick. One may suspect that $u$ has to be an *almost coboundary* from this, i.e., there exists a smooth function $w$ such that $\mathcal{L}_X w = u + C$ for some $C \in \mathbb{R}$. The next example shows that this is also not the case.

Now, assume that $X^t$ is a Reeb flow associated to a contact form $\theta$, let $\beta$ be any closed $1$-form on $M$, and define $u := \iota_X \beta.$ We see that 
$$ \mathcal{L}_X(\theta + \beta) = d \iota_X \beta = du.$$
Notice that for all closed orbits $\gamma$, we have
$$ \int_\gamma u = \int_\gamma \iota_X \beta. $$
In particular, the right hand side depends on the homology class of $\gamma$. If $\dim(M) = 3$, the flow is homologically full, and hence there is an orbit where the RHS is non-zero. $\square$ 

From these examples, we see that one has to weaken the question considerably. This leaves us with the following question. In fact, the following is an immediate corollary of the above and the Livshits theorem.

**Claim:** Suppose that $\mathcal{L}_X \theta = du$. We have that $u$ is an almost coboundary if and only if $\iota_X \theta$ is an almost coboundary.

