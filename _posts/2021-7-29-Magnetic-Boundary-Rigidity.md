---
layout: post
title: Magnetic Boundary Rigidity Part 1
tag: dynamics
categories: ["Dynamics"]
---

In this post, I begin discussing the magnetic boundary rigidity problem, following [this](https://arxiv.org/abs/math/0611788) paper by Dairbekov, Paternain, Stefanov, and Uhlmann.

# Definitions

## Simple Magnetic System

This section follows Chapter 2 of [Merry and Paternain's notes](https://www.dpmms.cam.ac.uk/~gpp24/ipgd(3).pdf) and Section 1 of [Daiberkov et al](https://arxiv.org/abs/math/0611788).

The ultimate question behind the boundary rigidity program is the following: Given a Riemannian manifold with boundary and two metric $$g_1, g_2$$, we can study their **boundary distance functions** $$d_1, d_2$$ which are defined to be the restriction of the usual distance function to the boundary. Is it true that if these are equal, then the metrics are isometric? Taking the question at face value, the answer is no. An easy enough example is to just take the disc in $$\mathbb{R}^n$$ and on a small open neighborhood of the origin define two metrics which are very big on this open set. Then every geodesic is going to avoid this open set, so therefore the two metrics will agree on the boundary, however they are clearly two different metrics on the open set so they cannot be isometric.

With a slight modification, it turns out that the problem reaches a doable point. We say that $$(M, \partial M, g)$$ is a **simple manifold** if two conditions are satisfied:

1) The exponential map is everywhere a diffeomorphism.

2) $$\partial M$$ is **strictly convex** in the sense that the **second fundamental form** $$S$$ satisfies the following on $$\partial M$$:

$$ S_x(u,w) \geq 0 \text{ with equality if and only if } u =w.$$

Recall that the second fundamental form is defined as follows. Take the vector field $$\nu : \partial M \rightarrow T_{\partial M}M$$ which sends a point to the **unit inward pointing normal**. That is, it takes it to the unique vector $$v$$ with $$v \in T_x^\perp \partial M$$ and $$\|v\| = 1.$$ Then the second fundamental form is the map

$$S : T \partial M \times T \partial M \rightarrow \mathbb{R}, \ \ S_x(u,w) := - \langle \nabla_u \nu(x), w \rangle.$$


In dimension two, it has been shown by Pestov and Uhlmann that simple manifolds are **boundary rigid** within the class of simple metrics, meaning that if two simple metrics agree on the boundary, then they are isometric. The goal of the magnetic boundary rigidity problem is to try to translate this problem to be in terms of magnetic flows instead of geodesic flows.

The first step is to try to translate the conditions for a simple manifold to be in terms of a magnetic flow. [Recall](https://marshareb.github.io/Magnetic-Flows/) that a magnetic flow is given in terms of the tuple $$(M, g, \sigma)$$, where $$\sigma$$ is a closed $$2$$-form on $$M$$. We'll fix the tuple $$(M, g, \sigma)$$ to be our magnetic system unless otherwise stated. The magnetic flow will be denoted by $$\psi^t$$. Daiberkov et al define $$\partial M$$ to be **strictly magnetic convex** if we have

$$ S_x(v,\nu(x)) > \sigma_x(v, \nu(x)).$$

They also define the **magnetic exponential map** at $$x$$ to be the map satisfying the following:

$$\exp^\mu_x : T_x M \rightarrow M, \ \ \exp_x^\mu(t v) = \pi \circ \psi^t(v), \ t \geq 0, x \in T^1_xM.$$

Thus we define the system $$(M, \partial M, g, \sigma)$$ to be **simple** if two conditions are satisfied:

1) $$\exp_x^\mu$$ is a diffeomorphism everywhere.

2) $$\partial M$$ is strictly magnetic convex.

**Remark:** Just like in the usual simple manifold case, we have that if the above two conditions are satisfied then $$M$$ is diffeomorphic to the unit ball in $$\mathbb{R}^n.$$ Thus we have that $$\sigma$$ is in fact an exact form. In this case, we have an **exact magnetic system** with $$d \alpha = \sigma$$, and we'll sometimes write $$(M, g, \alpha)$$ to denote the system.

