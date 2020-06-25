---
layout: post
title: Metrization Theorem
tag: functional-analysis dynamics
categories: ["Weekly Update"]
---

In this post, I discuss a little about moduli and equivalences (see Katok & Hasselblatt 2.1) and a little on duality in Banach spaces (see chapter 4 of Rudin).

# Personal Life

Nothing is really new beyond my readings (both for fun and for work) and running. Next week is July 4th, which I plan to take off to spend time with my family one last time before classes start. Since we might be potentially teaching in person in the fall, I figured I will become a new vector for the disease and so will have to continue my isolation outside of work. We'll see.

# Dynamics

I've been trying to parse through Katok & Hasselblatt Section 2.1, which focuses on smooth conjugacy and moduli for maps. The goal, as they state, is to try to figure out what properties are invariant under a change of coordinates (which, in terms of topology, is a conjugation by homeomorphisms). Depending on what invariants are preserved, the idea is to introduce equivalence relations between dynamical systems according to the change of coordinates. As is the general theme in mathematics, the goal with this is to try to push problems into an easier setting to understand, or to use this tool as a way to make broad statements on dynamical systems satisfying specific conditions.

I think this week I'll review what a smooth structure is, and next week I'll explore more on what Katok and Hasselblatt are talking about.

Here, I'll take $$M$$ and $$N$$ to be manifolds, although it is never specified in the book. Generally we'll be looking at maps $$f : M \rightarrow M$$, $$g : N \rightarrow N$$ which are $$C^r$$ maps, meaning that they admit at least $$r$$ derivatives and their $$r$$th derivative is continuous. Let's recall a little bit about manifolds before stumbling forward (we follow Lee's Smooth Manifolds for this).

