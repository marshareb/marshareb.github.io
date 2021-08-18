---
layout: post
title: Magnetic Boundary Rigidity Part 2
tag: dynamics
categories: ["Dynamics"]
---

In this post I continue the discussion from the [last post](https://marshareb.github.io/Magnetic-Boundary-Rigidity/).

# Definitions Continued

## Boundary Function

Recall that last time we defined the action functional as a function which takes curves and spits out something similar to the energy. Given a simple magnetic system $$(M,\partial M, g, \alpha)$$ this was defined by

$$ A(\gamma) := \int_0^T \| \dot{\gamma}(t)\|^2 dt - \int_\gamma \alpha.$$

We showed as well that unit speed magnetic geodesics minimize this functional, in the sense that if we take a smooth variation $$\{\gamma_s\}$$ with $$\gamma_0$$ a magnetic geodesic then we have

$$ \frac{\partial}{\partial s} A(\gamma_s) \mid_{s=0} = 0.$$

Notice that for our magnetic system if we have any two points on the boundary, say $$x, y \in \partial M$$, we can find a unique unit speed magnetic geodesic which connects them. Thus we are able to redefine the action function to be

$$ A : \partial M \times \partial M \rightarrow \mathbb{R},$$

$$ A(x,y) := A(\gamma), \text{ where } \gamma : [0,T] \rightarrow M \text{ a unit speed magnetic geodesic with } \gamma(0) = x, \ \ \gamma(T) = y.$$

Daiberkov et al refer to the action functional as **Mane's action potential** (of energy $$1/2$$), and they call the function defined on the boundary the **boundary action function.**

## Gauge Equivalent

Let $$(M, \partial M, g, \alpha)$$ and $$(M, \partial M, g', \alpha')$$ be two simple magnetic systems. We say that they are **gauge equivalent** if there exists a diffeomorphism $$f : M \rightarrow M$$ with $$f \mid_{\partial M} = \text{Id}$$ and a function $$\varphi : M \rightarrow \mathbb{R}$$ with $$\phi \mid_{\partial M} \equiv 0$$ such that

1) $$g' = f^*(g),$$

2) $$\alpha' = f^*(\alpha) + d\varphi.$$

We'll abbreviate the magnetic systems by just denoting them with their metric and $$1$$-form. Suppose we have two gauge equivalent systems $$(g, \alpha)$$ and $$(g', \alpha')$$. The question is whether or not they have the same boundary function. Let $$A$$ be the boundary function for $$(g,\alpha)$$ and $$A'$$ for $$(g', \alpha')$$. Take $$x,y \in \partial M$$. Let $$\gamma$$ be the unique unit speed magnetic geodesic connecting $$x$$ to $$y$$ with respect to the system $$(g,\alpha)$$. Then we have

$$ A(x,y) = \int_0^T \| \dot{\gamma}(t)\|^2 dt - \int_\gamma \alpha.$$

Consider the curve $$\gamma'$$ with $$f^*(\gamma') = \gamma$$. This is still a curve connecting $$x$$ to $$y$$, and we see that

