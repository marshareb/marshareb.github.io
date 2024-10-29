---
layout: post
title: Klingenberg's Theorem for Anosov geodesic flows on surfaces
tag: geometry, dynamics
categories: ["Geometry", "Dynamics"]
---

In this post, we talk about a new proof of Klingenberg's fact: an Anosov geodesic flow is without conjugate points.

# Result

I wanted to collect this proof somewhere, as the original paper of Klingenberg (see [here](https://www.jstor.org/stable/1971011)) is somewhat hard to read. The idea is to prove the following using some general facts about geodesic flows (following Mane's work).

**Theorem:** If a Riemannian metric is Anosov, then it is without conjugate points.

The sketch is as follows. First, if the geodesic flow is Anosov, then it is (in particular) a contact Anosov flow. As shown in [Theorem 2.8](https://arxiv.org/pdf/2004.14431), this implies that the geodesic flow is *homologically full*. There are many equivalent definitions for homologically full, but the one we adopt is that every homology class in $$H_1(SM, \mathbb{Z})$$ is represented by a closed geodesic.

Next, we study the so-called *Maslov index* (see [here](https://link.springer.com/article/10.1007/BF01075861)). Briefly, if a vector is in the vertical bundle, then its corresponding Jacobi field vanishes at zero. Given any Lagrangian space (which varies continuously and is invariant), we have that the space is "rotating" as one flows the orbit forward (in the case of surfaces, it is actually rotating). The Maslov index is a cohomology class in $$H^1(SM, \mathbb{Z})$$ which, for closed orbits, counts how many times this Lagrangian space intersects the vertical space in the correct orientation. One can show that the vertical bundle is transversal to the geodesic flow (call this the *twist property*), and hence (up to a choice of orientation) the Maslov index of a geodesic is always positive.

The proof of the theorem boils down to two observations.

1) If the geodesic flow is Anosov, then the Maslov index is exact.

2) If the metric has conjugate points, then the Maslov index (for any continuous Lagrangian bundle) is not exact.

Gluing these statements together yields the theorem. The first one is easy. In the case of an Anosov geodesic flow, either the stable or the unstable bundles give rise to a Lagrangian subspace, and so we can take their associated Maslov index. Now, since the geodesic flow is homologically full, we have that the Maslov index is a positive homomorphism from $$H_1(SM, \mathbb{Z})$$ to $$\mathbb{Z}$$, and hence it must be exact.

For the second, we simply need to show that if there are conjugate points, then the Maslov index cannot be exact. Assume we have a closed orbit with conjugate points. Without loss of generality, this implies there is a vector in the unit tangent bundle for which this Lagrangian space is equal to the vertical bundle, say $$v$$. Furthermore, the twist property implies there is an $$\epsilon > 0$$ so that the Lagrangian space at $$v_{\pm} =: g_{\pm \epsilon/2}(v)$$ does not intersect the vertical bundle. If this Lagrangian space depends continuously on $$v$$ (which is certainly the case for Anosov flows), then there is a neighborhood $$U_\pm$$ of $$v_\pm$$ such that for all $$v \in U_\pm$$, we have that the Lagrangian space for vectors in $$g_{\pm \epsilon/2}(U_\pm)$$ also does not intersect the vertical. Notice that $$g_\epsilon(U_-) \cap U_+ \neq \varnothing$$, and take $$\eta$$ in this intersection. Now use Poincare recurrence to get that there is a large $$S > \epsilon$$ so that $$g_S(\eta)$$ is back in the intersection. Let $$T := S - \epsilon > 0$$. Notice that $$g_T(\eta)$$ lies in $$U_-$$. We then form a loop by connecting $$v$$ to $$v_+$$, $$v_+$$ to $$\eta$$, $$\eta$$ to $$g_T(\eta)$$, $$g_T(\eta)$$ to $$v_-$$, and $$v_-$$ to $$v$$. The only thing to note about this loop is that, we connect $$v_+$$ to $$\eta$$ via a curve contained in $$U_+$$, and $$v_-$$ to $$g_T(\eta)$$ via a curve in $$U_-$$; the other components come from the flow. By construction, the Maslov index along this curve will be positive.

**Remark:** 1) The second observation is due to Mane. In particular, notice that this is a much deeper result on symplectic dynamics (once properly interpreted). Given a smooth flow $$\varphi_t : X \rightarrow X$$, consider its lifted flow to the tangent bundle $$d \varphi_t : TX \rightarrow TX$$. Suppose that there is a Lagrangian bundle of $$TX$$ which satisfies the *twist property*, meaning that it is transversal to the flow (or as Arnol'd puts it, the bundle is in general position). Given any other continuous invariant Lagrangian bundle, we can define its Maslov index according to the flow. If these bundles intersect at any point, then Mane's argument shows that the Maslov index is not exact *provided* the intersection point is in a neighborhood that satisfies Poincare recurrence. In the case of the geodesic flow, one can interpret this in terms of conjugate points, and since it is volume preserving every point is in a neighborhood that satisfies Poincare recurrence.

2) Notice that we actually have shown that if there is a continuous invariant Lagrangian subbundle, then the metric is without conjugate points. 

A version of this argument can be found in [Paternain's book](https://link.springer.com/book/10.1007/978-1-4612-1600-1).

# Remaining questions

This argument heavily uses the fact that it is contact and that there is recurrence. The contact property is useful for the fact that the flow is homologically full, while the recurrence is important for the last argument. A natural question is whether these are necessary conditions, or if they are just convenient. Of course, one has to be careful about what conjugate points even mean for flows that are not the geodesic flow. In a [recent paper](https://arxiv.org/html/2404.17726v3), Valerio Assenza, Ivo Terek, and I explored the notion of conjugate points for magnetic systems. Once restricted to the appropriate quotient bundle, there is a natural Lagrangian subbundle of interest, and one would like to show that if the magnetic flow is Anosov, then the stable and unstable bundles do not intersect this Lagrangian subbundle. All that needs to be fixed in the above argument is the homologically full portion.

Let $$F$$ be the infinitesimal generator of the magnetic flow. As noted in [Theorem 2.8](https://arxiv.org/pdf/2004.14431), the magnetic flow is homologically full if for every $$[\omega] \in H^1(M,\mathbb{R})$$, we have

$$ \int_M \omega(F)m = 0,$$

where $$m$$ is the volume form. In fact, notice that argument in Theorem 2.8 generalizes to magnetic flows; all that was used was that $$\alpha(F) = 1$$, where $$\alpha$$ is the contact form for the geodesic flow (and this is always true for the magnetic flow). Thus, the above argument *always* works for magnetic flows (once everything is appropriately interpreted).

Finally, it is natural to wonder whether this works for flows that are dissipative, such as generalized thermostats. Without Poincare recurrence, I am not sure how to bypass the last argument.
