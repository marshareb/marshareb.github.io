---
layout: post
title: Metrization Theorem
tag: functional-analysis
categories: ["Functional Analysis"]
---

In my last post (found [https://marshareb.github.io/Metrization-and-Flow/](here)) I mentioned going through the metrization theorem. Today, I'll actually go through and prove the result.

We recall a few definitions ahead of time. A *topological vector space* is a vector space $$X$$ (over a field $$F$$ which is either $$\mathbb{R}$$ or $$\mathbb{C}$$) equipped with a topology $$\tau$$ such that the singletons are closed sets and scalar multiplication $$F \times X \rightarrow X$$, $$(\alpha, x) \mapsto \alpha x$$ and addition $$ X \times X \rightarrow X$$, $$(x,y) \mapsto x+y$$ are continuous.

A topological vector space $$(X,\tau)$$ (where we generally drop the $$\tau$$ and just call $$X$$ a topological vector space) is said to be *metrizable* if there exists a metric $$d : X \times X \rightarrow \mathbb{R}_{\geq 0}$$ such that the topology of open balls generates $$\tau$$. Recall as well that the metric $$d$$ *generates* the topology $$\tau$$ if the open balls
$$B_\epsilon(x) = \{ y : d(x,y) < \epsilon\}$$
is a base for the topology. This should be sufficient to get us started for the theorem. A *neighborhood of the origin* is an open set containing the 0 vector, and a *local base* is a set of neighborhoods of the origin such that for every open set $$U$$ which contains the origin, we have that there is an open set $$V$$ in our local base with $$V \subset U$$. In essence, we can write every open set $$U$$ containing the origin as a union of sets from our local base.

# Metrization theorem statement

Let $$(X, \tau)$$ be a topological vector space. Then $$X$$ is metrizable if and only if $$X$ has a countable local base.

To prove this, we will actually break it up into two parts. There is a very trivial direction (the forward direction) and a not so trivial direction (the backwards direction, or the converse). However, while we prove the converse, we'll actually get a lot more for free.

# Proof of metrization theorem

Before getting too far, we remark that if we can find a local base (meaning a base for the set of neighborhoods centered at the origin), then we have a base for the entire topology. This follows by noting that the translation map

$$ T_\gamma : X \rightarrow X$$

given by

$$ T_\gamma(x) = x + \gamma$$

is a homeomorphism. So if we have a local base $$ \mathcal{B}(0)$$, we can shift it via this homeomorphism to get a base centered at a different point, and then taking the union of translates of these open sets we get a base for the entire topology. In essence, we reduce the problem of looking at the whole topology to looking at open neighborhoods at the origin.

Now, assuming that $$X$$ is metrizable, we get a metric $$d$$ which is compatible with our topology, meaning that the open balls $$B_\epsilon(0)$$ are a local base. Notice that we can refine this local base to the open balls $$B_{1/n}(0)$$ for $$n$$ a natural number greater than or equal to 1. This is a countable local base, and so we are done.

For the backwards direction, we need to get a little trickier. Note that a set $$U \subset X$$ is said to be *balanced* if we have that, for all $$\alpha \in F$$ our underlying field with
$$ \mid\alpha\mid = 1 $$, we get $$\alpha U \subset U$$.

## Theorem

If $$X$$ is a topological vector space with a countable local base, then there is a metric $$d$$ on $$X$$ such that:

(a) $$d$$ is compatible with the topology of $$X$$.

(b) the open balls centered at $$0$$ are balanced, and

(c) $$d$$ is invariant, meaning

$$d(x+z, y+z) = d(x,y).$$

## Proof

Step 1: Every neighborhood of 0 contains a balanced neighborhood of 0.

Let $$U$$ be a neighborhood of 0 in $$X$$. Scalar multiplication is continuous, so there is a $$\delta > 0$$ and a neighborhood of 0 $$V$$ so that $$\alpha V \subset U$$ whenever $$ \mid \alpha\mid < \delta $$. Taking the union over all $$\alpha V$$, we have a balanced neighborhood of 0.

As a consequence of this, for every local base we can find a local balanced base.

Step 2: For every neighborhood of 0 in $$X$$, say $$W$$, there is a neighborhood $$U$$ of $$0$$ which is symmetric and which satisfies $$U + U \subset W$$.

We have 0 + 0 = 0, and addition is continuous, so we can find neighborhoods $$V_1, V_2$$ so that $$V_1 + V_2 \subset W$$. Taking

$$ U = V_1 \cap V_2 \cap (-V_1) \cap (-V_2),$$

we have the desired set.

Step 3: By assumption, we have a countable local base $$\{U_n\}$$. By steps 1 and 2, we can refine this to get a countable local base $$\{V_n\}$$ where

$$V_{n+1} + V_{n+1} + V_{n+1} + V_{n+1} \subset V_n.$$

Step 4: Consider the dyadic rational numbers; i.e. consider the set $$D$$ consisting of rational numbers $$r$$ of the form

$$ r = \sum_{n=1}^\infty c_n(r) 2^{-n},$$

where the digits $$c_j(r)$$ are either 0 or 1, and only finitely many are 1. Note that $$ 0 \leq r < 1$$.

Put $$A(r) = X$$ if $r \geq 1$, and for $$r \in D$$ define

$$A(r) = c_1(r) V_1 + c_2(r) V_2 + \cdots. $$

Note that each of these sums are actually finite.

Step 5: Define the function

$$f(x) = \inf \{ r : x \in A(r)\}$$ for $$x \in X$$. Note that $$f(x) \leq 1$$ for all $$ x \in X$$, so that the infimum is finite.

Step 5: We show that if $$r,s$$ and $$r+s$$ are in $$D$$ and $$c_n(r) + c_n(s) \neq c_n(r+s)$$ for some $$n$$, then for the smallest such $$n$$ where this happens we have that $$c_n(r) = c_n(s) = 0$$ and $$c_n(r+s) = 1$$. This is just a consequence of the fact that

$$ r = \sum c_n(r) 2^{-n},$$

$$ s = \sum c_n(s) 2^{-n}$$,

and so if $$c_n(r) = c_n(s) = 1$$, then we have that their sum is 2. Since these are dyadic numbers, this shifts the coefficient to $$2^{-n+1}$$. Thus, we must have the inequality happens when $$c_n(r) = c_n(s) = 0$$ and $$c_n(r+s) = 1$$.

Step 6: We establish

$$A(r) + A(s) \subset A(r+s)$$

for all $$r,s \in D$$. If $$r +s \geq 1$$, then we are done, since $$A(r+s) = X$$. Thus, we consider $$r+ s < 1$$. Put $$\alpha_n = c_n(r)$$, $$\beta_n = c_n(s)$$, and $$\gamma_n = c_n(r+s)$$. Let N be the smallest integer for which $$\alpha_N + \beta_N \neq \gamma_N$$. Then by Step 5, we see $$\alpha_N = \beta_N = 0$$ and $$\gamma_N = 1$$, giving us

$$A(r) \subset \alpha_1 V_1 + \cdots + \alpha_{N-1}V_{N-1} + V_{N+1} + V_{N+2} + \cdots$$

$$ \subset \alpha_1 V_1 + \cdots + \alpha_{N-1}V_{N-1} + V_{N+1} + V_{N+1},$$

where here the last subset is due to the construction in Step 3. We have an analogous result for $$A(s)$$, and we see that since $$\alpha_n + \beta_n = \gamma_n$$ for $$n < N$$, we get

$$A(r) + A(s) \subset \gamma_1 V_1 + \cdots + \gamma_{N-1}V_{N-1} + V_N \subset A(r+s).$$

Step 7: Since every $$A(s)$$ contains 0, we see that Step 6 says

$$ A(r) \subset A(r) + A(t-r) \subset A(r + (t-r)) = A(t).$$

Thus, $$\{A(r)\}$$ is a POSET by inclusion.

Step 8: We claim that Step 7 gives us that

$$ f(x+y) \leq f(x) + f(y).$$

We assume without loss of generality that $$f(x) + f(y) < 1$$, since otherwise this trivially follows. Fixing $$\epsilon > 0,$$ there exists r and s dyadic rational numbers such that $$f(x) < r, f(y) < s, r + s < f(x) + f(y) + \epsilon.$$ So $$x \in A(r), y \in A(s)$$ and Step 6 implies that $$x + y \in A(r+s)$$. So

$$ f(x+y) \leq r + s < f(x) + f(y) + \epsilon.$$

Step 9: Since the $$A(r)$$ are balanced, we get $$f(x) = f(-x)$$, and $$f(0) = 0$$. So $$d(x,y) = d(y,x).$$ If $$x \neq 0$$, then $$x \notin V_n = A(2^{-n})$$ for some $$n$$, so $$f(x) \geq 2^{-n} > 0$$. Hence, we see that $$d(x,y) = 0$$ if and only if $$x = y$$. Step 9 establishes the triangle inequality, since

$$d(x,y) = f(x-y) = f(x - z + z - y) \leq f(x - z) + f(z-y) = d(x,z) + d(y,z).$$

Finally, translation invariance follows from $$d(x+z,y+z) = f(x+z-y-z) = f(x-y) = d(x,y).$$

Step 10: We need to show that this generates the topology. The open balls centered at $$0$$ are the sets

$$B_\delta(0) = \{x : d(x,0) < \epsilon\} = \{x : f(x) < \delta\} = \bigcup_{r < \delta} A(r).$$

To prove this is a local base, it suffices to show that for small enough $$\delta$$, we have $$B_\delta(0) \subset V_n$$. This just follows from choosing $$\delta < 2^{-n}.$$ Each $$A(r)$$ is balanced, so $$B_\delta(0)$$ is balanced, and so we have all the desired properties. Q.E.D.
