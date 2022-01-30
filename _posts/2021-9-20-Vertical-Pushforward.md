---
layout: post
title: Vertical Pushforward
tag: geometry
categories: ["Geometry"]
---

In this post I discuss a way of pushing forward forms assuming a vertical condition.

# Set Up and Solution

This can be found as Problem 14-9 in [Lee's Smooth Manifolds](https://www.springer.com/gp/book/9781441999818).

Let $$M$$ and $$N$$ be two smooth manifolds with $$\pi : M \rightarrow N$$ a surjective submersion with connected fibers. Recall that a tangent vector $$v \in T_pM$$ is said to be **vertical** if $$d\pi_p(v) = 0$$.

The goal is to show that if $$\omega \in \Omega^k(M)$$, then there exists $$\eta \in \Omega^k(N)$$ so that $$\pi^*(\eta) = \omega$$ if and only if the following two conditions are satisfied for every $$p \in M$$, $$v \in \ker(d\pi_p)$$:

(1) $$i_v(\omega_p) = 0.$$

(2) $$i_v(d\omega_p) = 0.$$

## Solution

We first work out the implication. Suppose $$\omega = \pi^*(\eta)$$. Then

$$ i_v(\omega_p) = \pi^*(\eta)_p(v) = \eta_{\pi(p)}(d\pi_p(v)) = 0.$$

Similarly,

$$i_v(d\omega_p) = \pi^*(d\eta)_p(v, \cdot) = \pi^*(d\eta)_p(v, \cdot) = d\eta_{\pi(p)} (d\pi_p(v), \cdot) = 0.$$

Now suppose that we have the following two conditions. First assume we're working with $$\pi : \mathbb{R}^{n+m} \rightarrow \mathbb{R}^n$$ the projection map (this is actually okay to do locally by the [local submersion theorem](https://math.stackexchange.com/questions/1320102/local-submersion-theorem-differential-topology-of-guillemin-and-pollack)). The goal is to define $$\eta$$ with $$\pi^*(\eta) = \omega$$. Since we're working over $$\mathbb{R}^n$$, let's just assume that we're dealing with nice coordinates. In other words, our form $$\omega$$ looks like the sum of forms $$\omega_\alpha$$ with

$$\omega_\alpha = f_{\alpha_{1} \cdots \alpha_{k}} dx_{\alpha_{1}} \wedge \cdots \wedge dx_{\alpha_{k}},$$

where $$\alpha$$ ranges over increasing combinations of $$k$$ elements from $$\{1, \ldots, n+m\}$$. Since $$i_{v} \omega_p = 0$$ for every vertical vector, we see that this implies that if $$\alpha$$ contains any factor $$\alpha_i$$ with $$i > n$$, then $$\omega_\alpha = 0$$. Thus $$\omega$$ only consists of the sum of forms $$\omega_\alpha$$ with $$\alpha$$ ranging over increasing combinations of $$k$$ elements from $$\{1, \ldots, n\}$$. However, the functions $$f_\alpha$$ still depend on the last $$m$$ coordinates. We now use the fact that $$i_v(d\omega_p) = 0$$ to deduce that the derivative of $$f_\alpha$$ in the direction of $$x_i$$ for $$i > n$$ will be $$0$$, which implies that it only depends on coordinates $$x_i$$ for $$1 \leq i \leq n$$. Thus $$\omega$$ just looks like a form in $$\Omega^k(\mathbb{R}^n)$$. Thus this gives us our choice of $$\eta$$ so that $$\pi^*(\eta) = \omega$$. This was done locally, but as mentioned earlier we can work in coordinate charts chosen by the local submersion theorem and splice things together to get that this kind of thing holds globally.

## Remarks

The first remark to make is that this gives us a subspace $$\Omega_p^k(M) \subseteq \Omega^k(M)$$ on which we can define a pushforward $$\pi_* : \Omega_p^k(M) \rightarrow \Omega^k(N)$$. As mentioned in the post on integrating over fibers, this usually doesn't make sense, but this gives us another way of interpreting this notation.

Next, let's assume we're working with a smooth conjugacy $$h$$ between two magnetic flows on $$SM$$ and $$S'M$$, where $$M$$ some closed surface. If $$h$$ respects vertical vectors (in the sense that $$dh$$ applied to vertical vector is a vertical vector) then we get that $$h^*(\Omega_p^k(M)) = \Omega_p^k(M)$$. Since it conjugates the flows, we know that $$dh(F) = F' \circ h$$.