Recall a (topological) manifold is a topological space $$M$$ which satisfies a few properties:
* $$M$$ is [Hausdorff](https://en.wikipedia.org/wiki/Hausdorff_space).
* $$M$$ is second-countable, meaning we have a countable basis for the topology of $$M$$.
* $$M$$ is locally Euclidean, meaning for all $$x \in M$$, there is a neighborhood $$U$$ of $$x$$ with the property that $$U$$ is homeomorphic to an open subset of $$\mathbb{R}^n$$. Call $$n$$ the local dimension of $$x$$.
* For all $$x \in M$$, the local dimension is $$n$$ (i.e. it is constant).

This third/fourth property tells us that we have a sort of coordinate chart. That is, locally our space looks just like a $$\mathbb{R}^n$$. Specifically, a coordinate chart is a pair $$(U, \varphi)$$ where $$U \subset M$$ is open, $$\varphi : U \rightarrow V \subset \mathbb{R}^n$$ a homeomorphism with $$V$$ open. $$U$$ is then a coordinate neighborhood for each of its points. Since $$V \subset \mathbb{R}^n$$, we note that $$\varphi(p) = (x_1(p), \ldots, x_n(p))$$, where $$x_i : U \rightarrow \mathbb{R}$$ is defined by $$x_i = \pi_i \circ \varphi$$, $$\pi_i : \mathbb{R}^n \rightarrow \mathbb{R}$$ defined by the projection onto the $$i$$th coordinate.

If we assume $$M$$ is a manifold, each of its points are covered by coordinate charts, so in particular we have a collection $$\{(U_x, \varphi_x)\}_{x \in M}$$ where $$M \subset \bigcup_{x \in M} U_x$$ and $$\varphi_x$$ are homeomorphisms, and $$(U_x, \varphi_x)$$ is a coordinate chart of $$x \in M$$. This collection gives us an *atlas* for our manifold, which we call $$\mathcal{A}$$.

We want to differentiate functions $$f : M \rightarrow N$$, where $$M$$ and $$N$$ are manifolds. However, derivatives really only exist in Euclidean spaces (defined via limits). Our spaces locally look like Euclidean spaces, so this is a good start, but what if I had two different charts for a point $$p \in M$$, say $$(U, \varphi)$$ and $$(V, \psi)$$, and we have that these charts look *drastically* different? Furthermore, even if these agreed, what if $$f(p) \in N$$ had two different charts which drastically disagree? The derivatives with respect to these different charts would be different, which kind of invalidates the fact that the derivative should be a statement about the point, not the chart and the point. We could try and fix this by saying that we can take a derivative with respect to a specific chart and point, but then we don't get coherence between points. So the derivative isn't *really* telling us anything at this point.

To solve this issue, we need some sort of coherence. That is, the charts on $$M$$ and $$N$$ are playing nice with each other, and then the function $$f$$ is playing nice with these charts as well. This is where smooth structures come in (recall what [smooth](https://en.wikipedia.org/wiki/Smoothness) means).

Between two charts $$(U, \varphi)$$ and $$(V,\psi)$$ on a manifold $$M$$, we have a transition map defined by $$\psi \circ \phi^{-1} : \phi(U \cap V) \rightarrow \psi(U \cap V)$$. It is a homeomorphism (being the composition of homeomorphisms). Furthermore, the transition map is such that $$\psi \circ \phi^{-1} : \mathbb{R}^n \rightarrow \mathbb{R}^n$$, so we can (possibly) take a derivative of this! We call $$U$$ and $$V$$ smoothly compatible if the transition map is a diffeomorphism or if $$U$$ and $$V$$ are disjoint.

We expand our definition of atlas. We say an atlas is a *smooth atlas* if any two charts in the atlas are smoothly compatible with each other. Consider two (smooth) atlases $$\mathcal{A}$$, $$\mathcal{B}$$ on $$M$$. We will give a partial ordering by saying $$\mathcal{A} \leq \mathcal{B}$$ if and only if all of the coordinate charts in $$\mathcal{A}$$ are in $$\mathcal{B}$$ (so containment). A *maximal atlas* is one where it is not properly contained in any other smooth atlas (so it is the largest you can get). We sometimes call this maximal smooth atlas the *smooth structure*, since this determines smoothness on our manifold.

Given a smooth atlas on a manifold, you can explicitly construct a unique smooth structure associated to it. So a smooth atlas uniquely determines a smooth structure on our manifold. If we only care about $$C^r$$ structure, just replace smooth throughout with $$C^r$$.

Since every smooth atlas is associated (uniquely) to a maximal atlas, we sometimes refer to the smooth structure just by an atlas. It is an easy exercise to show that two smooth structures are equivalent if their union is a smooth structure (if their union is a smooth structure, they are contained in the same maximal smooth atlas which is unique).

We now show that this wasn't all pointless by constructing two different smooth structures on the real lines. For a smooth homeomorphism $$f : \mathbb{R} \rightarrow \mathbb{R}$$, we can induce a smooth structure by just taking $$(\mathbb{R}, f)$$. For example, if we take the identity, this is clearly smooth (being a polynomial) and it is clearly a homeomorphism (its the identity, after all) so we get a smooth structure $$(\mathbb{R}, \text{Id})$$. Similarly, if we take $$f(x) = x^3$$, this is smooth (being a polynomial) and it is a homeomorphism (we have inverse $$x^{1/3}$$), so we get a smooth structure $$(\mathbb{R}, f)$$. Are these smooth structures the same?

Well, by the observation above, we take the union of these two atlases and check whether it is smooth. So examine $$\{(\mathbb{R}, \text{Id}), (\mathbb{R}, f)\}$$. To check this is smooth, we need to check that the transition maps are smooth. The transition maps here are just $$f \circ \text{Id}^{-1} = f$$ and $$\text{Id} \circ f^{-1} = f^{-1}$$. Recall $$f^{-1}(x) = x^{1/3} =: g(x)$$. We claim this is *not* smooth at the origin. To see this, we note $$g'(x) = (1/3)x^{-2/3}$$. At the origin, we have an issue since we're dividing by $$0$$, so this cannot be smooth on the entire real line. So this is not a smooth structure, hence these two smooth structures are distinct!

So we've got smooth structures, let's take the time to look at smooth maps between smooth manifolds. A map $$F : M \rightarrow N$$ is said to be *smooth* if we have the following property: For all $$p \in M$$, there exists a coordinate chart $$(U,\varphi)$$ around $$p$$ in $$M$$ and a coordinate charts $$(V, \psi)$$ around $$F(p)$$ in $$N$$ such that we have $$F(U) \subset V$$ and $$\psi \circ F \circ \phi^{-1} : \phi(U) \rightarrow \psi(V)$$ is a smooth map. Diffeomorphisms are defined in the obvious way: it is a smooth map with a smooth inverse (with respect to this definition).

Since a manifold is essentially defined via it's atlas, if we have different smooth structures on a manifold then we can view these as different manifolds. Diffeomorphisms provide us the necessary equivalence between these smooth structures. That is, two smooth structures are said to be *equivalent* if there is a diffeomorphism between them (as manifolds). It is a (difficult) exercise to show that all smooth structures on the real line are equivalent (so even though they differ, they really aren't that different).

The question is now can we find two different smooth structures on a manifold which aren't essentially the same? Milnor in 1956 said yes. The 7-dimensional sphere admits a smooth structure which is not equivalent to the standard smooth structure (giving rise to exotic smooth structures). This is where [Hopf fibrations](http://math.uchicago.edu/~may/REU2015/REUPapers/McEnroe.pdf) really come in.

So we have all this smooth structure talk, but where am I going with it in terms of dynamics? The goal here is to explore what a modulus is. I'll set up a few more definitions and leave the rest to next time.

For a (compact) $$C^r$$ manifold $$M$$, consider $$C^m(M,M)$$ to be the space of maps $$f : M \rightarrow M$$ which are $$C^m$$, where here $$0 \leq m \leq r$$. Equipped on this space is the $$C^r$$ topology, which is defined by the metric

$$ \max_{0 \leq j \leq m}\sup_{(U, \varphi), (V,\psi) \in \mathcal{A}}  \sup_{x \in U} \| D^j (\psi \circ f \circ \varphi^{-1})(x) - D^j (\psi \circ g \circ \varphi^{-1})(x) \|$$

where $$D^j$$ denotes taking the $$j$$th derivative. Since the space is compact, we can cover it with finitely many charts, so the supremum in the middle is really a max.

We say two $$C^r$$ maps $$f : M \rightarrow M$$, $$g : N \rightarrow N$$ are $$C^m$$ *equivalent* (where $$m \leq r$$) if there is a $$C^m$$ diffeomorphism $$h : M \rightarrow N$$ with

$$ f = h^{-1} \circ g \circ h.$$

The idea behind a modulus is measuring how much you fail to satisfy a condition.

# Functional Analysis

Here we study the dual space of a Banach space. Recall a space $$X$$ is said to be *Banach* if it is a normed topological vector space which is complete (meaning Cauchy sequences converge). The (algebraic) dual of a Banach space, denoted $$X^* $$, is the space of continuous linear functionals $$\varphi : X \rightarrow \mathbb{F}$$ (where $$\mathbb{F}$$ is the underlying field -- we generally take this to be $$\mathbb{R}$$ since I prefer the real numbers).

Since we have a normed vector space, continuity between Banach spaces has a nice definition. That is, if $$X$$ and $$Y$$ are Banach spaces, then a map $$T : X \rightarrow Y$$ is continuous iff it is bounded (meaning $$\|Tx\| \leq \|x\|$$). It turns out this is also sufficient if we drop completeness and just look at $$X$$ and $$Y$$ normed vector spaces. We denote the space of bounded linear functions (sometimes called operators) between $$X$$ and $$Y$$ as $$B(X,Y)$$. We will also sometimes examine the bounded operators on $$X$$ to itself, which we will denote by $$B(X)$$.

It turns out that we can make $$B(X,Y)$$ a normed vector space. To do this, we define the operator norm by

$$ \|T\| = \sup \{ \|Tx\| : \|x\| = 1\}.$$

There are a few other equivalent definitions, but for the most part this is the one I like. One just needs to show this is a norm (which is an easy exercise). It turns out that if $$Y$$ is Banach, we get $$B(X,Y)$$ is also Banach with respect to this norm. To see this, if $$(T_n) \subset B(X,Y)$$ is a Cauchy sequence, then

$$ \|T_n x - T_m x\| \leq \|T_n - T_n x\| \text{ for all } x \in X, \|x\| = 1.$$

So $$(T_n x) \subset Y$$ is a Cauchy sequence. Since $$Y$$ is Banach, it converges. Define a map $$T : S \rightarrow Y$$ by

$$ T(x) = \lim_{n \rightarrow \infty} T_n(x),$$

where $$S \subset X$$ is the unit sphere ($$S = \{x \in X : \|x\| = 1\}$$). Define $$T(0) = 0$$, and note that for all $$x \in X$$ with $$\|x\| \neq 0$$ (i.e. all $$x \neq 0$$, since it is a norm), we can normalize to get $$x/\|x\| \in S$$. So we have

$$ T \left( \frac{x}{\|x\|} \right) = \lim_{n \rightarrow \infty} T_n \left( \frac{x}{\|x\|} \right).$$

Each $$T_n$$ is linear, and limits are linear, so we really have

$$ T \left( \frac{x}{\|x\|} \right) = \frac{1}{\|x\|} \lim_{n \rightarrow \infty} T_n(x),$$

or

$$ \|x\| T \left( \frac{x}{\|x\|} \right) = \lim_{n \rightarrow \infty} T_n(x).$$

We can uniquely extend $$T$$ to a linear function, so after relabeling we get

$$ T(x) = \lim_{n \rightarrow \infty} T_n(x)$$

for all $$x \in X$$. It is then an easy exercise to show that $$T_n$$ converges to $$T$$ in the operator norm, so it is complete. Noting $$X^* = B(X, \mathbb{F})$$, and $$\mathbb{F}$$ will always be complete, we get that $$X^* $$ equipped with this norm is a Banach space too.

We can take double duals, meaning we dualize the dual. These are the continuous linear functionals on the continuous linear functionals, so the $$\varphi \in X^{**}$$ which satisfy $$\varphi(T) \in \mathbb{R}$$. Let $$J : X \rightarrow X^{**}$$ be defined by $$J(x)(T) = T(x)$$. It is easy to see this is a linear function, and since $$X^*$$ separates points we actually get that it is an injective linear functional. So we can embed $$X$$ into $$X^{**}$$.

Rudin goes on to talk about nice properties of quotients with dual spaces and annihilators, but maybe the more important thing is the existence of an adjoint. We write $$x^* \in X^{*}$$, $$x \in X$$,

$$ \langle x, x^* \rangle = x^*(x).$$

Suppose $$T : X \rightarrow Y$$ a bounded linear function. For $$y^* \in Y$$, we can write

$$ \langle Tx, y^* \rangle = y^*(T(x)).$$

The *adjoint* is defined to be the unique linear function $$T^* : Y^* \rightarrow X^*$$ so that

$$ \langle Tx, y^* \rangle = \langle x, T^* y^* \rangle.$$

The existence and uniqueness are just working through definitions. We actually get the adjoint is bounded, and actually we get

$$ \|T^*\| = \|T\|.$$

So even better than bounded, we know exactly what the norm of it is. Adjoints are useful in a lot of contexts, but the reason they were introduced here is that we have a theorem which says the following: For all conditions stated as above ($$X$$, $$Y$$ Banach, $$T$$ bounded between them) the following are equivalent:
* $$\text{Im}(T)$$ is closed.
* $$\text{Im}(T^*)$$ is weak*-closed.
* $$\text{Im}(T^*)$$ is norm-closed.

Recall that norm-closed sets are not always weak*-closed, so this is a significant statement. The advantage of this is the following result: $$T$$ is surjective if and only if $$T^*$$ is injective and $$\text{Im}(T^*)$$ is norm-closed. So the adjoint has this sort of inverse relation with respect to injectivity and surjectivity.

The other major property discussed in this chapter was compact operators. Let $$U = \{x \in X : \|x\| < 1\}$$ be the open unit ball. An operator is said to be *compact* if the closure of $$T(U)$$ in $$Y$$ is compact. Equivalently, $$T$$ is compact if $$T(U)$$ is totally bounded (using completeness), and equivalently $$T$$ is compact if for every bounded sequence $$(x_n) \subset X$$ contains a subsequence $$(x_{n_j}) \subset X$$ with the property that $$(Tx_{n_j})$$ converges to a point in $$Y$$. These equivalences are sometimes the easier thing to prove (particularly the last one in my limited experience).

Since we're doing infinite dimensional linear algebra, the definition of an eigenvalue and the definition of the spectrum of a linear function needs to be modified. The spectrum of $$T,$$ denotes $$\sigma(T)$$, is the collection of scalars $$\lambda$$ such that $$T - \lambda I$$ is not invertible, meaning one of the two things happens:
* $$T - \lambda I$$ is not surjective.
* $$T - \lambda I$$ is not injective.

If $$T - \lambda I$$ is not injective, then $$\lambda$$ is an *eigenvalue*. The difference here is that I'm used to the spectrum just being all of the eigenvalues, and us not having to worry about surjectivity issues. The *eigenspace* corresponding to that eigenvalue is $$\text{ker}(T - \lambda I)$$.

Rudin goes on to prove a bunch of results on compact operators, highlighting that the goal is to look at the spectrum of compact operators. I don't really know the value of this yet (though maybe I should based on the dynamics experience), but I'll leave that exploration to next week.
