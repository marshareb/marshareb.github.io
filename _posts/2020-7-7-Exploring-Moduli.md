---
layout: post
title: Exploring Modulus
tag: dynamics
categories: ["Dynamics"]
---

In this post, we continue the discussion from [here](https://marshareb.github.io/Moduli-and-Duality/) and Katok & Hasselblatt Section 2.1.


# Tangent Space and Derivatives

In the last post, we outlined some basic manifold theory (*very* briefly). We continue this slightly by going into derivatives. We described how to get differential maps but we didn't really paint the picture of what a derivative is. Here, we follow Katok & Hasselblatt A.3.

Recall that a curve can be encoded as $$\gamma : [0,1] \rightarrow M$$, a continuous map. It turns out that we can reparameterize so that the endpoints of our curve are any closed interval of $$\mathbb{R}$$ (this is an easy exercise). Furthermore, our curves need not necessarily be closed; we could have open curves $$\gamma : (a,b) \rightarrow M$$. We now are going to consider open curves where the interval contains $$0$$, so $$0 \in (a,b)$$ or $$a < 0 < b$$. This will be come relevant momentarily. Let $$C^\infty(M)$$ be the set of smooth maps $$f : M \rightarrow \mathbb{R}$$.

Since $$M$$ is a smooth manifold, we have that it has a smooth atlas (determining its smooth structure). So for $$p \in M$$, there is an atlas $$(U, \varphi)$$ with $$p \in U$$ and $$\varphi : U \rightarrow V \subset \mathbb{R}^n$$ a homeomorphism. We will fix $$p \in M$$. Consider the space of curves $$\gamma : (a,b) \rightarrow M$$ satisfying $$\varphi \circ \gamma : (a,b) \rightarrow V \subset \mathbb{R}^n$$ and with $$\gamma(0) = p$$. For each curve $$\gamma$$, we can define $$\Phi_\gamma : C^\infty(M) \rightarrow \mathbb{R}$$ by

$$ \Phi_\gamma(f) = \frac{d (f \circ \gamma)}{dt}(0).  $$

This map $$\Phi_\gamma$$ is called a *derivation*. If two curves induce the same derivation, that is, if $$\gamma, \gamma'$$ are two curves with $$\Phi_\gamma = \Phi_{\gamma'}$$, then we identify the curves in the set. This gives us an equivalence relation $$\sim$$. We take the space of curves and quotient it by this equivalence class. Now, we create a space of tangent vectors at $$p$$ by taking representatives from our equivalence classes $$\Phi_\gamma$$ from our space of derivations. It turns out that this is a finite dimensional vector space, and it has dimension $$n$$ (the dimension of the manifold).

A smooth map $$f : M \rightarrow N$$ is going to be differentiable if it has the property that for any charts $$(U, \varphi)$$ of $$M$$ and $$(V,\psi)$$ of $$N$$, we get $$\psi \circ f \circ \varphi^{-1}$$ is a differentiable map (differentiable in terms of maps from $$\mathbb{R}^n$$ to $$\mathbb{R}^m$$). Notice that such a map sends $$\gamma : (a,b) \rightarrow M$$ to $$f \circ \gamma : (a,b) \rightarrow N$$. The claim is that the map being differentiable implies that if two curves have the same derivation, i.e. if $$\gamma \sim \gamma'$$, then $$f \circ \gamma \sim f \circ \gamma'$$, so $$f$$ preserves the equivalence class of derivations. This is important, because this implies that $$f$$ induces a linear map $$D_pf : T_pM \rightarrow T_{f(p)}N$$. This induced map is defined by

$$ D_pf\left(\Phi_\gamma\right) = \Phi_{f \circ \gamma}. $$

Here the $$\Phi$$ are understood to be with respect to the appropriate spaces (the one on the left is $$C^\infty(M)$$, the one on the right is $$C^\infty(N)$$).

One can note that this derivative satisfies a lot of the general properties of what we're used to. Lee's Smooth Manifolds has these properties as an exercise if I remember correctly.

# Moduli and Conjugacy

Ultimately, a lot of our dynamical systems will be on (smooth) compact manifolds, or compact metric spaces. As a result, we'd like to be able to say whether two dynamical systems are "essentially" the same (where essentially here is a vague term). We outlined last time a sort of equivalence via diffeomorphisms. For discrete dynamical systems, all of the information is essentially contained in the map, since the change over time is measured via iterates and the map should be an endomorphism (which means a map from an object to itself). Naturally then, two maps (or dynamical systems if we are going to translate it) should be equivalent if there is a diffeomorphism (a bijective map preserving the smooth structure both ways) which conjugates one map to another.

