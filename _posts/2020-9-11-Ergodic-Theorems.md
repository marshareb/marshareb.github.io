---
layout: post
title: Poincare Recurrence
tag: dynamics
categories: ["Dynamics"]
---

In this post, I hope to outline one of the big theorems in ergodic theory -- Poincare recurrence.

# Personal Life

I sadly don't think I have enough time to pick back up the weekly update series, but I hope to occasionally write some posts about some things I've learned.

One of the classes I'm taking this semester is on ergodic theory. I'm hoping to fill the holes in my ergodic knowledge with this. The books we're following are Halmos' "Lectures on Ergodic Theory," Peter Walters' "An Introduction to Ergodic Theory," and Karl Petersen's, "Ergodic Theory."


# Basic Definitions

Recall that we're dealing with measure spaces in ergodic theory, so we'll generally be looking at a measure space $$(X, \mathcal{M}, \mu)$, abbreviated $$(X,\mu)$$ or just $$X$$. We want to study the dynamics of this system under some transformation which preserves the structure of this space, so we'll take $$ T : X \rightarrow X$$ a *measure preserving transformation*, meaning $$\mu(T^{-1}(E)) = \mu(E)$$ for all measurable $$E \subseteq X$$ and $$T$$ is measurable. In general, we study finite measure spaces in ergodic theory, and in particular probability measure spaces (meaning $$\mu(X) = 1$$). Note that without loss of generality we can just look at probability measure spaces, since normalizing the measure still gives us a measure.

One last definition we'll need is recurrent. Let $$E \subseteq X$$ be a measurable subset. A point $$x \in E$$ is *recurrent* if $$T^n(x) \in E$$ for some positive integer $$n$$. A natural extension to the definition is a point is *infinitely recurrent* if $$T^n(x) \in E$$ for infinitely many positive integers $$n$$.

**Question:** If we assume $$(X,\mathcal{M},\mu,T)$$ is a measure preserving system of a probability measure space, $$E \subseteq X$$ a measurable set, and $$x \in E$$ is recurent, is $$x$$ necessarily infinitely recurrent?

# Poincare Recurrence

The moral of this theorem is that studying individual points in a space is hard, but studying subsets is easier. If we translate this into physics, for a chaotic system it may be difficult (if not impossible) to predict the dynamics of an individual particle; however, what we could do instead is try to predict the probability a particle will land inside of a certain subset of our space.

Terry Tao in his blog (found [here](https://terrytao.wordpress.com/2008/01/30/254a-lecture-8-the-mean-ergodic-theorem/)) gives an interesting interpretation of this theorem. If we burn a piece of paper in a closed system, then there are arbitrarily small perturbations of the initial conditions which tell us that if we wait long enough, the paper will reassemble itself! He then goes on to explain why this doesn't contradict the second law of thermodynamics (something beyond my understanding, but interesting nonetheless).

Let's now state the theorem.

**Theorem:** If $$(X,\mathcal{M},\mu,T)$$ is a measure preserving system of a probability measure space and $$E$$ is a measurable set, then almost every point of $$E$$ is recurrent.

The proof is surprisingly easy. Let $$F$$ be the set of points in $$E$$ which never returns to $$E$$. Assume this set has positive measure. We claim that $$F \cap T^{-n}(F)$$ is empty for each $$n$$. For $$n=1$$, we see that if $$ x \in F \cap T^{-1}(F)$$, then $$x \in F \subseteq E$$ and $$T(x) \in F \subseteq E$$. This is impossible, since we assumed all points in $$F$$ never returned to $$E$$, so there can be no such point. This same kind of idea works for all $$n \geq 1$$, and furthermore this also shows that $$T^{-n}(F) \cap T^{-m}(F)$$ is empty for each $$n, m \geq 1$$. So we get that $$\{T^{-n}(F)\}_{n \geq 1}$$ is an infinite collection of sets of equal measure (since $$T$$ is measure preserving) which are all pairwise disjoint, so by countable additivity of the measure we have that $$\mu(X)$$ is infinite, contradicting the fact that we were working on a finite measure space.

Terry Tao in his blog outlines what seems to be a stronger result (since it actually gives us some bounds). Here is the idea:

**Theorem:** If $$(X, \mathcal{M}, \mu, T)$$ is a measure preserving system, $$E \subseteq X$$ a measurable set of positive measure, then

$$ \limsup_{n \rightarrow \infty} \mu(E \cap T^n(E)) \geq \mu(E)^2.$$

In particular, this says $$\mu(E \cap T^n(E)) \geq \mu(E)^2$$ for infinitely many $$n$$. The gist of this is to use Cauchy-Schwarz on characteristic functions.

**Warning:** The theorem is **false** if we do not have a finite measure space (see: Walters, page 26). Consider $$(\mathbb{Z}, \mathcal{P}(\mathbb{Z}), \mu)$$, where $$\mu$$ is counting measure. Consider the set $$E = \{0\}$$. This is a set with positive measure, since $$\mu(E) = 1$$. If we take $$T : \mathbb{Z} \rightarrow \mathbb{Z}$$ defined by $$T(x) = x+1$$, then this is measure preserving and we get a measure preserving system. Notice that we can actually write what $$F$$ looks like:

$$ F = E \cap \bigcap_{n \geq 1}T^{-n}(E^c).$$

Notice

$$T^{-1}(E^c) = T^{-1}(E)^c = \{-1\}^c.$$

This same idea applies for all $$n \geq 1$$, so

$$F = \{0\} \cap \bigcap_{n \geq 1} \{-n\}^c = \{0\} = E.$$

So the whole set $$E$$ never returns to $$E$$ under any amount of iterations. Note that if you don't like this explanation, Walters gives an alternate way of thinking about it.
