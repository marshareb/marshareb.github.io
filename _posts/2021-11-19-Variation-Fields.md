---
layout: post
title: Variational Fields
tag: geometry
categories: ["Geometry"]
---

In this post I discuss variational fields.

# Set Up

Throughout, $$(M,g)$$ denotes a smooth Riemannian manifold.

# Connections

The goal is to try to make sense of a directional derivative. We know how this makes sense on Euclidean space, and we'd like to generalize the important properties to Riemannian manifolds. We will denote $$\Gamma(TM)$$ to be the collection of smooth vector fields on $$M$$.

A **connection** on $$M$$ is a bilinear map $$\nabla : \Gamma(TM) \times \Gamma(TM) \rightarrow \Gamma(TM)$$ satisfying the following for every $$X,Y \in \Gamma(TM)$$, $$f \in C^\infty(M)$$:

(1) $$\nabla_{fX} Y = f \nabla_X Y,$$

(2) $$\nabla_X(fY) = X(f) \nabla_X(Y) + f \nabla_X Y.$$

A connection is said to be **compatible with the metric** if  we have

$$X g(Y,Z) = g(\nabla_X Y, Z) + g(X, \nabla_Y Z).$$

This is analogous to the chain rule.

A connection is said to be **torsion free** if we have

$$\nabla_X Y - \nabla_Y X - [X,Y] = 0.$$

The **Levi-Civita** connection is the unique connection which is compatible with the metric and torsion free. The idea behind finding it is to use the above conditions and the non-degenerate quality of $$g$$ to define a metric.


# Curves

Let $$\gamma : [0,T] \rightarrow M$$ be a smooth curve. We can define $$\gamma'(t) = \frac{d\gamma}{dt}(t).$$ Notice this is an element in $$T_{\gamma(t)}M$$ -- it's a vector. Thinking about the tangent bundle, we have that the curve $$\gamma$$ induces a curve on the tangent bundle, which we'll denote by $$\hat{\gamma} : [0,T] \rightarrow M$$. This curve is defined by

$$\hat{\gamma}(t) := (\gamma(t), \gamma'(t)).$$

Recall our metric defines a norm via

$$\sqrt{g_x(v,v)} = \|v\|_x.$$

From the Levi-Civita connection, we know how to differentiate

We can define the **length** of a curve by

$$L(\gamma) := \int_0^T \|\gamma'(t)\|dt.$$

We can define the **energy** of the curve by

$$E(\gamma) := \frac{1}{2} \int_0^T \|\gamma'(t)\|_{\gamma(t)}^2 dt.$$

# Parallel Transport

The idea here is that given a vector at a point, we wish to move the vector along the curve in such a way so that it remains parallel to the original vector. Let $$\gamma$$ be a curve on the manifold. A **vector field along $$\gamma$$** is a mapping $$X : [0,T] \rightarrow TM$$ so that $$X(t) \in T_{\gamma(t)}M$$. The set $$\Gamma(\gamma*TM)$$ will be the collection of smooth vector fields along a curve $$\gamma$$. The idea now is that the Levi-Civita connection induces a connection along the curve, meaning it induces a way of differentiating along a curve. This connection is denoted by $$\frac{D}{dt}$$. It satisfies the following properties:

(1) $$\frac{D}{dt}(fX) = f' X + f \frac{D}{dt}X,$$

(2) If $$X$$ admits an extension to a smooth vector field $$Z$$ on an open subset $$U$$ of $$M$$, then

$$\frac{D}{dt}X(t) = (\nabla_{\gamma(t)}Z)_{\gamma(t)}.$$

The proof for existence can be found in [these notes](https://www.ime.usp.br/~gorodski/teaching/mat5771/ch2.pdf).

A vector field is said to be **parallel** if $$ \frac{D}{dt}X \equiv 0.$$

# Induced Connection

Recall that if we have a smooth map $$\phi : N \rightarrow M$$, we can define the **pull back** of a vector field $$X \in \Gamma(TM)$$ by

$$\phi^*(X)(p) := X(\phi(p)).$$

The **pushforward** of a vector field $$Y \in \Gamma(TN)$$ is defined by

$$\phi_*(Y)(p) = d\phi_p(Y(\phi^{-1}(p)))$$

when this makes sense.

We then denote $$\Gamma(\phi^*(TN))$$ to be the set of smooth pulled back vector fields.

Given a smooth map $$\phi : N \rightarrow M$$ with $$M,N$$ smooth Riemannian manifolds, we get an **induced connection** which is a bilinear map $$\nabla^\phi : \Gamma(TN) \times \Gamma(\phi^*(TM)) \rightarrow \Gamma(\phi^*(TM))$$ satisfying the following:

(1) $$\nabla^\phi_{fX}Y = f \nabla_X^\phi Y,$$

(2) $$\nabla_X^\phi(fY) = X(f) Y + \nabla_X^\phi(Y),$$

(3) If $$Y$$ admits an extension to a vector field $$Z$$ on an open subset $$U \subseteq M$$ then

$$(\nabla_X^\phi Y)_p = (\nabla_{d\phi(X_p)}Z)_{\phi(p)}.$$

We observe that induced connections satisfy the following nice properties, similar to the Levi-Civita connection. Let $$X,Y \in \Gamma(TN)$$ and $U,V \in \Gamma(\phi^*(TM)).$$ We have

(1) $$\nabla_X^\phi(\phi_*(Y)) - \nabla_Y^\phi(\phi_*(X)) - \phi_*([X,Y]) = 0,$$

(2) $$X g(U,V) = g(\nabla_X^\phi U, V) + g(U, \nabla_X^\phi V).$$

# Variation

A **variation** of a curve $$\gamma : [0,T] \rightarrow M$$ is a smooth map $$\Gamma : (-\epsilon, \epsilon) \times [0,T] \rightarrow M$$ such that the following hold:

(1) $$\Gamma(s, \cdot)$$ is a smooth curve,

(2) $$\Gamma(0, t) = \gamma(t)$$.

This is a smooth function from a Riemannian manifold to a Riemannian manifold, so we can in particular induce a connection $$\nabla$$ (not the Levi-Civita connection). We consider the following vector fields along $$H$$:

(1) $$T := dH\left(\frac{d}{dt}\right),$$

(2) $$Y := dH\left(\frac{d}{ds}\right).$$

With this, we can define the **variational vector field** by

$$ S := Y \mid_{s=0}.$$

This is a vector field defined along the curve $$\gamma$$.

**Remark:** I'll be sloppy and sort of interchangeably use $$\gamma'$$ and $$T$$. Hopefully it'll be clear from context that these are really playing the same role.
