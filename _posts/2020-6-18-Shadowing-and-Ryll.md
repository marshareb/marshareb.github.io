---
layout: post
title: Shadow Orbits and Ryll-Nardzewski (Weekly Update 6)
tag: functional-analysis dynamics
categories: ["Weekly Update"]
---

In this post, we'll explore shadow orbits and Ryll-Nardzewski.

# Personal Life

I've decided I should stop playing the ignorance card when it comes to race and to start reading. The plan is to start following Noname's book club (found [here](https://www.nonamebooks.com/)) as well as try to find a group of people to discuss the readings with. The first book I'll be starting with is [Blood in My Eye](https://en.wikipedia.org/wiki/George_Jackson_(activist)). Maybe this section will be replaced with writing about my thoughts on that.

Otherwise, personally nothing is really new. A lot of running, reading, and trying to balance life with work and not doing a great job of it. There were interesting problems in the dynamics reading course but I spent a lot of time trying to figure them out (and I think I have). I'm hoping this next week will be slower paced.

# Dynamics

The exercise of most interest to me this week is the following:

## Problem
Let $$f : S^1 \rightarrow S^1$$ be the "times two" map on the circle; i.e.

$$ f(x) = 2x \pmod{1}$$

Let $$\epsilon > 0$$ be small (part of the problem is determining *how* small) and let $$(x_i)$$ be a sequence of points with the property that

$$ d(x_{i+1}, f(x_i)) < \epsilon.$$

Prove that there exists an orbit $$f^i(z)$$ such that

$$d(f^i(z), x_i) < 2\epsilon.$$

Prove that such a $$$$z$$$$ is unique.

The idea for proving this is to use a method called *shadowing* (a reference can be found [here](https://core.ac.uk/download/pdf/82334468.pdf)). The idea is that expanding maps in general have this property that, for points which are sufficiently close, we have

$$ d(f(x),f(y)) = m \cdot d(x,y),$$

where $$m$$ is the expanding constant. For the times 2 map, this means

$$ d(f(x), f(y)) = 2 \cdot d(x,y).$$

However, what does sufficiently close mean in this case? Well if the distance between the points is at most $$1/16$$, then we get that the property for sure holds; to show this, you go through a bunch of cases. Basically since the behavior of iterates of points are weird depending on the location, you need to make sure that they are close enough so that they act the same way.

So we've gone and made sure that the points are sufficiently close so that we have this nice property sort of Lipschitz property. We can now abuse this property to work backwards. That is, let's take $$0 < \epsilon < 1/64,$$ (the significance of choosing $$64$$ is that it is sufficiently small; I think you can maybe let it be a little bigger, but I like to be safe) and let's say that we have points $$x, y \in S^1$$ with

$$ d(f(x), y) < \epsilon.$$

The claim is that we can find a point $$z$$ in $$B_{\epsilon/2}(x)$$ with $$f(z) = y$$. Why exactly is this the case? Well, we chose $$\epsilon$$ *really* small, so the advantage of this is that we have this Lipschitzian property I mentioned above. This means that $$f(B_{\epsilon/2}(x)) = B_{\epsilon}(f(x))$$, and we see $$y \in B_\epsilon(f(x))$$, so $$y \in f(B_{\epsilon/2}(x))$$, giving us the desired result.

Let's now use this to work backwards. Define

$$ A_n = \{ z \in S^1 : d(f^i(z), x_i) \leq \epsilon \text{ for } 0 \leq i \leq n\}.$$

The goal is to show that (1) $$A_n \neq \varnothing$$ and (2) $$A_n$$ is closed. If we can do that, this shows that $$A_n$$ is a nonempty compact set. Furthermore, we see that these are *nested* nonempty compact sets. So we can invoke the [FIP](https://en.wikipedia.org/wiki/Finite_intersection_property) to get

$$ A := \bigcap_{n \geq 0} A_n \neq \varnothing.$$

In other words, there is a $$z \in A$$ which satisfies the property that $$f^i(z) \in \overline{B_\epsilon(x_i)}$$ for all $$i$$. This establishes the existence property.

Briefly, let's assume that we can show existence. We need to then show uniqueness. Suppose $$x, y \in A$$. Using the triangle inequality, we have that

$$ d(f^i(x), f^i(y)) \leq 2\epsilon < \frac{1}{32} \text{ for all } i \geq 0.$$

Let $$\delta = d(x,y)$$, and suppose for contradiction that $$x$$ and $$y$$ are distinct. That is, suppose $$\delta > 0$$. Since the property is for all $$i \geq 0$$, we have $$\delta < 1/32$$. Now using our sort of Lipschitzian property, we get

$$ d(f(x), f(y)) = 2\delta < \frac{1}{32}.$$

Since this is sufficiently small, we can keep iterating. We get

$$ d(f^i(x), f^i(y)) = 2^i \delta < \frac{1}{32} \text{ for all } i \geq 0.$$

Notice this implies

$$ \delta < \frac{1}{2^i \cdot 32} \text{ for all } i \geq 0,$$

so we must have $$\delta = 0$$, a contradiction. So if a point exists, it must be unique.

Let's now establish existence. For each $$n$$, we'll construct a sequence $$(z_i^{(n)})$$ which satisfies the desired properties. Let $$z_n^{(n)} = x_n$$ preemptively. By construction, we have

$$ d(f(x_{n-1}), x_n) < \epsilon. $$

By the proposed lemma above, we can find $$z_{n-1}^{(n)} \in B_{\epsilon/2}(x_{n-1})$$ with $$f(z_{n-1}^{(n)}) = z_n^{(n)}$$. Notice now

$$ d(f(x_{n-2}), z_{n-1}^{(n)}) \leq d(f(x_{n-2}), x_{n-1}) + d(x_{n-1}, z_{n-1}^{(n)}) < \frac{3}{2}\epsilon.$$

This is still sufficiently small to invoke our lemma, so we can find $$z_{n-2}^{(n)} \in B_{3\epsilon/4}(x_{n-2})$$ with $$f(z_{n-2}^{(n)}) = z_{n-1}^{(n)}$$. We can continue inductively in this fashion. That is, if we let

$$ \lambda_j = 2 - 2^{1-j},$$

then for $$2 \leq i \leq n$$ we can find $$z_{n-i}^{(n)} \in B_{\lambda_i \epsilon/2}(x_{n-i})$$ with

$$ f(z_{n-i}^{(n)}) = z_{n-i+1}^{(n)} \text{ and } d(f(x_{n-i-1}), z_{n-i}^{(n)}) < \lambda_{i+1}\epsilon < 2\epsilon.$$

That is, it's sufficiently small so we can continue. So there exists $$z_0^{(n)}$$ with the property that for $$0 \leq i \leq n$$,

$$ f^i(z_{0}^{(n)}) = z_{i}^{(n)} \text{ and } d(z_{n-i}^{(n)}, x_{n-i}) \leq \frac{\lambda_i}{2}\epsilon \leq \epsilon.$$

So letting $$z = z_0^{(n)}$$, we have found $$z \in A_n$$. This establishes that $$A_n$$ is nonempty.

The fact that $$A_n$$ is closed is easy. Let $$(z_m) \subset A_n$$ be a sequence with $$z_m \rightarrow z$$. The goal is to show $$z \in A_m$$ as well. Notice for each $$x_i$$, $$0 \leq i \leq n$$, we get

$$ d(f^i(z), x_i) \leq d(f^i(z), f^i(z_m)) + d(f^i(z_m), x_i).$$

For each $$m$$, we have

$$d(f^i(z_m), x_i) \leq \epsilon.$$

Since $$f$$ is continuous with respect to the metric, and compositions of continuous functions remain continuous, we can find sufficiently large $$m$$ so that

$$d(f^i(z), f^i(z_m)) < \kappa$$

for all $$\kappa > 0$$. Putting these facts together, we get

$$ d(f^i(z), x_i) < \kappa + \epsilon.$$

Taking $$\kappa \rightarrow 0$$ gives

$$ d(f^i(z), x_i) \leq \epsilon$$

for $$0 \leq i \leq n$$, and so $$z \in A_n$$ as desired. Thus we have each $$A_n$$ is nonempty and closed, and furthermore nonempty and compact. By the above discussion, we win!

The paper I linked above (another link [here](https://core.ac.uk/download/pdf/82334468.pdf) in case you're lazy) gives much more general results, and I recommend checking it out if this looked interesting to you.

# Functional Analysis

In functional, we've taken a break from Rudin to explore the [Ryll-Nardzewski theorem](https://en.wikipedia.org/wiki/Ryll-Nardzewski_fixed-point_theorem). I'll set up a few definitions first to give the gist of the theorem, but for an actual proof one can look [here](https://www.springer.com/gp/book/9780387001739).

The theorem talks about fixed points, so I guess the starting point should be what is a fixed point. Throughout, $$\mathcal{F}$$ denotes a family of maps of a space $$X$$ into itself. A *fixed point* for $$f$$ is a point $$x_0 \in X$$ with the property that for all $$T \in \mathcal{F}$$, $$T(x_0) = x_0$$.

Now consider $$X$$ a linear topological space. The family is said to be *noncontracting* on $$X$$ if, for any two distinct points $$x, y \in X$$, we have

$$ 0 \notin \overline{\{Tx - Ty : T \in \mathcal{F}\}}.$$

Analytically, we cannot find a net $$(T_n) \subset \mathcal{F}$$ with $$T_n x - T_n y \rightarrow 0$$, or in other words the maps eventually the maps contracting to $$0$$ (hence the name).

In the same setting, we call the family *distal* (coming from "point of attachment", I think) if for any distinct $$x, y \in X$$ there is an open covering of $$X$$, say $$\{V_\alpha\}$$, with the property

$$ Ty \notin \bigcup_\alpha \{V_\alpha : Tx \in V_\alpha\} \text{ for each } T \in \mathcal{F}.$$

In other words, these don't exist in the same open sets. There is a lemma which states that if $$E$$ is a locally convex topological vector space, $$X \subset E$$ is compact, then noncontracting means the same thing as distal. Generally one of these is easier to work with, but conceptually the other is easier to set up.

A pair of theorems (**Theorem 9.3, 9.4** from [here](https://link-springer-com.proxy.lib.ohio-state.edu/book/10.1007%2F978-0-387-21593-8)) by Hahn say that if we let $$C \subset E$$ be a compact convex subset of a locally convex topological vector space, and $$\mathcal{F}$$ a semigroup of continuous affine self maps of $$C$$, then if $$\mathcal{F}$$ is distal on $$C$$ (or on all minimal closed $$\mathcal{F}$$-invariant subsets, which I don't feel like getting into) then $$\mathcal{F}$$ has a fixed point. The goal of Ryll-Nardzewski is to extend this.

The theorem says the following: If $$C$$ is a nonempty weakly compact convex set in a locally convex topological vector space $$E$$, and if $$\mathcal{F}$$ is a semigroup of weakly continuous affine self-maps of $$C$$, then if $$\mathcal{F}$$ is strongly noncontracting on $$C$$, then $$\mathcal{F}$$ has a fixed point.

In other words, we can take *weak* information (we just know the set $$C$$ is weakly compact, the functions are weakly continuous) and we can extract *topological* information on the family (i.e. there is a fixed point). In many of the applications I've found, the advantage of having weak information over strong information is that is easier to check the weak data, so easier to work with.

There are a lot of cool applications of the theorem (most extend far beyond my understanding). One big one is that you can use it to establish the existence of a Haar measure on compact Hausdorff topological groups. A cool reference for that can be found [here](http://aurora.asc.tuwien.ac.at/~funkana/downloads_general/sem_kiesenhofer.pdf) (also the author of this is apparently a famous cyclist, see [here](https://en.wikipedia.org/wiki/Anna_Kiesenhofer)). Another cool application is proving amenability of *weakly almost periodic functions* (the proof of which involves unpacking a lot of jargon, but it seems like a useful result). A good reference for that can be found [here](https://books.google.com/books/about/Weakly_Almost_Periodic_Functions_on_Semi.html?id=diEsAAAAIAAJ) (I believe the first chapter covers almost everything you need to know, but it is dense). It seems like one can extend the result to nonlinear spaces (see [this](https://arxiv.org/pdf/1903.12123.pdf) arxiv paper) but that seems a little beyond my understanding right now.

The theorem overall seems useful to know, but I'm hoping to come back with some good examples of where you can use it in dynamical systems in the future (maybe that's where weakly almost periodic functions comes up).
