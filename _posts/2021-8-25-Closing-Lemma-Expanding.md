---
layout: post
title: The Closing Lemma for Expanding Maps
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss a variation on the closing lemma.

# Set Up

The goal of this article is to prove a version of the closing lemma for expanding maps on the circle. We'll first recall some key definitions:

(1) A $$C^1$$ map $$f : S^1 \rightarrow S^1$$ is said to be **expanding** if $$ \mid f'(x) \mid > 1$$ for every $$x \in S^1$$.

(2) Let $$(x_i)_{i=1}^\infty$$ be a sequence of points in $$S^1$$. We say that this is an **$$\epsilon$$-orbit** if for each $$k$$ we have

$$d(f(x_k), x_{k+1}) < \epsilon.$$

Now recall (or see **Theorem 6.4.15** in Katok and Hasselblatt) that the closing lemma states that if we have an Anosov diffeomorphism $$f : M \rightarrow M$$, then there exists constants $$C, \epsilon_0 > 0$$ so that for any $$\epsilon < \epsilon_0$$ and any periodic $$\epsilon$$-orbit $$(x_0, \ldots, x_m)$$ there is an honest periodic point $$y \in M$$ with $$f^m(y) = y$$ so that for $$0 \leq k \leq m-1$$ we have

$$d(f^k(y), x_k) < C \epsilon.$$

The proof can be found in either Katok and Hasselblatt or [my notes](https://marshareb.github.io/files/dossier_finaldraft.pdf). The gist is to use a contracting mapping principle argument to find the periodic point.

# Result and Proof

**Theorem:** Let $$f : S^1 \rightarrow S^1$$ be a $$C^1$$ expanding map. There exists a $$C, \epsilon_0 > 0$$ so that if $$\epsilon < \epsilon_0$$ and $$(x_0, \ldots, x_m)$$ is a periodic $$\epsilon$$-orbit, then there exists a $$y \in S^1$$ so that $$d(f^k(y), x_k) < \epsilon$$. Furthermore this $$y$$ is unique and periodic.

**Proof:** This basically will just be the solution to Problem 24 in [this](https://marshareb.github.io/files/Dynamics.pdf). As seen in **Proposition 3.2.3** in Katok and Hasselblatt, there is a constant $$\delta$$ sufficiently small so that

$$d(x,y) < \delta \implies d(f(x), f(y)) < D \delta,$$

where $$D$$ is some constant depending on the expansion. Thus for sufficiently small $$\delta > 0$$, we have

$$f(\overline{B_\delta(x)}) = \overline{B_{D\delta}(f(x))}.$$

Hence we have the property that if $$d(f(x), y) \leq D \delta$$ then there is a $$z \in \overline{B_\delta(x)}$$ with $$f(z) = y$$. We're going to first ignore the fact that $$(x_0, \ldots, x_m)$$ is periodic and just extend it to an infinite $$\epsilon$$-orbit. Fix very small $$\epsilon > 0$$ -- it will be clear in our proof how small we'll need as we go. Let

$$A_n := \{z \in S^1 : f^i(z) \in \overline{B_\epsilon(x_i)} \text{ for } 0 \leq i \leq n\},$$

$$A := \bigcap_{n \geq 0} A_n.$$

We check that the $$A_n$$ are non-empty and closed. We can then deduce by the finite intersection property that $$A \neq \varnothing$$. We will then show that $$A$$ is just one point, and we'll be done.

Let's show that the $$A_n$$ are non-empty. Let $$z_n = x_n$$. By making $$2\epsilon$$ small enough, we can use our observation above to deduce that there is some $$z_{n-1} \in \overline{B_{\epsilon/2}(x_{n-1})}$$ with $$f(z_{n-1}) = x_n$$. Now

$$d(f(x_{n-2}), z_{n-1}) \leq d(f(x_{n-2}), x_{n-1}) + d(x_{n-1}, z_{n-1}) < \epsilon (1 + 1/2) < 2 \epsilon.$$

Let $$\lambda_j = 2 - 2^{1-j}$$. We can inductively construct $$z_{n-j}$$ so that $$z_{n-j} \in \overline{B_{\lambda_j\epsilon/2}(x_{n-j})}$$ and $$f(z_{n-j}) = z_{n-j+1}$$. Notice this gives us a point $$z_0$$ with

$$d(f^{n-j}(z_0), x_{n-j}) \leq \epsilon \text{ for } 0 \leq j \leq n.$$

So each $$A_n$$ is non-empty. It's easy to see that the continuity of $$f$$ will give us that $$A_n$$ is closed -- just take sequences. Finally if $$x,y \in A$$, then $$d(f^i(x), f^i(y)) \leq 2\epsilon$$ for all $$i$$, which if we take $$\epsilon$$ small enough forces $$x = y$$ since it's expanding.

Suppose $$z$$ is the point in $$A$$. We have that $$f^m(z)$$ and $$z$$ will both lie in $$A$$, so this uniqueness forces $$f^m(z) = z$$, which means we have a periodic point. This finishes the proof.

The other thing to note here is that we can actually get a variation of **Proposition 6.4.16** from Katok and Hasselblatt. Namely if $$x,y \in S^1$$ satisfy the property that $$d(f^k(x), f^k(y)) < \delta$$ for $$\delta$$ sufficiently small and $$0 \leq k \leq n$$ then we have that

$$d(f^k(x), f^k(y)) \leq C \alpha^{k, n-k} (d(x,y) + d(f^n(x), f^n(y))),$$

where $$\alpha$$ comes from the Anosov exponents. To deal with this in just the expanding case, we have that as long as $$\delta$$ is small we can get

$$d(f^k(x), f^k(y)) \leq \alpha^k d(x,y),$$

where here we have $$\alpha = \max_{x \in S^1} \mid f'(x) \mid.$$ The same result then follows easily. We can get the so-called "improved closing lemma" as well. Let's state this one, since it's useful.

**Theorem:** If $$f : S^1 \rightarrow S^1$$ is an expanding map with $$\alpha = \max_{x \in S^1} \mid f'(x) \mid$$, then there exists a $$\delta, C > 0$$ so that if $$d(f^k(x), x) < \delta$$ for $$k = 0, \ldots, n$$ then there is a periodic point $$y$$ so that $$f^n(y) = y$$ and

$$d(f^k(y), f^k(x)) < C \alpha^k d(f^n(x), x).$$

**Proof:** Notice that we can apply the closing lemma as long as $$\delta$$ is small since

$$ d(f^k(x), f^{k+1}(x)) \leq d(f^k(x), x) + d(x, f^{k+1}(x)) < 2 \delta.$$

This gives us a periodic point $$y$$ with

$$d(f^k(x), f^k(y)) < \delta \text{ for } 0 \leq k \leq n.$$

Now as long as we make sure $$\delta$$ is small here, we can apply the above result to get

$$ d(f^k(x), f^k(y)) < \alpha^k (d(x,y) + d(f^n(x), y)).$$

At the cost of some constant $$C$$ we get

$$ d(f^k(x), f^k(y)) < C \alpha^k d(f^n(x),x),$$

as desired.


# References

(i) [Introduction to the Modern Theory of Dynamics by Katok and Hasselblatt](http://cosweb1.fau.edu/~jmirelesjames/ODE_course/katok.pdf)

(ii) [A Survey of the Livschitz Theorem](https://marshareb.github.io/files/dossier_finaldraft.pdf)

(iii) [Dynamics Problems](https://marshareb.github.io/files/Dynamics.pdf)

(iii) [Various shadowing properties for positively expansive maps by Sakai](https://core.ac.uk/download/pdf/82334468.pdf)