Throughout, $$M$$ and $$N$$ will be smooth manifolds. Recall last time that we had the space $$C^r(M,M)$$, which is the space of endomorphisms on $$M$$ which admit up to $$r$$ continuous derivatives. On this space we were able to equip it with a metric called the $$C^r$$ metric (really a norm) which gives it a topology, called the $$C^r$$ topology. We are going to take an open subset $$U \subset C^r(M,M)$$. Note that this is a collection of maps which are sort of "stable" in the sense that small perturbations stay within the set (meaning that if I change the map slightly, where slightly is with regards to the $$C^r$$ metric, then it stay within the set $$U$$). We take $$0 \leq m \leq r$$. A $$C^m$$ modulus, then, is a continuous functional $$F : U \rightarrow \mathbb{R}$$ if there exists a $$\delta > 0$$ such that $$F(f) = F(g)$$ for any two maps $$f,g \in U$$ that are $$C^m$$ equivalent via a diffeomorphism $$h$$ which is close to the identity. If we denote the $$C^r$$ metric by $$d_{C^m}$$, this is saying $$F(f) = F(g)$$ if there is a $$C^m$$ diffeomorphism $$h$$ satisfying $$d_{C^m}(h, \text{id}) < \delta$$.

The first thing to note in this definition is that the $$\delta$$ is uniform on the modulus. So uniformly we have that the $$C^m$$ equivalences are $$\delta$$ close to the identity. As Katok & Hasselblatt say, the condition of being close to the identity is useful for continuous-time systems (i.e. flows). In some sense, moduli are a general way of capturing equivalence of dynamical systems. Once you have some moduli on a space, you can then take that moduli and use it to determine not only equivalence, but *how* equivalent a system is (where maybe a good notion of how equivalent you are is how far away your diffeomorphism is from the identity).

We follow Katok & Hasselblatt's example for finding some moduli on a space. Let $$f : M \rightarrow M$$ be a discrete-time dynamical system, and suppose $$f$$ has a periodic point of period $$n$$. Label this point as $$p$$. If $$g$$ is $$C^m$$ equivalent to $$f$$ through a diffeomorphism $$h$$, we have that

$$ g = h \circ f \circ h^{-1} \implies g \circ h = h \circ f.$$

Note that

$$g^n \circ h = g^{n-1} \circ g \circ h = g^{n-1} \circ h \circ f, $$

so inducting gives

$$ g^n \circ h = h \circ f^n.$$

Now note that $$p$$ being a periodic point of period $$n$$ implies that $$f^n(p) = p$$. We see then that

$$ g^n(h(p)) = h(f^n(p)) = h(p).$$

So $$h(p)$$ is a periodic point of $$g$$ with period $$n$$. This tells us that the number of periodic points with period $$n$$ for both dynamical systems is the same. Since this is a nice measure of complexity, this suggests that the complexity of equivalent dynamical systems is the same (note that using the notion of topological entropy gives us the same result).

We get a little more if $$m \geq 1$$. In this case, we see that $$h$$ gets $$m$$ continuous derivatives. Hence, since

$$ f^n = h^{-1} \circ g^n \circ h,$$

we see that at the point $$p \in M$$ (now not necessarily periodic) we get

$$ D_p f^n = D_p(h^{-1} \circ g^n \circ h) = D_{g^n(h(p))}h^{-1} \circ D_{h(p)}g^n \circ D_p h.$$

If $$p$$ is a periodic point with period $$n$$, then we know that $$g^n(h(p)) =h(p)$$, so

$$ D_p f^n = D_{h(p)}h^{-1} \circ D_{h(p)} g^n \circ D_ph.$$

Now we remark that

$$ D_{h(p)}h^{-1} = (D_p h)^{-1}.$$

This is proven by showing that

$$ D_{h(p)}h^{-1} \circ D_p h = D_p(h^{-1} \circ h) = D_p(\text{Id}) = \text{Id},$$

$$ D_p h \circ D_{h(p)} h^{-1} = D_{h(p)}(h \circ h^{-1}) = D_{h(p)}(\text{Id}) = \text{Id}.$$

This is also in Lee's Smooth Manifolds. Using this, we have

$$ D_p f^n = (D_p h)^{-1} \circ D_{h(p)} g^n \circ D_p h.$$

So the linear functions $$D_p f^n$$ and $$D_{h(p)} g^n$$ are conjugate. Conjugate linear maps share the same spectrum (since finite dimensional, same eigenvalues). The set of eigenvalues of $$D_pf^n$$ is called the spectrum of the periodic point $$p$$.

Earlier in the book [Proposition 1.1.4], Katok & Hasselblatt prove that if $$p$$ is a periodic point of period $$n$$ for a $$C^1$$ map $$f$$ and the differential $$D_p f^n$$ does not have one as an eigenvalue, then for every map $$g$$ sufficiently close to $$f$$ in the $$C^1$$ topology there is a unique periodic point of period $$n$$ close to $$p$$. So if $$1$$ is not in the spectrum of the periodic point $$p$$ of $$f$$, then we have that there are several $$C^1$$ moduli. Periodic points are isolated, so this gives some idea of how moduli are somehow independent.

The data that a modulus can give us is varying depending on the structure itself. Sometimes a great deal of structure can be encoded in the modulus for specific dynamical systems.
Looking at the expanding map $$E_m$$ which is the times $$m$$ map, we see that the spectra of periodic orbits gives us a complete system of $$C^1$$ and smooth equivalences in a neighborhood of this map. The moral of this story is that a modulus is a useful tool for extracting information around neighborhoods of functions, though the information that we extract is dependent on the kind of modulus we're looking at.
