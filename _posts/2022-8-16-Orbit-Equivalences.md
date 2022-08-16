---
layout: post
title: Upgrading Orbit Equivalences to Conjugacies
tag: dynamics
categories: ["Dynamics"]
---

In this post, we talk about the Livsic theorem and how we can use it to upgrade orbit equivalences to conjugacies.

# Definitions

Throughout, we'll be working with smooth flows on closed manifolds, although the regularity doesn't need to be so high for many of these concepts. We want to compare flows dynamically. There are four major definitions when considering this.

1) Let $$f^t : M \rightarrow M$$ be a flow. We say that a function $$\alpha : M \times \mathbb{R} \rightarrow \mathbb{R}$$ is a **cocycle over $$f^t$$** if it satisfies the cocycle conditions:

a) $$\alpha(x,0) = 0$$,

b) $$\alpha(x, s+t) = \alpha(f^t(x), s) + \alpha(x,t)$$.

Sometime, we might include a third condition which says that $$\alpha(x,t) \geq 0$$ if $$t \geq 0$$. This is in order to make sense of orientation. Maybe a proper name for this would be orientation preserving cocycles over $$f^t$$, but as far as I know there is nothing in the literature of this form.

2) Let $$f^t, g^t : M \rightarrow M$$ be flows. We say that $$f^t$$ is a **time change** of $$g^t$$ if we have

$$f^t(x) = g^{\alpha(x,t)}(x),$$

where $$\alpha$$ is a cocycle over $$f^t$$. Notice that this saying that the orbits are the same, so this is one way of saying two flows are the same.

3) Let $$f^t : M \rightarrow M$$ and $$g^t : N \rightarrow N$$ be two flows. We say they are **orbit equivalent** if there is a homeomorphism $$h : N \rightarrow M$$ and a cocycle $$\alpha$$ over $$h^{-1} \circ f^t \circ h$$ so that

$$ f^t \circ h(x) = h \circ g^{\alpha(x,t)}(x).$$

This is not the usual definition of orbit equivalence. Usually, we just say an orbit equivalence is a homeomorphism which maps orbits bijectively onto each other. It is not too hard to see that the definitions are equivalent. This generalizes the equivalence in 2), since we don't require the orbits to actually be the same, but rather we just require the orbit structures to be the same. In other words, the orbits don't need to be in the same location or even in the same space.

4) Let $$f^t : M \rightarrow M$$ and $$g^t : N \rightarrow N$$ be two flows. We say they are **conjugate** if there is a homeomorphism $$h : N \rightarrow M$$ so that

$$ f^t \circ h = h \circ g^t.$$

In other words, they are conjugate if $$h$$ is an orbit equivalence where $$\alpha(x,t) = t$$. When we say two flows are equivalent, we usually mean this.

The final thing we need is the definition of a generator. Let $$\alpha$$ be a cocycle over $$f^t : M \rightarrow M$$. We generally assume enough regularity on $$\alpha$$ so that it is differentiable along the flow, meaning that it is differentiable in the $$t$$-direction. This is okay to do in the cases we care about for this post, see Chapter 19 of Katok and Hasselblatt for details. In this case, the function $$a : M \rightarrow \mathbb{R}$$ defined by

$$a(x) := \frac{d}{dt} \alpha(x,t) \Big|_{t=0}$$

is called the **generator** for the cocycle. Notice that we are able to recover the cocycle from the generator. In other words, we have

$$\alpha(x,t) = \int_0^t a(f^t(x)) dt.$$

# Upgrading Orbit Equivalences

The goal of this article is to figure out when we can upgrade orbit equivalences to conjugacies. We start by observing the following.

**Claim 1:** Let $$\beta : M \rightarrow \mathbb{R}$$ be a continuous function. Then

$$\alpha(x,t) := \beta(f^t(x)) - \beta(x)$$

is a cocycle over $$f^t$$.

**Proof:** The first condition is easy to see:

$$ \alpha(x,0) = \beta(f^0(x)) - \beta(x) = \beta(x) - \beta(x) = 0.$$

The second condition is also fairly easy to see:

$$\alpha(x, t+s) = \beta(f^{t+s}(x)) - \beta(x) = \beta(f^{t+s}(x)) - \beta(f^t(x)) + \beta(f^t(x)) - \beta(x) = \beta(f^{s}(f^t(x))) - \beta(f^t(x)) + \beta(f^t(x)) - \beta(x) = \alpha(f^t(x), s) + \alpha(x,t).$$

This concludes the proof. $$\blacksquare$$

We call cocycles which satisfy this condition **coboundaries**.

**Claim 2:** Let $$f^t : M \rightarrow M$$ be a flow, $$\alpha$$ a cocycle over $$f^t$$. The map $$\gamma(x,t) := \alpha(x,t) - t$$ is a cocycle over $$f^t$$.

**Proof:** The first condition is, again, easy:

$$\gamma(x,0) = \alpha(x,0) - 0 = 0.$$

The second condition follows:

$$ \gamma(x, t+s) = \alpha(x, t+s) - (t+s) = \alpha(f^t(x), s) + \alpha(x,t) - t - s = [\alpha(f^t(x), s) - s] + [\alpha(x,t) - t] = \gamma(f^t(x), s) + \gamma(x,t).$$

