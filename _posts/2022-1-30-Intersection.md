---
layout: post
title: Geodesic Currents and Intersection Numbers
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss geodesic currents and intersection numbers

# Geodesic Currents

Throughout, let $$M$$ be a closed orientable hyperbolic surface and let $$\tilde{M}$$ be its universal cover with the appropriately lifted metric. Two geodesic $$\gamma_0, \gamma_1 : [0,\infty) \rightarrow \tilde{M}$$ are said to be **asymptotic** if there exists a $$T \in \mathbb{R}$$ so that

$$\lim_{t \rightarrow \infty} d(\gamma_0(t + T), \gamma_1(t)) = 0.$$

We write $$\gamma_0 \sim \gamma_1$$ if this holds. We observe this forms an equivalence relation on the space of directed geodesics, and hence we can form the **boundary at infinity** $$\partial^\infty \tilde{M}$$ to be the set of all equivalence classes of directed geodesics under this equivalence relation. We can also do this in backward time, and this forms the same boundary at infinity.

Notes that two distinct points $$(x,y) \in \partial^\infty \tilde{M} \times \partial^\infty \tilde{M}$$ determine a unique geodesic (up to reparameterization). Since we're focused on unit speed geodesics, it makes sense to define the space of **oriented geodesics** by

$$G(M) := \partial^\infty \tilde{M} \times \partial^\infty \tilde{M} \setminus \Delta.$$

Notice that this is a manifold with charts. Given a unit-speed geodesic $$\gamma$$ on $$\tilde{M}$$ with endpoints $$x,y \in \partial^\infty \tilde{M}$$ we can let $$I(G)$$ be the set of all unit-speed geodesics which intersect $$\gamma$$ transversely. Then these geodesics are uniquely determined by two points of data -- where they intersect $$\gamma$$ and at what angle they intersect $$\gamma$$. This gives us charts $$\mathbb{R} \times (0,\pi)$$ on $$G(M)$$ (in the sense of a smooth manifold). On each chart we can define a measure

$$d\lambda := \frac{1}{2} \sin(\theta) d\theta dt,$$

and we can pull back this measure through each chart. We can check that these measures agree on overlaps of charts, and thus we can define a global measure $$\lambda_g$$ on $$G(M)$$.

We also observe that we can define the **unoriented geodesics** by

$$OG(M) := G(M)/\{ \pm\}.$$

It is not too hard to see that $$\lambda_g$$ defined is independent of the orientation of the geodesic, so descends to a measure $$\lambda_g$$ on $OG(M)$$ (which is invariant under the action of $$\pi_1(M)$$). We call said measure the **Liouville current**.

We can define a **geodesic current** of $$M$$ to be a locally finite Borel measure on $$OG(M)$$ invariant under the action of $$\pi_1(M)$$. The space of geodesic currents is given by $$C(M)$$, and this is endowed with the weak* topology. That is, $$\mu_n \rightarrow \mu$$ if for every function $$\phi$$ we have

$$\int \phi d\mu_n \rightarrow \int \phi d\mu.$$

Thus our first example of a geodesic current is the Liouville current. We now want to give a bunch of examples of geodesic currents arising from geodesics.

Let $$[\gamma]$$ be a free homotopy class on $$M$$. Suppose it is a prime class, meaning there is not another class $$[\delta]$$ so that $$[\delta]^k = \[\gamma]$$ for some integer $$k$$. Since everything is hyperbolic, there is a unique closed geodesic $$\gamma$$ in this free homotopy class. We can lift this geodesic to a family of geodesics in $$\tilde{M}$$ and define a measure $$j([\gamma])$$ which is simply the Dirac measure of this lift.

**Claim:** $$j([\gamma])$$ is a geodesic current.

**Proof:** Let's first check that it is invariant under the action of $$\pi_1(M)$$. Given a deck transformation $$p : \tilde{M} \rightarrow \tilde{M}$$ and a Borel set $$U \subseteq \tilde{M}$$ we have that $$p_*(j([\gamma]))(U) = j([\gamma])(p^{-1}(U)).$$ Since deck transformations preserve the set of all lifts, we get that the number of lifts of the closed geodesic must be the same, so $$p_*(j([\gamma])) = j([\gamma])$$ and hence this measure is invariant under the $$\pi_1(M)$$ action. It is a Borel measure by nature, and it is locally finite since the set is discrete. $$\blacksquare$$

Now we extend $$j$$ by homogeneity to all classes -- that is, $$j([\gamma]^p) = p j([\gamma])$$. If we label the collection of all free homotopy classes $$\mathcal{C}(M)$$ this gives us a map $$j : \mathcal{C}(M) \rightarrow C(M)$$. Since closed geodesics are dense, we get that the span of the image of $$j$$ is dense inside of $$C(M)$$. Thus (up to approximation) we have identified essentially all geodesic currents.

