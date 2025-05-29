---
layout: post
title: Effective density of closed orbits for SFTs
tag:  dynamics
categories: ["Dynamics"]
---

In this post, we discuss the density of closed orbits of a prescribed length for an suspension flow of a shift of finite type.

# Question and proof

To start, we are going to work with a suspension flow. Let $$\sigma : X_A \rightarrow X_A$$ be a shift of finite type, and let $$r$$ be some roof function (which will be Holder for us). We will be assuming that this shift of finite type is *not* reversible for simplicity. Recall that the metric on $$X_A$$ is given by

$$d(x,y) = e^{-n}, \text{ where } x_k = y_k \text{ for all } k < n \text{ and } x_n \neq y_n.$$

Note that the constant is generally $$2$$, but it will be convenient to choose $$e$$. We denote the corresponding suspension flow by $$\sigma^t : X_A^r \rightarrow X_A^r$$. Given a metric on $$X_A$$, we have an induced metric on $$X_A^r$$ given by

$$ d((x,t), (y,s)) = d(x,y) + \mid t-s \mid.$$

Recall that a closed orbit for the flow is of the form $$\gamma(t) := \sigma^t(x)$$ for some $$x \in X_A^r$$, where $$\gamma(T) = \gamma(0)$$ for some $$T > 0$$. We denote the period of the orbit by $$\ell(\gamma) > 0$$. Let $$P_\sigma$$ be the collection of all closed orbits for $$\sigma^t$$. Apriori, this is a collection of curves on the space, and so to help our discussion we introduce the notation $$\Gamma_\sigma := \{x \in X_A^r : x = \gamma(t) \text{ for some } \gamma \in P\}$$. In other words, $$\Gamma_\sigma$$ is the image of all of the closed curves coming from $P_\sigma$.

It is well-known that $$\Gamma_\sigma$$ is dense in $$X_A^r$$. One can see this using transitivity of the flow along with the Anosov closing lemma, however, let's show this to be true using equidistribution. If $$C \subseteq X_A^r$$ is an open set, then let's write $$\chi_C$$ as a function on $P_\sigma$, where $$\chi_C(\gamma)$$ is the integral of $$\chi_C$$ over the curve $$\gamma$$. If $$\mu$$ is the measure of maximal entropy, then one way of interpreting equidistribution is that we have

$$ \lim_{T \rightarrow \infty} \frac{\sum_{\gamma \in P(T)} \chi_{C}(\gamma)}{\# P(T)} = \mu(C) > 0. $$

Note that this implies there is some $$T > 0$$ large enough so that $$\chi_C(\gamma) = 1$$, and this gives us density.

A more interesting question is the rate at which it is becoming dense. We now introduce four more bits of notation:
- We write $$P_\sigma(T)$$ (and respectively $$\Gamma_\sigma(T)$$) for all the closed orbits whose period is less than or equal to $$T$$.
- Given $$x \in X_A^r$$, let $$B_\eta(x)$$ be the ball of radius $$\eta$$ which is centered at $$x$$.
- Given a set $$A \subseteq X_A^r$$, we say that it is **$$\eta$$-dense** if for every $$x \in X_A^r$$, we have that  $$B_\eta(x) \cap A \neq \varnothing$$.
- For $$T > 0$$, let

$$ \eta(T) := \inf\{ \eta > 0 : \Gamma(T) \text{ is } \eta \text{-dense}\}.$$

We can now state our question more precisely as follows: Can we say anything about the asymptotics of $$\eta(T)$$?

**Proposition:** There are constants $$C, \delta > 0$$ such that $$\eta(T) \leq C e^{-\delta T}$$.

**Proof:** First, we identify $$X_A$$ with the subset $$X_A \times \{0\}$$ in $$X_A^r$$; we will call this the **base**. Now, given $$\gamma \in P(T)$$, notice that there must be some $$t$$ such that $$x = \gamma(t) \in X_A$$. In light of this, we want to reduce our study to the base. If $$x$$ corresponds to a closed orbit with period at most $$T$$, then we must have that

$$ \sum_{k=0}^{n-1} r(\sigma^k(x)) \leq T \text{ and } \sigma^n(x) = x.$$

We write

$$r^n(x) := \sum_{k=0}^{n-1} r(\sigma^k(x)).$$

We now reduce our study to the collection of points

$$A_T := \{x \in X_A : r^n(x) \leq T \text{ and } \sigma^n(x) = x \text{ for some } n\}.$$

Notice that this is simply the projection of $$\Gamma(T)$$ to the base $$X_A$$ along the flow lines. Since things are isometric in the flow direction, if this set is $$\eta$$-dense in $$X_A$$, then we deduce that $$\Gamma(T)$$ is $$\eta$$-dense in $$X_A^r$$. Recall that the topology of $$X_A$$ is given through cylinders; given an finite sequence $$(x_1, \ldots, x_n)$$, we write

$$[x_1, \ldots, x_n] := \{y \in X_A : y_i = x_i \text{ for } 1 \leq i \leq n\}.$$

We call $$n$$ the **length** of the cylinder, and we say the cylinder is **admissible** if $$[x_1, \ldots, x_n] \neq \varnothing$$. Let $$\mathcal{C}(n)$$ be the collection of all admissible cylinders. In this language, we now have that a set $$A$$ is $$e^{-n}$$-dense if $$A \cap C \neq \varnothing$$ for all $$C \in \mathcal{C}(n)$$. In particular, this shows that we are looking for the largest $$n$$ such that $$\text{Fix}(\sigma^n) \subseteq A_T$$; we can then translate this to density through the above.

Using the variational principle and the fact that orbits have zero entropy, we can deduce that for every $$x \in \text{Fix}(\sigma^n)$$, we have

$$P(r) \geq \frac{r^n(x)}{n}.$$

Notice that this shows if $$n P(r) \leq T$$, then $$r^n(x) \leq T$$ for all such $$n$$. Thus, the largest $$n$$ which does the trick satisfies $$n \geq \lfloor T/P(r) \rfloor$$. In particular, this shows that $$A_T$$ is $$e^{-\lfloor T/P(r) \rfloor}$$-dense, and we deduce that $$A_T$$ is $$O(\exp(-T/P(r)))$$-dense, or in other words, $$\eta(T) \leq C\exp(-T/P(r))$$ for some constant $$C > 0$$. $$\square$$


## Follow up remarks

- A simpler bound is to simply use the supremum of $$r$$ instead of the pressure (but follow the same logic in the above). In some cases, this bound is better. The real goal at the end is to try to find an optimal bound, which preferably only depends on the dynamics of the flow.
- Using Markov partitions, the same result should carry over to Anosov flows.
- It might be interesting to see how this would follow from an effective equidistribution result (in the vein of Kadyrov in [here](https://arxiv.org/abs/1608.01767), and later improved by O'Hare in [here](https://arxiv.org/abs/2310.20027)). In particular, I suspect that one can use the Gibbs property and this effective equidistribution to get better control on the $$\delta$$ in the above theorem, but I still don't think it will get us the optimal rate.