This concludes the proof. $$\blacksquare$$

**Remark:** The set of cocycles forms a vector space over $$\mathbb{R}$$, so another proof of this claim is to use this.

**Claim 3:** Suppose $$f^t, g^t : M \rightarrow M$$ are flows, $$f^t$$ a time change of $$g^t$, $$\alpha$$ a cocycle over $$f^t$$ such that

$$ f^t(x) = g^{\alpha(x,t)}(x).$$

If $$\gamma(x,t) := \alpha(x,t) - t$$ is a coboundary with

$$\gamma(x,t) = \beta(x) - \beta(f^t(x)),$$

then $$q : M \rightarrow M$$ defined by

$$q(x) := g^{\beta(x)}(x)$$

satisfies

$$ q \circ f^t(x) = g^t \circ q(x).$$

**Proof:** We have

$$q \circ f^t(x) = g^{\beta(f^t(x))}(f^t(x)).$$

Since

$$f^t(x) = g^{\alpha(x,t)}(x),$$

we substitute this in to get

$$q \circ f^t(x) = g^{\beta(f^t(x))}(f^t(x)) = g^{\beta(f^t(x))}( g^{\alpha(x,t)}(x)) = g^{\beta(f^t(x)) + \alpha(x,t)}(x).$$

Now, we have

$$\alpha(x,t) - t = \beta(x) - \beta(f^t(x)),$$

so

$$\alpha(x,t) + \beta(f^t(x)) = \beta(x) + t.$$

We use this to rewrite the above as

$$ q \circ f^t(x) = g^{\beta(f^t(x)) + \alpha(x,t)}(x) = g^{\beta(x) + t}(x) = g^t(g^{\beta(x)}(x)) = g^t \circ q(x).$$

Thus we have $$f^t$$ is conjugate to $$g^t$$ through $$q$$. $$\blacksquare$$

The last thing we need is the Livsic theorem. We recall it now.

**Theorem:** Let $$f^t : M \rightarrow M$$ be a transitive Anosov flow with infinitesmal generator $$X$$. Let $$p : M \rightarrow \mathbb{R}$$ be a Holder continuous function such that for each $$x \in M$$ with $$f^T(x) = x$$ we have

$$ \int_0^T p(f^t(x)) dt = 0.$$

Then there is a Holder continuous function $$u : M \rightarrow \mathbb{R}$$ which is differentiable along the flow such that

$$p = X(u).$$

**Remark:** By the work of de La Llave, Marco, and Moriyon, we actually have that this theorem holds for higher regularity. This means that if $$p$$ is either $$C^1$$ or smooth, then $$u$$ will also be $$C^1$$ or smooth. This is referred to as the smooth Livsic theorem.

Now let's put it all together.

**Claim 4:** Suppose $$f^t : M \rightarrow M$$ and $$g^t : N \rightarrow N$$ are orbit equivalent transitive Anosov flows, so there is an $$h : N \rightarrow M$$ and a cocycle $$\alpha$$ over $$f^t$$ so that

$$ h^{-1} \circ f^t \circ h(x) = g^{\alpha(x,t)}(x).$$

Suppose that for every $$x \in M$$ satisfying $$f^T(x) = x$$ we have $$\alpha(h^{-1}(x),T) = T$$ -- in other words, lengths of corresponding periodic orbits are the same. Then we can find a $$q : N \rightarrow M$$ so that

$$ q^{-1} \circ f^t \circ q(x) = g^t(x).$$

In other words, we have that $$f^t$$ and $$g^t$$ are actually conjugate.

**Proof:** Write

$$\psi^t(x) := h^{-1} \circ f^t \circ h(x).$$

Then $$\psi^t : N \rightarrow N$$ is a time change of $$g^t$$. Let

$$\gamma(x,t) := \alpha(x,t) - t.$$

If $$a$$ generates $$\alpha(x,t)$$ and $$g$$ generates $$\gamma(x,t)$$, then we have the relationship

$$g = a - 1.$$

Our assumption on lengths of corresponding periodic orbits can be translated to the following: for every $$x \in N$$ with $$\psi^T(x) = x$$, we have $$\alpha(x,T) = T$$. This tells us that

$$ \int_0^T g(\psi^t(x)) dt = \gamma(x,T) = \alpha(x,T) - T = 0.$$

Hence we see that there is a $$\beta : N \rightarrow \mathbb{R}$$ such that

$$ \alpha(x,t) - t = -\beta(\psi^t(x)) + \beta(x).$$

Here, we're using the Livsic theorem and replacing the result we get from the Livsic theorem with its negative. Now we use Claim 2 to get a homeomorphism $$r : N \rightarrow N$$ so that

$$ r^{-1} \circ \psi^t \circ r = g^t.$$

Let $$q = h \circ r : N \rightarrow M$$. Then we have

$$ q^{-1} \circ f^t \circ q = r^{-1} \circ \psi^t \circ r = g^t.$$

This tells us that $$f^t$$ is conjugate to $$g^t$$. $$\blacksquare$$
