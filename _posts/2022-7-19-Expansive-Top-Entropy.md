---
layout: post
title: Topological Entropy and Expansive maps
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss a calculation involving topological entropy and expansive maps.

# Set Up

Recall that there are a few definitions for the topological entropy of a dynamical system on a compact metric space $$ f: X \rightarrow X$$. We'll go through them now. First, it is useful to have the so-called **Bowen metric**. This is a metric defined by

$$d_n^f(x,y) := \max_{0 \leq i \leq n} d(f^i(x), f^i(y)).$$

In some sense, this is the metric which measures the distance between finite orbit segments. Open balls with respect to this metric will be defined by

$$ B_f(x, \epsilon, n) := \{y \in X \ | \ d_n^f(x,y) < \epsilon\}.$$

Next, there are a few kinds of sets we care about. The first of which is an $$(n,\epsilon)$$-spanning set. We say that $$E$$ is an **$$(n,\epsilon)$$-spanning set** if we have

$$X \subseteq \bigcup_{x \in E} B_f(x,\epsilon,n).$$

On the other end of the spectrum is an $$(n,\epsilon)$$-separated set. We say that a set $$E$$ is **$$(n,\epsilon)$$-separated** if for every $$x,y \in E$$ with $$x \neq y$$ we have $$d_n^f(x,y) \geq \epsilon$$. Let $$S_d(f,\epsilon,n)$$ be the minimal cardinality of an $$(n,\epsilon)$$-set. Then we can define the topological entropy as

$$ h(f) := \lim_{\epsilon \rightarrow 0^+} \limsup_{n \rightarrow \infty} \frac{1}{n} \log S_d(f,\epsilon,n).$$

As an alternative, if we let $$D_d(f,\epsilon,n)$$ be the minimum number of sets whose diameter in the $$d_n^f$$ metric is at most $$\epsilon$$ and whose union covers $$X$$, then we also have

$$h(f) = \lim_{\epsilon \rightarrow 0^+} \limsup_{n \rightarrow \infty} \frac{1}{n}\log D_d(f,\epsilon,n).$$

Finally, if we let $$N_d(f,\epsilon,n)$$ be the cardinality of the largest $$(n,\epsilon)$$-separated set, then we also have

$$h(f) = \lim_{\epsilon \rightarrow 0^+} \limsup_{n \rightarrow \infty} \frac{1}{n} \log N_d(f,\epsilon,n).$$

We would like to establish a bound involving the topological entropy of an expansive map. Recall that a continuous map $$f : X \rightarrow X$$ is expansive if there is a constant $$\delta > 0$$ such that if $$d(f^n(x), f^n(y)) < \delta$$ for all $$n \geq 0$$, then $$x = y$$.

# Result

Define

$$p(f) := \limsup_{n \rightarrow \infty} \frac{1}{n} \log \# P(n),$$

where

$$P(n) := \{x \in X \ | \ f^n(x) = x\}.$$

Then we'd like to show that $$p(f) \leq h(f)$$ for expansive maps. This turns out to be an easy argument. Let $$f : X \rightarrow X$$ be an expansive map with expansivity constant $$\delta$$. let $$x,y \in P(n)$$ with $$x \neq y$$. Notice that

$$d_n^f(x,y) = \max_{0 \leq i \leq n} d(f^i(x), f^i(y)) \geq \delta.$$

If this was less than $$\delta$$, then we see that $$d(f^k(x), f^k(y)) < \delta$$ for all $$k \geq 0$$ by periodicity, so we would have $$x = y$$, a contradiction. Thus we see that $$P(n)$$ is an $$(n,\delta)$$-separated set. In particular, it is $$(n,\epsilon)$$ separated for all $$0 < \epsilon \leq \delta.$$ Taking $$\epsilon$$ sufficiently small, we see that

$$\# P(n) \leq N_d(f,\epsilon,n)$$

by maximality, hence taking log and limits we get the desired inequality.
