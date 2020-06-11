---
layout: post
title: Entropy and Krein-Milman
tag: functional-analysis dynamics
categories: ["Weekly Update"]
---

In this post, we explore more on topological entropy (Katok & Hasselblatt section 3.2) and discuss the Krein-Milman theorem (Rudin chapter 3).

# Personal Life

I've picked up Diablo 3 on the Switch thanks to the summer sale and am hoping to play some of that with my girlfriend. Otherwise the schedule has been running in the morning, math during the day, and a brief respite before bed and starting over.

# Dynamics

Last week we gave a few different ways for calculating topological entropy (briefly). This week we try using it on
an example.

## Lipschitz Topological Entropy

**Remark:** I use $$\| \cdot \|$$ for absolute value, since MathJax has issues with absolute values. Sorry for the confusion.

Let $$(X,d)$$ be a metric space (usually compact), $$f : X \rightarrow X$$ a map.
The map $$f$$ is said to be *Lipschitz* with Lipschitz constant $$M \geq 0$$ if we have

$$ d(f(x), f(y)) \leq M \cdot d(x,y).$$

It is a very easy exercise to deduce a Lipschitz map is continuous, so we are dealing with a more stringent case than the usual continuous function from a compact metric space to itself. Recall that we are going to equip our metric space with a new metric

$$ d_n^f(x,y) = \max\{ d(f^i(x), f^i(y)) : 0 \leq i \leq n\}.$$

One of our definitions was concerned with $$(n,\epsilon)$$-spanning sets. Recall that $$E \subset X$$ is said to be such a set if

$$ X \subset \bigcup_{x \in E} B_f(x, \epsilon, n)$$

where

$$ B_f(x,\epsilon, n) = \{ y \in X : d_n^f(x,y) < \epsilon\}$$

is the ball of radius $$\epsilon$$ around our orbit of $$x$$ up to time $$n$$. Defining $$S_d(\epsilon, n, f)$$ to be the cardinality of the minimal $$(n,\epsilon)$$-spanning set, we defined topological entropy as

$$ h(f) = \lim_{\epsilon \rightarrow 0^+} \limsup_{n \rightarrow \infty} \frac{1}{n} \log(S_d(f,\epsilon,n)).$$

So keep in mind our goal is to use this definition for topological entropy.

For $$(X,d)$$ a compact metric space, let $$b(\epsilon)$$ be the minimum cardinality of covering $$X$$ by $$\epsilon$$-balls. In other words,

$$ b(\epsilon) = \min \left\{ \| E \| : X \subset \bigcup_{x \in E} B_\epsilon(x) \right\}.$$

Note that the minimum is fine to take instead of an infimum since our space is compact. We define the *ball dimension of X* as

$$ D(X) := \limsup_{\epsilon \rightarrow 0} \frac{b(\epsilon)}{\| \log(\epsilon)\|}.$$

We will denote by $$L(f)$$ the Lipschitz constant of $$f$$. Recall that for a metric space, we have an equivalent definition for calculating $$L(f)$$, which is

$$ L(f) := \sup_{x \neq y} \frac{d(f(x), f(y))}{d(x,y)}.$$

The gist is that we can get an upper bound on topological entropy based on these two quantities. In other words, the theorem is that if $$f : X \rightarrow X$$ is a Lipschitz map on a compact metric space, then

$$h(f) \leq D(X) \cdot \max\{0, \log(L(f))\}.$$

To prove this, take $$L > \max\{1, L(f)\}$$. Since the map is Lipschitz, we get

$$ d(f(x), f(y)) \leq L(f) \cdot d(x,y) < L \cdot d(x,y) $$

for all $$x,y \in X$$. Iterating, we get

$$ d(f^m(x), f^m(y)) < L^m \cdot d(x,y).$$

Note

$$B_d(x, L^{-n}\epsilon) = \{ y \in X : d(x,y) < L^{-n}\epsilon\},$$