## Free Time Action

A significant tool in the study of the boundary rigidity problem is the **energy functional**. Given a curve $$\gamma : [a,b] \rightarrow M$$, the energy functional is defined as

$$E(\gamma) := \int_a^b \|\dot{\gamma}(t)\|^2 dt.$$

To see the power behind the energy functional, let's work with the following simplified version of the boundary rigidity problem. Let $$\{g_s : s \in (-\epsilon, \epsilon)\}$$ be a family of simple metrics for $$(M, \partial M)$$ with negative sectional curvature. Let $$d_s := d_{g_s}$$ denote the boundary distance function. Suppose $$d_s = d_0$$ for all $$s$$. The goal is to show that the family is **trivial** in the [Guillemin-Kazhdan](https://marshareb.github.io/GK) sense -- that is, we can find a smooth family of diffeomorphisms $$\{\psi_s\}$$ so that $$\psi_0 = \text{Id}$$, $$\psi_s |_{\partial M} = \text{Id}$$, and $$g_s = \psi_s^*(g_0)$$. Take $$x,y \in \partial M$$ and note that $$T := d_0(x,y) = d_s(x,y)$$ for each $$s$$. Thus we can take a variation with respect to $$s$$. If we let $$E_s$$ denote the energy functional with respect to the metric $$g_s$$, then using the same argument as in the above post we can calculate

$$ 0 =\frac{\partial}{\partial s} E_s(\gamma_s) = \int_{\gamma_0} \dot{E}, \ \ \dot{E} = \frac{\partial}{\partial s} E_s \bigg|_{s=0}.$$

The argument diverges from Guillemin-Kazhdan here, since we can no longer use the Livschitz theorem -- we only know the vanishing condition on the boundary, not on all periodic orbits. The goal now is to fix this gap.

We define the **X-Ray transform** to be a map $$I$$ which takes symmetric two tensor $$\beta$$ and gives the following:

$$I[\beta] : \partial M \times \partial M \rightarrow \mathbb{R}, \ \ I[\beta](x,y) = \int_0^T (\beta)_{\gamma(t)}(\dot{\gamma}(t), \dot{\gamma}(t)) dt,$$

where $$\gamma$$ is the unique unit speed geodesic connecting $$x$$ to $$y$$. If we let $$\beta = \frac{\partial g_s}{\partial s} \bigg|_{s=0}$$, we see that we have a symmetric $$2$$-tensor, and moreover we actually have that $$\beta \in \ker(I).$$ The goal is to build a function $$u : SM \rightarrow \mathbb{R}$$ so that $$X(u) = \beta.$$ If we can do so, then we have that $$\beta$$ is a trivial $$2$$-tensor, and the result essentially follows from the same argument as in the GK post.

Consider the function $$\tau^+, \tau^- : T^1M \rightarrow \mathbb{R}$$ so that if $$(x,v) \in T^1M$$ and $$\gamma$$ is the unique geodesic (viewed in terms of a function on $$T^1M$$) associated with $$(x,v)$$, then $$\gamma(\tau^-(x,v)), \gamma(\tau^+(x,v)) \in \partial(T^1M).$$ The difference between these two vectors is that we have

$$ \langle \gamma(\tau^+(x,v), \nu(\pi(\gamma(\tau^+(x,v)))) \rangle \geq 0, \ \ \langle \gamma(\tau^-(x,v), \nu(\pi(\gamma(\tau^-(x,v)))) \rangle \leq 0.$$

It is non-trivial to show that the functions $$\tau^+, \tau^-$$ are smooth off of $$T^1(\partial M)$$, however it follows by the simplicity condition. We define then

$$ u(x,v) := \int_{\tau^-(x,v)}^0 \beta_{\gamma(t)}(\dot{\gamma}(t), \dot{\gamma}(t)) dt.$$
