---
layout: post
title: Gauss-Bonnet for disks
tag: geometry
categories: ["Geometry"]
---

In this post, we talk about the Gauss-Bonnet theorem for disks.

# Introduction

The Gauss-Bonnet theorem is a beautiful result which connects topological information and geometric information. Let $$(M,g)$$ be an oriented surface. Then the Gauss-Bonnet theorem says that for a polygon $$Q$$ in the surface, we have

$$ \int_Q K^g dA + \int_{\partial Q} k_g ds = 2\pi \chi(Q),$$

where
- $$K^g$$ is the [Gaussian curvature](https://en.wikipedia.org/wiki/Gaussian_curvature),
- $$k_g$$ is the [geodesic curvature](https://en.wikipedia.org/wiki/Geodesic_curvature), and
- $$\chi(Q)$$ is the [Euler characteristic](https://en.wikipedia.org/wiki/Euler_characteristic).

Note that if $$\partial Q$$ is piecewise smooth, then the integral over the boundary is interpreted to be the sum of the integral of the smooth part plus the angles by which the smooth part turns -- see [here](https://en.wikipedia.org/wiki/Gauss%E2%80%93Bonnet_theorem#Statement).

There are many deep results one can derive using the Gauss-Bonnet theorem. For example, applying the above to a geodesic triangle, we get

$$ 2\pi = \int_Q K^g dA + \sum_{i=1}^3 \alpha_i,$$

where $$\alpha_i$$ are the exterior angles of the triangle. Let $$\beta_i = \pi - \alpha_i$$ be the interior angles. Then we have

$$ 2\pi = \int_Q K^g dA + 3\pi - \sum_{i=1}^3 beta_i,$$

which after rearranging yields

$$\sum_{i=1}^3 \beta_i = \int_Q K^g dA + \pi.$$

If we have everywhere negative curvature, then this can be interpreted as saying that the sum of the interior angles of a geodesic triangle is less than $$\pi$$.

The Gauss-Bonnet theorem is a critical tool when it comes to proofs of marked length spectrum rigidity on surfaces. Both Otal and Croke use some variation of it:
- Otal uses the Gauss-Bonnet theorem for geodesic triangles to get a fact about the sum of the interior angles. This can also be deduced using the Rauch comparison theorem.
- Croke uses the Gauss-Bonnet theorem for a disk to get a bound independent of the parameterization. It seems like a comparison theorem could replace his result as well, but it's not as clear.

The only weakness the Gauss-Bonnet theorem has is that it only applies to surfaces -- nothing can be said in higher dimensions using this theorem. Tools to get around this fact are known (for example, the Rauch comparison theorem), but there's nothing really as powerful as the full result.

There are essentially two kinds of proofs of the Gauss-Bonnet theorem, which after some careful consideration are related. One comes from a perspective on the tangent bundle, while the other is more intrinsic to the manifold itself. In this post, I'll recreate the proof of Gauss-Bonnet for geodesic disks, which is different from both of the proofs. Note this is not my own result, but rather a recreation of something I read [here](https://cuhkmath.wordpress.com/2018/02/26/a-simple-proof-of-the-gauss-bonnet-theorem-for-geodesic-ball/). This proof is nice, as it is essentially an argument in Jacobi fields and the fundamental theorem of calculus.

# Gauss-Bonnet for disks

Recall that the geodesic exponential map is given by $$\exp_p(v) := \gamma_v(1).$$ We can define a smooth parameterization of a geodesic disk on the surface using this exponential map:

$$ H : S^1 \times [0,T] \rightarrow M, \ \ H(\theta, t) := \exp_p( t \cdot (\theta v)),$$

where $$v$$ is some reference vector that is fixed and $$\theta v$$ is that vector rotated by $$\theta$$. Let $$B_T := H(S^1 \times [0,T])$$ be the geodesic disk in $$M$$. Notice this is fine to do as long as the radius of the geodesic ball is sufficiently small (in particular, as long as it is contained in a normal neighborhood). For simplicity, just assume that the curvature is negative so that we can get rid of this criteria.

Consider the variational vector field $$H_*(d/d\theta) = J(\theta, t).$$ Clearly $$J(\theta, 0) = 0$$. Using the same argument as in DoCarmo Chapter 10 Proposition 2.5, we also see that $J'(\theta, 0) = 1.$$ We claim that $$J$$ is a Jacobi field along the geodesic $$\gamma_{\theta v}$$. Recall that this means that

$$ J''(\theta, t) + K^g(\gamma_{\theta v}(t)) J(\theta, t) = 0,$$

where the prime denotes the derivative in the $$t$$ direction (i.e. the geodesic direction). This involves a classic lemma from Riemannian geometry (see [here](https://www.mathi.uni-heidelberg.de/~lee/Sebastian05.pdf) or DoCarmo Chapter 4 Lemma 4.1). We'll skip over the details for now.

Notice that everything is parameterized with respect to arc length, so $$J(\theta t)$$ is actually a normal Jacobi field. This means that the tangential part of $$J(\theta ,t)$$ is zero, so there is a function $$ j : S^1 \times [0,T] \rightarrow \mathbb{R}$$ so that we can write $$J(\theta, t) = j(\theta, t) \dot{\gamma}_{\theta v}^\perp(t).$$

Now, notice that

$$ \int_0^{2\pi} j'(\theta, T) d\theta = \int_0^{2\pi} \int_0^T j''(\theta, t) dt d\theta + \int_0^{2\pi} j'(\theta, 0)d\theta.$$

Using the fact that $j(\theta, t)$$ satisfies the Jacobi equation, we can rewrite this as

$$ \int_0^{2\pi} j'(\theta, T) d\theta = -\int_0^{2\pi} \int_0^T K^g(\gamma_\theta(t)) j(\theta, t) dt d\theta +  \int_0^{2\pi} j'(\theta, 0)d\theta.$$

We now set up notation:
- Let $$\sigma(\theta) := H(\theta, T)$$ be a curve which parameterizes the boundary. Notice that $$\sigma'(\theta) = J(\theta, T)$$.
- Let $$T(\theta) := \sigma'(\theta)/|\sigma'(\theta)|$$ be the unit tangent vector field of $$\sigma$$.
- Let $$N(\theta) := \dot{\gamma}_{\theta v}(T)$$. This is a unit tangent vector field, and by the Gauss lemma this is normal to $$T$$.

Notice that
$$ J'(\theta, T) = \nabla_{\dot{\gamma}_{\theta v}(T)} J(\theta, T) = \nabla_{\sigma'(\theta)} \dot{\gamma}_{\theta v}(T) = |\sigma'(\theta)| \nabla_T N = - k_g(\theta) |\sigma'(\theta)| T(\theta),$$

here using the definition of geodesic curvature. Thus

$$ \int_0^{2\pi} j'(\theta, T) d\theta = \int_{\partial B_T} k_g ds.$$

On the other hand, recall that the area form on $$M$$ is given by

$$ dA(v,w) := \langle w, v^\perp \rangle.$$

We see that

$$H^*(dA) = j(\theta, t) dt d\theta,$$

so combining the above yields

$$ \int_{\partial B_T} k_g ds = -\int_0^{2\pi} \int_0^T K^g(H(\theta, t)) H^*(dA) +  \int_0^{2\pi} j'(\theta, 0)d\theta.$$

Now, we have equality as long as the parameterization is one-to-one, which in this case it is. Using the change of variables formula, we get

$$ \int_{B_T} K^g dA + \int_{\partial B_T} k_g ds =  \int_0^{2\pi} j'(\theta, 0)d\theta.$$

Finally, use the fact that $$j'(\theta, 0) = 1$$ to get

$$ \int_{B_T} K^g dA + \int_{\partial B_T} k_g ds = 2\pi.$$

This is exactly the Gauss-Bonnet theorem for disks!

**Remark:** If we chose a different parameterization which is possibly more than one-to-one but has the same boundary, then using the fact that curvature is negative we would have

$$ \int_{\partial B_T} k_g ds + \int_{B_T} K^g dA \geq \int_0^{2\pi} j'(\theta, g(\theta))d\theta. $$

An expression like this arises in Lemma 1.3 of Croke (though his lemma works in more generality); see [here](https://link.springer.com/article/10.1007/BF02566599). For Theorem B, Croke only needs the disk version of this lemma, which is what we've just derived above.