so

$$ f^m(B_d(x, L^{-n}\epsilon)) = \{ f^m(y) \in X : d(x,y) < L^{-n} \epsilon\}.$$

The map is Lipschitz, so if we take $$f^m(y)$$ in the above set, we have

$$ d(f^m(x), f^m(y)) < L^m d(x,y) < L^{m-n}\epsilon.$$

So for $$ 0 \leq m \leq n,$$ we see that

$$f^m(B_d(x,L^{-n}\epsilon)) \subset B_d(f^m(x), \epsilon).$$

Now examine

$$B_d(x, L^{-n}\epsilon) = \{y \in X : d(x,y) < L^{-n}\epsilon\}.$$

Taking $$y$$ in this set, we see that

$$ d_n^f(x,y) = \max \{ d(f^i(x), f^i(y)) : 0 \leq i \leq n\}.$$

By the above observations, we see that

$$d(f^i(x), f^i(y)) < \epsilon \text{ for all } 0 \leq i \leq n,$$

so

$$B_d(x, L^{-n}\epsilon) \subset B_{d_n^f})(x,\epsilon).$$

The choice of $$n$$ and $$x$$ were arbitrary in the construction. Looking at a minimal $$(n,\epsilon)$$-spanning set, we see that the cardinality of this set is going to be smaller than the minimal number of balls needed to cover $$X$$ with $$L^{-n}\epsilon$$ balls. This gives us the bound

$$ S(f,\epsilon,n) \leq b(L^{-n}\epsilon).$$

Since

$$ \| \log (L^{-n}\epsilon)\| = n \log(L) - \log(\epsilon),$$

we can write

$$ n = \left\| \frac{\log(L^{-n}\epsilon)}{\log(L)} \right\| \left( 1 + \frac{\log(\epsilon)}{\| \log(L^{-n}\epsilon)\|} \right).$$

We can rewrite the right hand side ass

$$ \frac{\| \log(L^{-n}\epsilon) \|}{\log(L)} \left(1 + \frac{\log(\epsilon)}{n\log(L) - \log(\epsilon)} \right) = \frac{\| \log(L^{-n}\epsilon) \|}{\log(L)} \left(1 +O\left(\frac{1}{n} \right) \right).$$

Now we get

$$ \limsup_{n \rightarrow \infty} \frac{\log(S(f,\epsilon,n))}{n} \leq \limsup_{n \rightarrow \infty} \frac{\log(b(L^{-n}\epsilon))}{n}, $$

and using the rewrite for $$n$$ as above, this simplifies to

$$ \limsup_{n \rightarrow \infty} \frac{\log(S(f,\epsilon,n))}{n} \leq \log(L) \limsup_{n \rightarrow \infty} \frac{\log(b(L^{-n}\epsilon))}{\| \log(L^{-n}\epsilon) \|}.$$

Recalling the definition for $$D(X)$$, we are left with

$$h(f) \leq D(X) \log(L) < \infty.$$

The argument can be extended to compact Riemannian manifolds in the obvious fashion (see **Katok & Hasselblatt Corollary 3.2.10**.)

# Functional Analysis

The core idea of Krein-Milman is that in nice examples of convex sets in nice spaces, the set of *extreme points* (to be defined) totally encodes the convex set. This is nice for dynamical systems, since this means we only need to look at behavior on the extreme points to understand the behavior in the convex set (assuming our dynamical system respects the convex behavior).

Let $$X$$ be a topological vector space, $$K \subset X$$ some nonempty subset. Consider $$S \subset K$$. We call $$S$$ an *extreme set* of $$K$$ if no point of $$S$$ is an internal point of any line interval whose endpoints are in $$K$$, except when both endpoints are in $$S$$. Basically, if $$ 0 < t < 1$$, $$x \in K$$, and $$y \in K$$, then

$$ (1-t)x + t y \in S$$

