---
layout: post
title: Poincare Recurrence Part 2
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss a variation on [Poincare Recurrence](https://marshareb.github.io/An-Ergodic-Theorem/).

# Problem

## Set Up

We follow Einsiedler and Ward Exercise 2.2.1. Let $$(X, \mathcal{M}, \mu, T)$$ be a measure-preserving system (meaning $$\mu(T^{-1}(A)) = \mu(A)$$ for every $$A$$ measurable). Suppose we only know that $$\mu$$ is a *finitely additive measure*, meaning that if $$\{A_i\}_{i=1}^n$$ is a finite collection of disjoint measurable sets, then

$$ \mu \left( \bigcup_{i=1}^n A_i \right) = \sum_{i=1}^n \mu(A_i).$$

Notice we really only require disjoint almost everywhere, meaning that pairwise the measure of their intersection is $$0$$. We're also implicitly assuming that $$\mu$$ is a probability measure as well, so $$\mu(X) = 1$$.

Under this set up, our goal is to prove that if $$\mu(A) > 0$$, then there exists $$n \leq 1/\mu(A)$$ so that $$\mu(A \cap T^{-n}(A)) > 0$$. In other words, we have a bound on return time for a measurable set.

## Solution

Assume that $$\mu(A \cap T^{-n}(A)) = 0$$ for every $$1 \leq n \leq 1/\mu(A)$$. To help with notation, let $$N := 1/\mu(A)$$. Let

$$B_i := \bigcup_{j=0}^{i} T^{-j}(A).$$

Observe that

$$\mu(B_1) = \mu(A \cup T^{-1}(A)) = \mu(A) + \mu(T^{-1}(A)) = 2 \mu(A)$$

since we have these sets are almost everywhere disjoint. We claim by induction that for $$i < N$$ if

$$ \mu(B_i) = \sum_{j=0}^i \mu(T^{-j}(A))$$

then

$$ \mu(B_{i+1}) = \sum_{j=0}^{i+1} \mu(T^{-j}(A)).$$

It suffices to check that $$T^{-i-1}(A)$$ is almost everywhere disjoint from $$T^{-j}(A)$$ for $$0 \leq j \leq i$$. Here we can use the fact that $$T$$ is measure preserving, so

$$ \mu(T^{-j}(A) \cap T^{-i-1}(A)) = \mu(A \cap T^{j-i-1}(A)).$$

Since $$0 \leq j < i+1$$ we see $$-(i+1) \leq j-i-1 < 0$$, so by assumption this is $$0$$. Thus

$$ 0 \leq \mu(B_i \cap T^{-i-1}(A)) \leq \sum_{j=0}^i \mu(T^{-j}(A) \cap T^{-i-1}(A)) = 0,$$

and hence

$$ \mu(B_{i+1}) = \mu(B_i) + \mu(T^{-i-1}(A)) =  \sum_{j=0}^{i+1} \mu(T^{-j}(A)).$$

Using induction and the fact that $$T$$ is measure preserving, we see that

$$ \mu\left( \bigcup_{i=0}^N T^{-i}(A) \right) = (N+1) \cdot \mu(A) > 1,$$

which is impossible. This gives us that for some $$1 \leq n \leq 1/\mu(A)$$ we must have $$\mu(A \cap T^{-n}(A)) > 0$$.


# References

(i) [Ergodic Theory with a view towards Number Theory](https://link.springer.com/book/10.1007/978-0-85729-021-2)
