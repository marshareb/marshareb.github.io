---
layout: post
title: Entropy and Goldstine
tag: functional-analysis dynamics
categories: ["Weekly Update"]
---

In this post, we discuss topological entropy and weak topologies.

# Personal Life

I ended up having to drive back to my home town to vote in the primaries, so I was not able to do as much work as I wanted to this week.
Other than traveling the week has mostly been filled with meetings.

## Dynamics

The more interesting thing I covered this week was topological entropy. Broadly speaking, topological entropy is a
quantity which measures how well we can finely distinguish orbits in a finite amount of time. It turns out there are a few
equivalent definitions for topological entropy, which I'll try and cover quickly.

The discussion will be focused on discrete dynamical systems, and specifically we'll stick to compact metric spaces. So let
$$(X,d)$$ be a compact metric space, $$ f : X \rightarrow X$$ a continuous map. The goal is to see how well we can distinguish
distinct orbits, so we will define a new metric to try to measure this. Let

$$ d_n^f(x,y) = \max \{ d(f^i(x), f^i(y)) : 0 \leq i \leq n-1\}.$$

This measures the maximum distance between the orbit starting at $$x$$ and the orbit starting at $$y$$. If we can
distinguish these orbits at some finite time, we should have that this quantity is positive.

It's an easy exercise to check that this is still a metric. We have:
* $$ d_n^f(x,y) \geq 0$$ since $$d \geq 0$$.
* For each i, $$d(f^i(x), f^i(y)) = d(f^i(y), f^i(x))$$ so $$d_n^f(x,y) = d_n^f(y,x).$$
* For each i, the triangle inequality is satisfied by the above kind of argument.
* We have $$d_n^f(x,y) = 0 $$ if and only if $$ x = y$$, since $$d_n^f(x,y) = 0$$ if and only if $$d(x,y) = 0$$ if and only if $$x = y$$.


So we get a sequence of increasing metrics. We can create open balls for each $$n$$ for the topology of $$d_n^f$$ by writing

$$ B_f(x, \epsilon, n) = \{ y \in X : d_n^f(x,y) < \epsilon\}.$$

This metric is sometimes referred to as the *Bowen-Dinaburg metric*.

A set $$E \subset X$$ is said to be *$$(n, \epsilon)$$-spanning* if we have

$$ X \subset \bigcup_{x \in E} B_f(x, \epsilon, n).$$

The cardinality of this set is, in some sense, measuring the number of initial conditions
which approximates the behavior up to time $$n$$ of any initial condition up to $$\epsilon$$. The first definition
for topological entropy is to try to find the *minimal* number of initial conditions which captures this behavior up to any time $$n$$. So we define the *minimal $$(n,\epsilon)$$-spanning set* to be the set $$E \subset X$$ of minimal cardinality so that it is an $$(n,\epsilon)$$-spanning set.

Let $$S_d(\epsilon,n,f)$$ be the cardinality of the minimal $$(n,\epsilon)$$-spanning set.
The goal now is to measure the exponential growth rate of this quantity; i.e. the exponential
growth rate of the number of initial conditions which captures the behavior of the dynamical system up to $$\epsilon$$ fineness.
Relating this back to our original goal, we see that this will in some sense capture the worst case scenario for distinguishing orbits in a finite amount of time. We define the quantity

$$h_d(f,\epsilon) := \limsup_{n \rightarrow \infty} \frac{1}{n} \log(S_d(f,\epsilon,n)).$$

Heuristically, this is monotone with respect to $$\epsilon$$ since a smaller $$\epsilon$$
requires more balls to cover the set, so this will only get bigger. Thus we can define

$$h_d(f) := \lim_{\epsilon \rightarrow 0^+} h_d(f,\epsilon).$$

This is going to be the *topological entropy* for the dynamical system $$f$$.

There are a few natural questions one asks about this quantity. First, we want this to be
a topological invariant, which means it needs to be invariant under the *topology*, not the metric itself.
In other words, if there is another metric which generates the same topology as the original metric, then
we want the topological entropy with respect to both of these metrics to be the same. It turns out this is the case.

The gist is that these metrics generate the same topology, so an easy exercise says that there are constants $$c, C > 0$$ so that

$$ cd' \leq d \leq Cd'.$$

Using the inequality, we see that any $$(n,\epsilon)$$-spanning set with respect to $$d$$ will be a $$(n,\delta(\epsilon))$$-spanning set with respect to $$d'$$ for some $$\delta(\epsilon) > 0$$, and the same argument works for the other direction. So taking the limit, we have

$$ h_{d'}(f) \geq \lim_{\epsilon \rightarrow 0^+} h_{d'}(f, \delta(\epsilon)) \geq h_d(f)$$

and vice versa. So the quantities are actually equal, and this is really a statement about the topology and not the metric.

Consequently, a very easy exercise using the pullback metric shows that the topological entropy is
an invariant under topological conjugacy (i.e. conjugating by a homeomorphism). These together show that this quantity
is really a topological invariant; if two topological spaces are equivalent with respect
to homeomorphisms, then they share the same topological invariant.

We can give an alternative definition for topological entropy. Let $$D_d(f, \epsilon, n)$$ be the minimal number of sets whose diameter in the metric $$d_n^f$$ is at most $$\epsilon$$ and whose union covers $$X$$. An easy argument (but long, so omitted) shows that using a similar exponential growth definition for topological entropy using this quantity gives us the same definition.

The final definition involves using *$$(n,\epsilon)$$-separated sets*, which are sets
defined to be a collection of points in $$X$$ which are pairwise $$d_n^f$$ distance at least $$\epsilon$$. Denoting the maximum number of points by the quantity $$N_d(f,\epsilon,n)$$ and defining topological entropy by the exponential growth of this quantity, we get the same definition again. So all three quantities can be used to calculate topological entropy. Next time, I hope to have some examples to explore involving this.

## Functional Analysis

I'm still reading chapter 3 in Rudin. Part of the week was devoted to reading about Goldstine's theorem, which is a fun theorem showing the weak* compactness of the embedded unit ball in the double dual. Briefly, we define the *dual space* of a topological vector space $$X$$ to be the space of continuous linear functionals on $$X$$ (a linear functional is a linear function from the topological vector space into its underlying scalar field). Given a set of linear functionals on $$X$$, we can define a new topology called the *weak topology* by giving it the weakest topology which makes these linear functionals continuous. If the set is nice, say it separates points (meaning if $$x \neq y$$, there is some $$f$$ in the set with $$f(x) \neq f(y)$$) and is a vector space, then the weak topology will be locally convex, and the dual space with respect to the topology will be exactly the vector space of functions.

Notice that we can embed $$J : X \hookrightarrow X**$$ (the double dual) by sending $$J(x)$$ to its evaluation map; i.e. for all $$ \varphi \in X*$$ we have $$J(x)(\varphi) = \varphi(x)$$. This embedding will separate points, and we can define a weak topology on $$X*$$ using $$J(X)$$. This topology will be called the weak* topology. It is an easy exercise to show that this is the topology of pointwise convergence.

There are a bunch of interesting results one can show involving the weak and weak* topology, but I'll postpone doing that until next week.