implies  $$x \in S$$ and $$y \in S$$.

The *extreme points* are the extreme sets with just one point. In other words, we say that $$z$$ is an extreme point if, for $$x,y \in K$$, $$0 \leq t \leq 1$$,

$$(1-t)x + ty = z$$

implies either $$t = 0$$ or $$t = 1$$. Rudin denotes the set of all extreme points by $$E(K)$$.

We now assume that $$X$$ is a topological vector space such that its dual $$X^* $$ separates points, and $$K \subset X$$ is a nonempty compact convex set in $$X$$. The **Krein-Milman theorem** says that if $$\text{co}$$ denotes the convex hull of a set, then

$$ K = \overline{\text{co}}(E(K)).$$

That is, $$K$$ is the closed convex hull of its extreme points.

The fact that $$K$$ is convex is a little overkill -- if $$X$$ is locally convex, $$K$$ is a compact subset, then we get

$$ K \subset \overline{\text{co}}(E(K)).$$

Notice that

$$\overline{\text{co}}(K) = \overline{\text{co}}(E(K)).$$

It may be possible that $$\bar{\text{co}}(K)$$ has extreme points outside of $$K$$. The example to show this is a little pathological, but essentially this never happens in a Frechet space (which is where we really live all the time anyways). This is the content of **Milman's theorem**, which says that if $$K$$ is compact and if $$\overline{\text{co}}(K)$$ is also compact, then this can't happen.

The proofs of all of these are fun, however they take a bit of time to set up. Instead of going through the proofs, let's apply Krein-Milman to something interesting. Consider

$$ L^1 = L^1([0,1]) := \left\{ f : [0,1] \rightarrow \mathbb{C} : \|f\|_ {1} = \int_ {[0,1]} |f| < \infty \right\}.$$

Denote by $$K$$ the closed unit ball; i.e.,

$$ K := \left\{f \in L^1 : \|f\|_ {1} \leq 1  \right\}.$$

The goal is to show that this has no extreme points. If $$f$$ were an extreme point, it would live on the surface of this ball; in other words, we would have $$ \|f\|_ {1} = 1$$. Now recalling that the integral is continuous, let

$$F(t) = \int_{[0,t]} |f| .$$

We see $$F(0) = 0$$, $$F(1) = 1$$, so the intermediate value theorem says there is a $$c$$ with $$F(c) = 1/2$$. Let

$$ f_1 = 2 f \chi_{[0,c]},$$

$$ f_2 = 2 f \chi_{[c,1]}.$$

Then

$$ \|f_1\|_ {1} = \int_ {[0,c]} 2 |f| = 1,$$

$$ \|f_2\|_ {1} = \int_ {[c,1]} 2 |f| = 1,$$

so both of these also live on the surface. Notice as well that

$$ \frac{1}{2} (f_1 + f_2) = f,$$

so we can express $$f$$ as a convex combination of values also on the surface. So it is impossible for there to be an extreme point. In other words, $$E(K) = \varnothing.$$

Now, if $$L^1([0,1])$$ were the dual space of some topological vector space, then we could equip it with the weak* topology. Banach-Alaoglu says that this will be weak*-compact (and also other results tell us tat this is a locally convex topological vector space now). Since $$K$$ is compact, convex, nonempty, then Krein-Milman tells us that

$$ K = \bar{\text{co}}(E(K)).$$

But this implies that there is an extreme point, which is a contradiction. So we cannot have that $$L^1([0,1])$$ is the dual space for some topological vector space. In particular, it is for sure not the dual of $$L^\infty([0,1])$$, which based on the pattern for $$L^p([0,1])$$, $1 < p < \infty$$, you would try guessing that. Contrast this as well with the fact that $$\ell^1$$ is the dual of $$c_0$$, the space of bounded sequences vanishing at infinity.

In general, these results tell us that if a topological vector space is going to be the dual of another topological vector space, then the unit ball needs to have extreme points.
