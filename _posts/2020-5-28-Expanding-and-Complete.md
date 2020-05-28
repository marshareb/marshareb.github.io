---
layout: post
title: Expanding Maps and Baire Category
tag: weekly-update
categories: ["Weekly Update"]
---

# Personal Life

Monday was Memorial day, so consequently I didn't get as much work done as I wanted. I did end up starting Avatar the Last Airbender, which has been enjoyable to rewatch. I've also finished up the base campaign for Grim Dawn and started the DLC. I'm hoping to get to play that more this upcoming week.

# Dynamics

I attended the Utah working seminar for Ergodic theory, where we covered the unique ergodicity of the horocycle flow. While still a little above my head, the talk was approachable and I feel like I got a good feeling of where I'm heading in terms of dynamical systems/ergodic theory. Ratner theory came up at some point, and after a quick google search I figured this might be an interesting topic to explore in the future. I'm planning on attending the rest of the seminars, so hopefully I'll get more topics to explore out of that.

In terms of Katok reading, I've covered expanding maps, hyperbolic toral automorphisms, and the beginning of symbolic dynamical systems. Based on how Katok presented it, I think expanding maps seem to be just things on the circle, so the space we'll be focusing on in this section is

$$ S^1 = \mathbb{R}/\mathbb{Z}.$$

An *expanding map* is a map of the form

$$ E_m(x) = mx \pmod{1}.$$

Unlike the rotation, we see that we lack the property that for all measurable sets $$ A \subset S^1$$ we have $$ \mu(E_m(A)) = \mu(A),$$ where $$\mu$$ here is going to be Lebesgue measure. This is clear since we're doubling the length of intervals. Even though we lack this nice property, we still get that this is a *covering map* of the circle (which, in casual language, means we have a map where the preimage of the circle gives us $$m$$ disjoint copies of the circle). When we explore more on ergodicity in the future, we will learn that this map is also a measure preserving ergodic map, and gives us a little intuition on why we're more concerned with preimages as opposed to images when it comes to the definition of measure preserving.

We wish to ask the usual questions for maps of this form. That is:
* Is this map topologically transitive? (Note that since the circle is a topological group, topologically transitive is equivalent to minimal. So this question, while easier, also gives us the answer of whether the system is minimal.)
* Are periodic points dense? In other words, for every open set $$ A \subset S^1$$, must $$A$$ contain a periodic point for $$E_m$$?
* Is the map *topologically mixing*? In other words, for every two nonempty open sets $$U, V \subset S^1$$, do we have that there exists an integer $$ N$$ so that for all $$ n > N$$, $$f^n(U) \cap V \neq \varnothing$$?
* We can also ask (and answer) the additional question: How many periodic points of period $$n$$ are there?

Since we're working over a nice space (the circle), we get that we can use the following lemma (which is sort of the reason we think about topologically mixing).

**Lemma:** [Lemma 1.4.2 Katok & Hasselblatt] If $$ f : X \rightarrow X$$ is a continuous map of a locally compact separable metric space $$X$$ into itself, then the map $$f$$ is topologically transitive if and only if for any two nonempty open sets $$U, V \subset X$$ there exists an integer $$N$$ such that $$f^N(U) \cap V \neq \varnothing$$.

The forward direction is pretty easy and doesn't require locally compact separable metric space. The converse is not so easy, and there you really utilize the fact that you can find precompact sets to sort of build a point with a dense orbit.

The idea for showing the expanding map is topologically transitive is to convert things to base $$m$$ and look at $$m$$-ary intervals

$$ \Delta_n^k = \left[ \frac{k}{m^n}, \frac{k+1}{m^n}\right].$$

Note that every open interval contains the interval $$\Delta_n^k$$ for $$n$$ large enough and some $$k$$ in the range $$0 \leq k \leq m^n - 1$$. One notes that the expanding map applied to these intervals blow them up, and after applying the map enough times we get

$$ E_m^n(\Delta_n^k) = S^1.$$

Utilizing the above lemma, we get that the map is topologically transitive. Note this also is the gist for how one can show topologically mixing.

To count the number of periodic points, we note that if we view

$$ S^1 = \{ z \in \mathbb{C} : \mid z \mid = 1\},$$

then

$$ E_m(z) = z^m.$$

So a point is periodic with period $$n$$ if

$$E_m^n(z) = z^{m^n} = z \Rightarrow z^{m^n-1} - 1 = 0$$.

So periodic points correspond to the $$m^n-1$$ roots of unity, of which there are exactly $$m^n-1$$ of them. Taking $$n$$ large, we see that these uniformly spread out across the circle, and so we get that every open interval will contain at least one for $$n$$ large enough. Hence, every open set contains a periodic point, so periodic points are dense.

There's more info to extract from the expanding map, but this at least establishes a lot of properties that we care about.

To generalize the expanding map to the two torus, we look at hyperbolic toral automorphisms. The idea here is to take $$A \in \text{SL}(2;\mathbb{Z})$$ (i.e. a matrix with determinant 1 whose coefficients are integers) so that for all $$\lambda \in \text{spec}(A),$$ we have $$\mid \lambda \mid \neq 1$$ (i.e. there is no eigenvalue with absolute value 1). We associate to it a map on the torus, $$F_A : \mathbb{T}^2 \rightarrow \mathbb{T}^2$$ defined by

$$ F_A(x,y) = A(x,y) \pmod{1}.$$

This map shares a lot of properties with the expanding map. That is, this map is:
* Topologically transitive.
* The periodic points are dense.
* Topologically mixing.

The proof of these properties is more involved, so it may be something I come back to later. For now, I'll omit it.

