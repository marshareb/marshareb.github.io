---
layout: post
title: Recitation Seventeen
tag: [MA1172]
---

In this recitation, we covered Taylor series and calculus with Taylor series.

# Taylor Series

A **Taylor series** is a power series which arises as a limit of Taylor polynomials. In a formula, the Taylor series for $$f(x)$$ centered at $$x=a$$ is given by

$$ \lim_{n \rightarrow \infty} p_n(x) = \sum_{k=0}^\infty \frac{f^{(k)}(a)}{k!}(x-a)^k.$$

If $$f$$ is infinitely differentiable at a point, then this formula makes sense, however it doesn't really approximate anything meaningful. For example, take the function

$$ f(x) = \begin{cases} 1 \text{ if } -1 < x < 1 \\ 0 \text{ if } x \leq -1 \text{ or } x \geq 1. \end{cases}$$

It's easy to see $$f$$ is infinitely differentiable at $$x=0$$, and its Taylor series will be just $$1$$. However, it is also clear that $$f(x) \neq 1$$. So while this locally did a good job, globally this is a bad approximation. On the other hand, if $$f(x)$$ is infinitely differentiable on an interval, then we showed that the Taylor series actually converges to the function on that interval. It's clear we need to restrict to functions satisfying this property if we want to meaningfully study Taylor series as alternative ways of expressing functions.

As an aside, if the center $$a$$ of a Taylor series is zero, then we call it a **Maclaurin series**.

We've already discussed some Taylor series. For example, since sine is infinitely differentiable, we can write

$$\sin(x) = \sum_{k=0}^\infty \frac{(-1)^k}{(2k+1)!} x^{2k+1}.$$

We can do a similar thing with cosine:

$$\cos(x) = \sum_{k=0}^\infty \frac{(-1)^k}{(2k)!} x^{2k}.$$

I recommend trying to calculate the Maclaurin series of $$e^x$$ on your own.

# Calculus and Taylor Series

Here's a powerful theorem that we will be using a lot.

**Theorem:** Let

$$f(x) = \sum_{k=0}^\infty a_k (x-a)^k$$

be a function defined by a power series with radius of convergence $$R$$. Then $$f(x)$$ is continuous and differentiable on $$(c-R, c+R)$$, and we have

$$ f'(x) = \sum_{k=1}^\infty a_k \cdot k \cdot (x-a)^{k-1},$$

with radius of convergence $$R$$, and

$$ \int f(x)dx = C + \sum_{k=0}^\infty a_k \frac{(x-c)^{k+1}}{k+1},$$

with radius of convergence $$R$$. We can use this trick to integrate hard functions.
