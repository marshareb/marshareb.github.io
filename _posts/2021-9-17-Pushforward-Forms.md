---
layout: post
title: Pushforward of Differential Forms
tag: geometry
categories: ["Geometry"]
---

In this post I discuss pushing forward differential forms, inspired by [this stackexchange post](https://math.stackexchange.com/questions/1435998/push-forward-of-differential-form-integration-over-fiber).

# Set Up

Suppose we have two smooth manifolds and a smooth map $$f : M \rightarrow N$$. If we have a smooth function $$g : N \rightarrow \mathbb{R}$$, we can define the **pullback** by

$$f^*(g)(x) = g(f(x)).$$

Thus we see that smooth maps induce a smooth map $$f^* : C^\infty(N,\mathbb{R}) \rightarrow C^\infty(M, \mathbb{R})$$. In the same way, we can define the **pullback** of a differential form $$\omega \in \Omega^k(N)$$ by

$$ f^*(\omega)_x(v_1, \ldots, v_k) = \omega_{f(x)}(df_x(v_1), \ldots, df_x(v_k)).$$

We observe that this is compatible with exterior derivatives and wedge products in the sense that

(1) $$f^*(\omega \wedge \eta) = f^*(\omega) \wedge f^*(\eta)$$,

(2) $$f^*(d\omega) = d(f^*(\omega))$$.

Checking this is just a matter of checking it on coordinates.

Our goal in this article is to try to go the other direction. In other words, given a smooth map $$f : M \rightarrow N$$, can we find a way to make sense of a *pushforward* between differentials? It turns out the answer is yes if we are dealing with submersions and differential forms with compact support (which can be weakened, but for our purposes isn't that much different). This method is called [integration along fibers](https://en.wikipedia.org/wiki/Integration_along_fibers).

# Building a Pushforward

## Vector Bundles

All hope may not be lost. Following [Bott and Tu](https://www.maths.ed.ac.uk/~v1ranick/papers/botttu.pdf), we refine our study to $$f : M \rightarrow N$$ with $$f$$ a submersion, meaning it is a smooth map such that the differential is surjective at every point. In general, we'll be focusing on **vector bundles**, which is a tuple of data $$(\pi, E, M, \{U_\alpha\}, \{\phi_\alpha\})$$ (sometimes written ambiguously as $$\pi : E \rightarrow M$$) where $$E, M$$ are manifolds, $$\pi^{-1}(x)$$ is a vector space for each $$x \in M$$, and there is an open cover $$\{U_\alpha\}$$ along with fiber preserving diffeomorphisms $$\phi_\alpha : \pi^{-1}(U_\alpha) \rightarrow U_\alpha \times \mathbb{R}^n$$ which are linear isomorphisms on each fiber. Observe that the tangent bundle is a vector bundle.

Let $$\{\phi_\alpha\}$$ come from our vector bundle data. Observe that given two of these maps we can get a map

$$\phi_\alpha \circ \phi_\beta^{-1} : U_\alpha \cap U_\beta \times \mathbb{R}^n \rightarrow U_\alpha \cap U_\beta \times \mathbb{R}^n.$$

Define the map

$$g_{\alpha \beta} : U_\alpha \cap U_\beta \rightarrow \text{GL}(n,\mathbb{R}), \ \ g_{\alpha \beta}(x) = \phi_\alpha \circ \phi_\beta^{-1} \mid_{\{x\} \times \mathbb{R}^n}.$$

We call these the **transition functions** of the vector bundle.

**Claim:** The transition functions of a vector bundle satisfy the **cocycle condition** on the intersection $$U_\alpha \cap U_\beta \cap U_\gamma$$:

$$ g_{\alpha \beta} \cdot g_{\beta \gamma} = g_{\alpha \gamma},$$

where $$\cdot$$ is defined to be the group operation for $$\text{GL}(n,\mathbb{R})$$.


**Proof:** This is just an easy calculation. Let $$x \in U_\alpha \cap U_\beta \cap U_\gamma$$. On $$\text{GL}(n,\mathbb{R})$$ the group operation is composition, so

$$g_{\alpha \beta} \circ g_{\beta \gamma}(x) = \phi_\alpha \circ \phi_\beta^{-1} \mid_{\{\phi_{\beta} \circ \phi_{\gamma}^{-1}(x)\} \times \mathbb{R}^n} \cdot \phi_\beta \circ \phi_\gamma^{-1} \mid_{\{x\} \times \mathbb{R}^n}.$$

Since these both share the same coordinates we see this translates to composition on the level of transition functions, so

$$g_{\alpha \beta} \circ g_{\beta \gamma}(x) = \phi_\alpha \circ \phi_\gamma^{-1} \mid_{\{x\} \times \mathbb{R}^n} = g_{\alpha \gamma}(x).$$

The result follows. $$\blacksquare$$

A nice observation to make is that the coycles $$\{g_{\alpha \beta}\}$$ completely determine the vector bundle. The idea is that given a vector bundle, we can build cocycles $$\{g_{\alpha \beta}\}$$, and then given the cocycles we can build a vector bundle with those cocycles by setting

$$E' := \left( \bigsqcup U_\alpha \times F \right)/\sim,$$

where $$(x,y) \sim (x, g_{\alpha \beta}(x)(y))$$. We then define a **bundle map** to be a map between vector bundles which is a fiber-preserving smooth map that is also linear on the fibers. One can show that this new vector bundle will be isomorphic to the old vector bundle under a bundle map -- see [this stackexchange post](https://math.stackexchange.com/questions/1010155/vector-bundles-and-cocycles).

We say the **structure group** of our vector bundle is $$\text{GL}(n, \mathbb{R})$$. If all of the cocycles live in a common subgroup $$H$$, we say the structure group may be reduced to this smaller subgroup.

There's some nice categorical properties for vector bundles, namely direct sums make sense, tensor products make sense, duals make sense, and Hom spaces make sense. We can also define a pullback as follows. Let $$f : M \rightarrow N$$ be a map between manifolds and $$\pi : E \rightarrow M$$ a vector bundle. Then $$f^*(E)$$ is the fiber bundle over $$N$$ defined by

$$f^*(E) := \{(n,e) : f(n) = \pi(e)\} \subseteq N \times E.$$


Another nice property is captured in **Theorem 6.8** in [Bott and Tu](https://www.maths.ed.ac.uk/~v1ranick/papers/botttu.pdf), which we'll list below.

**Theorem:** Let $$f,g : Y \rightarrow X$$ be homotopic maps with $$Y$$ a paracompact manifold and $$X$$ any manifold. If $$E$$ is a vector bundle on $$X$$, then $$f^*(E)$$ is isomorphic to $$g^*(E)$$.

**Remark:** Many of these results are more general than stated here, and apply to something called a **fiber bundle** (see [here](https://en.wikipedia.org/wiki/Fiber_bundle)).

**Remark:** The **trivial bundle** for a manifold $$M$$ of dimension $$n$$ is given by $$E := M \times \mathbb{R}^n$$.

## Forms with Compact Support

Let $$E$$ be an oriented rank $$n$$ vector bundle with base $$M$$ (meaning the dimension of the fibers is $$n$$ and that the structure group can be reduced to $$\text{GL}^+(n,\mathbb{R})$$). Suppose the dimension of $$M$$ is $$m$$. Our first claim is that we have a nice representation for forms with compact support on $$E$$.

**Claim:** If $$\omega \in \Omega_c^k(E)$$, then we have $$\eta \in \Omega_c^{n-m}(E)$$ and $$\delta \in \Omega^{k+m-n}(M)$$ so that

$$ \omega = \eta \wedge \pi^*(\delta).$$

**Sketch of Proof:** The idea is to do this in charts and then use a partition of unity to splice it all together. Since we have a submersion and we're dealing with a chart, we can utilize the [local submersion theorem](https://math.stackexchange.com/questions/1320102/local-submersion-theorem-differential-topology-of-guillemin-and-pollack). In these local coordinates we can write $$\omega = \sum_\alpha f_\alpha dx_{\alpha_1} \wedge \cdots \wedge dx_{\alpha_k}$$. It's then clear that we can choose $$\delta$$ to be those $$\alpha$$ for which all of the $$\alpha_i$$ are in the range $$\{1, \ldots, m\}$$, and we let $$\eta$$ be whatever remains. Since $$\omega$$ has compact support, we see that $$\eta$$ must also have compact support, and the representation follows. Observe this representation is not necessarily unique (since moving around coordinates will give rise to different representations on the charts) but we will see that integrating removes any ambiguity. $$\blacksquare$$

So we have a nice representation of compactly supported forms. Given a form $$\omega$$, we write it as $$\omega = \eta \wedge \pi^*(\delta)$$ and then we will ideally define the pushforward by setting

$$\pi_*(\omega) = \pi_*(\eta) \wedge \delta.$$

So we just need to understand what the pushforward of $$\eta$$ is. This is define by integration along the fiber. More precisely, we have

$$ \pi_*(\eta) \in C^\infty(M, \mathbb{R}), \ \ \pi_*(\eta)(x) := \int_{\pi^{-1}(x)} \eta.$$

Since this is a compactly supported form, this integral makes sense and is finite. We mentioned earlier that the decomposition of $$\omega$$ is not necessarily unique, however something to note is that the pushforward is still well-defined. This is actually essentially a change of variables argument. A form with compact support is completely determined by how it integrates along every ball, and we see exactly that for any choice of forms for $$\pi_*(\omega)$$ we have

$$ \int_B \pi_*(\omega) = \int_{\pi^{-1}(B)} \omega.$$