$$ A(x,y) = \int_0^T \| \dot{\gamma}(t)\|^2 - \int_{\gamma'}\alpha = \int_0^T (\|\dot{\gamma'}(t)\|')^2 dt - \int_{\gamma'} (\alpha' + d\phi).$$

Since $$\phi$$ is $$0$$ on the boundary, we can simplify the above to be

$$ A(x,y) = \int_0^T \|\dot{\gamma'}(t)\|')^2 dt - \int_{\gamma'} \alpha' \geq A'(x,y).$$

A similar argument shows that $$A(x,y) \leq A'(x,y),$$ so they must be the same.

Our ultimate goal is to go the other way. Suppose we have two simple magnetic systems whose boundary functions are equivalent. Is it true that they are gauge equivalent? Before continuing on, we'll need to review one last concept.

## Normal Boundary Coordinates

Let $$(M, \partial M, g)$$ be a Riemannian manifold with boundary. Let's assume we're dealing with a surface for simplicity, so $$\partial M$$ is diffeomorphic to $$\mathbb{R}$$. Fix $$x_0 \in \partial M$$. By choosing a neighborhood $$U$$ sufficiently small around $$x_0$$ we may assume that the exponential map is a diffeomorphism from this open neighborhood to an open neighborhood around $$0$$, with $$\partial M \cap U$$ identified with $$\mathbb{R} \times \{0\}$$ and $$U \cap (\partial M)^c \subseteq \mathbb{H}^{\mathrm{o}}.$$ In other words, the boundary looks like the $$x$$-axis and all points live in the upper half space. Inside of this neighborhood, each point $$p \in U$$ has a unique unit geodesic $$\gamma$$ contained in $$U$$ which hits some unique point on the boundary, say $$z$$. We define our coordinate system as follows: let $$\psi : (U \cap \partial M) \rightarrow \mathbb{R}$$ be the projection onto the $$x$$ coordinate of the exponential map, and let $$\varphi : U \rightarrow \mathbb{R}$$ be defined by $$\varphi(p) = d(x, \partial M).$$ Extend $$\psi$$ for $$p \in U$$ by setting $$\psi(p) = \psi(z)$$, where $$z$$ is the unique point on the boundary hit by the unit speed geodesic.

This is, in some sense, the coordinates which come from the "usual" boundary exponential map, defined by $$\exp_{\partial M}(p,t) := \exp_p(t \nu(p)),$$ $$p \in \partial M$$, $$t \geq 0$$, and $$\nu(p)$$ the unique inward pointing normal vector.

Let $$f : U \rightarrow \mathbb{H}$$ denote the diffeomorphism which realizes these coordinates. We push our metric $$g$$ through $$f$$ to define a new metric $$g^*$$ with

$$g^*(p,q) = g(x,y) \text{ where } f(x) = p, \ f(y) = q.$$

We study how the metric behaves in these coordinates. Notice that geodesics are either transverse entirely to the $$x$$-axis or they live along it. This observation tells us that $$g^*_{22} = 1$$ and $$g^*_{12} = 0$$. We will in the future conflate $$g$$ and $$g^*$$.


# First Major Results

## A result on jets

This now follows Section 2.1 in [Daiberkov et al](https://arxiv.org/abs/math/0611788). Note that throughout we'll simplify things by dealing with the case of a surface instead of a general Riemannian manifold, although the arguments are essentially the same.

The first major result we are heading towards is the following.

**Theorem 2.2:** If $$(g,\alpha)$$ and $$(g', \alpha')$$ are two simple magnetic systems with the same boundary action function, then $$(g',\alpha')$$ is gauge equivalent to some $$(\bar{g}, \bar{\alpha})$$ such that in any local coordinate system and for any multi-index $$m$$ we have

$$\partial^m g \mid_{\partial M} = \partial^m \bar{g}\mid_{\partial M}$$

and

$$ \partial^m \alpha \mid_{\partial M} = \partial^m \bar{\alpha} \mid_{\partial M}.$$

Before proving this, we need the following lemma.

**Lemma 2.1:** Let $$i : \partial M \rightarrow M$$ be the embedding map. If $$(g,\alpha)$$ and $$(g', \alpha')$$ are two simple magnetic systems on $$M$$ with the same boundary action function, then

$$ i^*(g) = i^*(g') \text{ and } i^*(\alpha) = i^*(\alpha').$$

**Proof:** Fix $$x \in \partial M$$, $$\xi \in T_x(\partial M)$$, and let $$\tau(s)$$ be a curve on $$\partial M$$ with $$\tau(0) = x$$ and $$\dot{\tau}(0) = \xi$$. We claim

$$ \lim_{s \rightarrow 0} \frac{A(x, \tau(s))}{s} = \|\xi\|_g - \alpha(\xi).$$

This follows by going into coordinates defined by the magnetic exponential map. Since $$s \rightarrow 0$$, we can take it small enough so that it stays in a neighborhood, and thus we have

$$ \lim_{s \rightarrow 0} \frac{1}{s} d(x, \tau(s)) =  \|\xi\|_g.$$

A similar kind of argument works for $$\alpha$$. Since they have the same boundary action function, we get

$$ \|\xi\|_{g'} - \alpha'(\xi) = \lim_{s \rightarrow 0} \frac{A'(x, \tau(s))}{s} = \lim_{s \rightarrow 0}\frac{A(x,\tau(s))}{s} = \|\xi\|_g - \alpha(\xi).$$

Replace $$\xi$$ by $$-\xi$$ to get

$$\| \xi\|_{g'} + \alpha'(\xi) = \|\xi\|_g + \alpha(\xi).$$

Add the formulas together to get

$$2 \| \xi\|_{g'} = 2\|\xi\|_g \implies \|\xi\|_{g'} = \|\xi\|_g.$$

With this, we can deduce that $$\alpha'(\xi) = \alpha(\xi).$$ The result then follows.

Recall that a **jet** is a truncated Taylor polynomial (see [Wikipedia](https://en.wikipedia.org/wiki/Jet_(mathematics))). With the above lemma, Daiberkov et al are able to show that the boundary action determines the full jets of the metric and magnetic potential on the boundary.

**Theorem 2.2:** If $$(g,\alpha)$$ and $$(g',\alpha')$$ are simple magnetic systems on $$M$$ with the same boundary action function, then $$(g',\alpha')$$ is gauge equivalent to some $$(\bar{g}, \bar{\alpha})$$ such that in any local coordinate system and every multi-index $$m$$ we have

$$ \partial^m g \mid_{\partial M} = \partial^m \bar{g} \mid_{\partial M}$$

and

$$ \partial^m \alpha \mid_{\partial M} = \partial^m \bar{\alpha} \mid_{\partial M}.$$

Instead of proving this, we'll just discuss how the proof works. First we use the boundary exponential map $$\exp_{\partial M}(p, t) = \exp_p(t \nu(p))$$ for $$p \in \partial M, t \geq 0$$. We see that $$\exp_{\partial M} \circ (\exp_p'_{\partial M})^{-1}$$ is well-defined on a neighborhood of $$\partial M$$ in $$M$$ and is the identity restricted to $$\partial M$$. We can use a bump function to extend this to all of $$M$$. This let's us extend our metric; $$\bar{g} = f^*(g')$$. Now with the $$1$$-form we need to be a little more careful. We set $$\alpha'' = f^*(\alpha')$$, and we use Lemma 2.2 from [this](https://www.researchgate.net/publication/226079698_An_Integral_Geometry_Problem_in_a_Nonconvex_Domain) Sharafutdinov paper which says that we can find $$\varphi \in C^\infty_0(M)$$ so that $$(\alpha - \alpha'') - d\varphi$$ induces the zero form on every sufficiently short geodesic of $$\bar{g}$$ starting from $$\partial M$$ in the normal direction. We set $$\bar{\alpha} = \alpha'' + d\varphi$. The gist from here is to look at things in the boundary normal coordinates -- that is, study the function $$h = g - \bar{g}$$ and $$\beta = \alpha - \bar{\alpha}$$. Around the point $$x_0 \in \partial M$$ we can write

$$ h = \sum_{1 \leq i,j \leq n} h_{ij} dx_i dx_j, \ \ \beta = \sum_{i=1}^n \beta_i dx_i.$$

Observe that $$h_{in} = 0$$ for $$1 \leq i \leq n$$ and, when on the boundary, we have that $$\beta_1 = \beta_2 = 0$$. To show the jets are all zero, we just need to show that

$$ \partial^m h_{in} \mid_{x=x_0} = 0, \ \ \partial^m \beta_i \mid_{x=x_0} = 0$$

for $$1 \leq i \leq n-1$$ (the case of $$\beta_n$$ is trivial). We have by the above remark that the case of $$m = 0$$ is trivial, so we induct on the size of $$m$$. Looking at the Taylor expansion, if this was not the case then we would have either

$$ \frac{1}{2} h_{ij}(x) \xi^i \xi^j - \beta_i(x) \xi^i > 0 \text{ or } < 0$$

for $$x= (x_1, \ldots, x_n)$$ with $$x_n > 0$$ and $$\|(x_1, \ldots, x_{n-1})\|$$ sufficiently small, $$\xi$$ close to $$\xi_0$$ with $$\xi_0 \in T_{x_0}(\partial M)$$. Here we note that $$1 \leq i, j \leq n-1.$$ This will give us a contradiction. Look at the action functions for both $$g$$ and $$\bar{g}$$. Take a geodesic $$\bar{\gamma}$$ which minimizes the free time action for $$(\bar{g}, \bar{\alpha})$$ and connects points $$x$$ and $$y$$. Then for any curve $$\gamma$$ we have

$$A(\gamma) = \bar{A}(\bar{\gamma}) \leq \bar{A}(\gamma),$$

Using the definition, this says

$$ \int_0^T g_{ij}(\gamma(t)) \dot{\gamma}^i(t) \dot{\gamma}^j(t) dt - \int_0^T \alpha_i(\gamma(t)) \dot{\gamma}^i(t) dt \leq \int_0^T \bar{g}_{ij}(\gamma(t)) \dot{\gamma}^i(t) \dot{\gamma}^j(t) dt - \int_0^T \bar{\alpha}_i(\gamma(t)) \dot{\gamma}^i(t) dt.$$

Subtracting yields

$$\int_0^T h_{ij}(\gamma(t)) \dot{\gamma}^i(t) \dot{\gamma}^j(t) dt - \int_0^T \beta_i(\gamma(t)) \dot{\gamma}^i(t) dt \leq 0.$$

A symmetric argument gives

$$\int_0^T h_{ij}(\gamma(t)) \dot{\gamma}^i(t) \dot{\gamma}^j(t) dt - \int_0^T \beta_i(\gamma(t)) \dot{\gamma}^i(t) dt \geq 0.$$

Chose $$x = x_0$$ and choose $$y = \delta(s)$$ where $$\delta$$ a smooth curve on the boundary with $$\delta(0) = x_0$$ and $$\dot{\delta}(0) = \xi_0$$. Then we see that in light of our earlier observation the above cannot happen simultaneously, which is a contradiction.