Since the Liouville current $$\lambda_g$$ is so dependent on the metric, one might ask to what extend does it determine the metric? That is, does the Liouville current somehow *uniquely* determine what the metric is (up to isometry)? Recall that the marked length spectrum is a map $\ell_g : \mathcal{C}(M) \rightarrow \mathbb{R}_{> 0}$$ which takes free homotopy classes to the lengths of the unique geodesic inside of the free homotopy class. We have  that Otal-Croke's theorem says that the marked length spectrum determines the metric up to isometry -- in other words, if $$g_1, g_2$$ are two metrics on $$M$$ so that $$\ell_{g_1} = \ell_{g_2}$$ then $$g_1 \simeq g_2$$. It turns out we can extend this to the Liouville current as well with the following observation.

**Observation:** If $$\lambda_{g_1} = \lambda_{g_2}$$ then $$\ell_{g_1} = \ell_{g_2}$$.

To prove this, we'll need to discuss the intersection form.

# Intersection Form

Define the following bundles:

- With regards to a metric, we have the **unit tangent bundle** is given by

$$T_1 \tilde{M} := \{(x,v) \in T \tilde{M} \ | \ \|v\|_x^2 = 1\}.$$

- We have the **projective unit tangent bundle** is given by

$$PT_1 \tilde{M} := T_1\tilde{M}/\alpha \text{ where } \alpha : T_1 \tilde{M} \rightarrow T_1 \tilde{M}, \ \alpha(x,v) = (x,-v).$$

This is equipped with the usual projection map $$\pi : PT_1 \tilde{M} \rightarrow \tilde{M}$$ with $$\pi(x, \pm v) = x$$.

- We have the **geodesic intersection bundle** is given by

$$ I_1 \tilde{M} := \{(\pm v, \pm w) \in PT_1 \tilde{M} \times PT_1 \tilde{M} \ | \ \pi(\pm v) = \pi(\pm w), v \neq \pm w\}.$$

The **intersection form** is a continuous symmetric bilinear map $$i : C(M) \times C(M) \rightarrow \mathbb{R}$$ defined by

$$i(\alpha, \beta) := (\alpha \times \beta)(I_1 \tilde{M}).$$

We make the following observation which justifies the name.

**Observation:** Suppose $$\alpha, \beta$$ are closed geodesics on $$M$$, then $$i(j([\alpha]), j([\beta]))$$ is the number of transverse intersections of $$\alpha$$ and $$\beta$$.

**Idea:** To help with notation, just identify $$\alpha$$ with $$j([\alpha])$$ and similarly with $$\beta$$. Observe that

$$i(\alpha, \beta) = \int_{I_1 \tilde{M}} d\alpha \times d\beta = \int_{x \in \tilde{M}}\int_{(\pm v, \pm w) \in (I_1)_x \tilde{M}} d\alpha(x, \pm v) d\beta(x, \pm w).$$.

Consequently $$d\alpha(x, \pm v) = 1$$ iff $$(x, v)$$ or $$(x,-v)$$ lies on the geodesic $$\alpha$$. Thus $$d\alpha(x, \pm v) d\beta x, \pm w) = 1$$ iff $$\alpha$$ and $$\beta$$ intersect transversely at $$x$$. We sum over all such points and this gives us the desired result. $$\blacksquare$$

There's also an interesting connection to the Liouville current.

**Claim:** Using similar identifications to above, we have that $$i(\alpha, \lambda_g) = \ell_g([\alpha]).$$

**Proof:** Notice that

$$i(\alpha, \lambda_g) = \int_{x \in \tilde{M}}\int_{(\pm v, \pm w) \in (I_1)_x \tilde{M}} d\alpha(x, \pm v) d\lambda_g(x, \pm w).$$

Notice that this is going to be the measure of all unoriented geodesics which intersect the geodesic $$\alpha$$ transversely. Hence in this local chart around $$\alpha$$ (choosing some orientation for it) we see that this integral is the same as

$$i(\alpha, \lambda_g) = \int_0^{\ell_g(\alpha)} \int_0^\pi \frac{1}{2} \sin(\theta) d\theta dx = \ell_g(\alpha).$$

The result follows. $$\blacksquare$$

Consequently, $$\lambda_g$$ determines the marked length spectrum, in the sense that for every free homotopy class the functional $$\lambda_g^* := i(\cdot, \lambda_g)$$ on the space of free homotopy classes gives us the marked length spectrum. So if two Liouville currents are the same, i.e. $$\lambda_{g_1} = \lambda_{g_2}$$, then the corresponding marked length spectrums must be the same (up to isometry). This gives us the following way of restating Otal-Croke's theorem (matching the observation above).

**Theorem:** Given two negatively curved metrics $$g_1, g_2$$ on $$M$$, if $$\lambda_{g_1} = \lambda_{g_2}$$ then $$g_1 \simeq g_2$$.

Another way to think of this is that there is a function taking (negatively curved) metrics and giving Liouville currents. Otal-Croke's theorem says that for surfaces this function on the space quotiented out by the equivalence relation given by isometries is injective.

We also wish to study $$i(\lambda_g, \lambda_g)$$. There's an interesting property here as well.

**Observation:** We have that $$i(\lambda_g, \lambda_g) = \frac{\pi}{2} A(g)$$, where $$A(g)$$ is the area.

We omit the proof here and refer the reader to [this article](https://people.math.harvard.edu/~ctm/home/text/class/harvard/275/05/html/home/course/course.pdf) instead (the calculation isn't hard, it's just tedious to write out).