Symbolic dynamical systems is something I would like to write more about, so I'll wait until next week to write about that.

# Functional Analysis

This week was focused on starting and finishing chapter 2 of Rudin's functional analysis on completeness. The focus is on Baire category and all of it's applications (Banach-Steinhaus, open mapping theorem, closed mapping theorem). The gist is to categorize sets on being *topologically* (topologically here is my language) large or small. Sadly this notion doesn't play well with measure (there are meager sets with full measure in the unit interval, for example), but that doesn't matter for our applications.

A set is said to be *nowhere dense* if the interior of its closure is empty. In other words, if $$X$$ is our topological space, the set $$ A \subset X$$ is meager if $$(\bar{A})^{\mathrm{o}} = \varnothing.$$ To recall, a set is said to be *dense* if $$\bar{X} = X$$. The language "nowhere dense" makes sense; if we consider the complement of $$A$$, denote it by $$B$$, we have that $$A$$ is nowhere dense iff $$B$$ contains a dense open set. This follows since

$$ (\bar{A})^\mathrm{o} = \varnothing \iff \overline{B^{\mathrm{o}}} = X,$$

utilizing the fact that $$\bar{A}^c = B^{\mathrm{o}}$$ and a similar equation for interiors and complements.

A set is of the *first category* if it is a countable union of nowhere dense sets. A set is of the *second category* if it is not of the first category.

It might seem like a space should always be of second category in itself based on the definition, however it's not necessarily true. Note that if we consider an infinite-dimensional topological vector space $$X$$, we have that any finite-dimensional subspace $$Y \subset X$$ will be of first category in $$X$$. Every finite dimensional subspace is closed automatically, so it suffices to show that it has empty interior. Suppose without loss of generality it had nonempty interior, so there is some open subset $$ U \subset Y$$ nonempty. Since it's nonempty, we have $$a \in U$$, and so we can shift it to get a neighborhood of the origin $$U-a \subset Y$$. It's still in $$Y$$ since it is closed under translation. Now, for any $$x \in X$$, we have that there exists $$n$$ large so that $$(1/n)x \in U-a$$ (this follows by the absorption property of open neighborhoods around the origin). Since $$Y$$ is a subspace, it is closed under scaling, so $$x \in Y$$. This implies that $$X = Y$$, contradicting that it is a subspace. So if $$X$$ is an infinite-dimensional vector space with a countable Hamel basis, then it is of first category in itself.

Luckily weird examples are hard to come by, which is the content of Baire's theorem. This says that if your space is either a
* complete metric space or
* a locally compact Hausdorff space

then the space is of second category in itself. The actual content of the theorem says that the intersection of every countable collection of dense open subsets of the space is dense, but by taking complements you get that the countable union of nowhere dense subsets can't be the whole space.

To review quickly, a collection of maps $$\Gamma$$ is said to be *equicontinuous* if they are all "simultaneously continuous." In the context of topological vector spaces, this says that for every neighborhood of the origin in $$Y$$, say $$W$$, there exists a neighborhood of the origin $$V \subset X$$ with $$\Lambda(V) \subset W$$ for all $$\Lambda \in \Gamma$$.

The content of the Banach-Steinhaus theorem is that if we consider a collection of continuous maps between topological vector spaces and if the set of all orbits of points in $$X$$ under the action of $$\Gamma$$ is bounded and of second category, then the collection is in fact equicontinuous. Moreover, you get that the collection of all bounded orbits in $$X$$ is the whole space.

Using Baire's theorem, we can deduce some nice corollaries if we assume that our space is an $$F$$-space (recall that this means it has an invariant metric compatible with its topology). For example, a nice theorem is the following.

**Theorem:** [Theorem 2.8 Rudin] If $$\{\Lambda_n\}$$ is a sequence of continuous linear mappings from an $$F$$-space to a topological vector space, $$\Lambda_n : X \rightarrow Y$$, and if

$$ \Lambda x = \lim_{n \rightarrow \infty} \Lambda_n x$$

exists for all $$x \in X$$, then $$\Lambda$$ is continuous.

There are other variants of course, but the spirit in all of these is the same: checking continuity boils down to checking limits on nice sequences.

There's also the open mapping theorem, which says that if $$\Lambda : X \rightarrow Y$$ is a continuous linear map from an $$F$$-space to a topological vector space and the image is of second category, then it is actually a surjective open mapping. In fact, this actually forces $$Y$$ to also be a $$F$$-space. The corollary of this is that if $$\Lambda$$ is a surjective, continuous, linear map from an $$F$$-space to an $$F$$-space, then it is an open map (this is the version I'm most used to). So the open mapping theorem gives us an easy way to check if maps are homeomorphisms.

The closed graph theorem is another theorem concerned with checking continuity. The graph of a map $$f : X \rightarrow Y$$ is the set

$$ \Gamma(f) = \{(x, f(x)) : x \in X\} \subset X \times Y.$$

The gist of the theorem is that if the spaces are $$F$$-spaces, the map is linear, and the graph is closed with respect to the product topology, then the map is actually continuous. Boiling it down, instead of checking that the graph is closed, we often just check that if

$$ \lim_{n \rightarrow \infty} x_n = x, \qquad y = \lim_{n \rightarrow \infty} \Lambda x_n,$$

then $$y = \Lambda x$$. It's easy to check that this property is equivalent to a closed graph (Rudin does most of the work for you).

Overall, while not super interesting material on its own, the section contains a large number of theorems that I expect to see again, so my time will mostly be spent trying to get used to using them in different exercises. A nice post in the future might be exploring some examples (one such example might be looking at distributions).
