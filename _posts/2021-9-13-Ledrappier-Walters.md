---
layout: post
title: The Ledrappier-Walters formula
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss the [Ledrappier-Walters formula](https://www.researchgate.net/publication/243088144_A_Relativised_Variational_Principle_for_Continuous_Transformations).

# Set Up

Throughout, let $$(X,d)$$ be a compact metric space and $$T : X \rightarrow X$$ a continuous map (which is our dynamical system). For $$\delta > 0$$ and $$n \in \mathbb{N}$$ we say a set $$E \subseteq X$$ is **delta separated** if for any $$x \neq y \in E$$ we have

$$ \max_{0 \leq i < n} d(T^i(x), T^i(y)) \geq \delta.$$

Let $$f : X \rightarrow \mathbb{R}$$ be any function and define

$$ f_n(x) := \sum_{i=0}^{n-1} f(T^i(x)).$$

We can define the **exponential accumulation** by

$$S(f, T, \delta, n) := \inf\left\{\sum_{x \in E} \exp(f_n(x)) : E \subseteq X \text{ is a delta separated set} \right\}.$$

The **topological pressure** is then defined as

$$ P(f, T) := \lim_{\epsilon \rightarrow 0} \limsup_{n \rightarrow \infty} \frac{1}{n} \log(S(f,T,\delta,n)).$$

Note that we recover the entropy if we let $$f = 0$$ in the above definition, so

$$ h(T) = P(0,T).$$

One observation to make is that the space of $$T$$-invariant probability measures on $$X$$ is compact (in the weak*-topology) and convex, with extreme points the ergodic measures (this can be found in [Walters](https://www.springer.com/gp/book/9780387951522) book).

The next goal is to define measure theoretic entropy. Recall that a **measurable partition** for a measure space $$(X, \mathcal{M}, \mu)$$ is a collection of measurable subsets $$\xi := \{A_i\}$$ such that the following hold:

(1) $$\mu \left( X \setminus \left(\bigcup_i A_i \right) \right) = 0.$$

(2) $$\mu(A_i \cap A_j) = 0$$ for all $i \neq j$$.

A measurable partition is then a collection of subsets such that they cover $$X$$ almost everywhere and they are almost everywhere disjoint. We will make the additional assumption that $$\mu(A_i) > 0$$ for each $$i$$, which just generally means we ignore the sets of measure $$0$$ in our calculations. All measurable partitions are going to be either finite or countable with finite entropy.

Let $$\xi$$ be a measurable partition. We define the **entropy** of $$\xi$$ to be

$$H_\mu(\xi) := \sum_{i \in I} \mu(A_i) \log(\mu(A_i)).$$

If one doesn't want to ignore zero measure sets in their partition, then we use the same definition with the convention that $$0 \log(0) = 0$$.

We define the **conditional measure** by

$$ \mu(A \mid B) := \frac{\mu(A \cap B)}{\mu(B)}.$$

If we have two measurable partitions $$\xi := \{A_i\}_{i \in I}$$ and $$\eta := \{B_j\}_{j \in J}$$, then we define the **conditional entropy** of $$\xi$$ with respect to $$\eta$$ by

$$ H_\mu(\xi \mid \eta) := -\sum_{j \in J} \mu(B_j) \sum_{i \in I} \mu(A_i \mid B_j) \log(\mu(A_i \mid B_j)).$$

We also define the **join** of two measurable partitions by

$$\xi \vee \eta := \{A \cap B : A \in \xi, B \in \eta\}.$$

If $$\xi$$ is a measurable partition and $$T : X \rightarrow X$$ a measure preserving transformation, then we define the **joint partition** by

$$\xi_{n}^T := \bigvee_{i=0}^{n-1} T^{-i}(\xi).$$

The **measure entropy** of a measure preserving transformation $$T : X \rightarrow X$$ and a measurable partition $$\xi$$ is defined by

$$ h_\mu(T, \xi) := \lim_{n \rightarrow \infty} \frac{1}{n} H(\xi_{n}^T).$$

The **measure entropy** of just $$T$$ is then defined as

$$ h_\mu(T) := \sup\{h_\mu(T,\xi) : \xi \text{ is a finite measurable partition of }X\}.$$

Suppose now $$\pi : X \rightarrow Y$$ is a measure preserving transformation of $$X$$ onto a probability space $$Y$$ so that $$\pi T = S \pi$$ for a measure preserving transformation $$S : Y \rightarrow Y$$. If $$\xi$$ a measurable partition of $$X$$, then we define the **relative entropy** of $$T$$ with respect to $$S$$ and the partition $$\xi$$ as

$$h_\mu(T \mid S, \xi) := \lim_{n \rightarrow \infty} H_\mu(\xi_n^T \mid \pi^{-1}(\epsilon_Y)),$$

where $$\epsilon_Y$$ is the partition of $$Y$$ into points. We define the **relative entropy** of $$T$$ with respect to $$S$$ by

$$h_\mu(T \mid S) := \sup\{ h_\mu(T \mid S, \xi) : \xi \text{ is a finite measurable partition of } X\}.$$

**Claim:** Let $$\xi, \eta$$ be finite partitions of $$X$$. We have

$$h_\mu(T \mid S, \xi) \leq h_\mu(T \mid S, \eta) + H_\mu(\xi \mid \eta \vee \pi^{-1}(\epsilon_Y)).$$

**Proof:** Recall that we have the following nice properties for entropy.

(1) For any finite measurable partitions $$\xi, \eta$$ we have

$$H_\mu(\xi \vee \eta) = H(\xi) + H(\eta \mid \xi).$$

(2) For any finite measurable partitions $$\xi, \eta, \rho$$ we have

$$H_\mu(\eta \vee \xi \mid \rho) + H_\mu(\xi \mid \rho) + H(\eta \mid \xi \vee \rho).$$

Using the above, we see that for fixed $$n$$ we have

$$H_\mu(\xi_n^T \mid \eta_n^T \vee \pi^{-1}(\epsilon_Y)) + H_\mu(\eta_n^T \mid \pi^{-1}(\epsilon_Y)) = H_\mu(\xi_n^T \vee \eta_n^T \mid \pi^{-1}(\epsilon_Y)) \geq H(\xi_n^T \mid \pi^{-1}(\epsilon_Y)).$$

To show our goal, we just need to study the term $$H_\mu(\xi_n^T \mid \eta_n^T \vee \pi^{-1}(\epsilon_Y))$$. The trick is to proceed inductively. Notice

$$H_\mu(\xi_n^T \mid \eta_n^T \vee \pi^{-1}(\epsilon_Y)) = H_\mu(\xi \mid \eta_n^T \vee \pi^{-1}(\epsilon_Y)) + H_\mu(T^{-1}(\xi_{n-1}^T) \mid \xi \vee \eta_n^T \vee \pi^{-1}(\epsilon_Y)).$$

We can get an upper bound:

$$H_\mu(\xi_n^T \mid \eta_n^T \vee \pi^{-1}(\epsilon_Y)) \leq H_\mu(\xi \mid \eta \vee \pi^{-1}(\epsilon_Y)) + H_\mu(T^{-1}(\xi_{n-1}^T) \mid \eta_n^T \vee \pi^{-1}(\epsilon_Y)).$$

We can continue in this fashion to eventually get

$$ H_\mu(\xi_n^T \mid \eta_n^T \vee \pi^{-1}(\epsilon_Y)) \leq n H_\mu(\xi \mid \eta \vee \pi^{-1}(\epsilon_Y)).$$

The result now follows by plugging in limits. See [Katok and Hasselblatt](https://cosweb1.fau.edu/~jmirelesjames/ODE_course/katok.pdf) Proposition 4.3.10 for more details. $$\blacksquare$$

We define the **boundary** of a measurable partition $$\xi := \{A_1, \ldots, A_n\}$$ to be

$$\partial \xi := \bigcup_{i=1}^n \partial A_i.$$

We define the measure $$\delta_x$$ to be the probability measure concentrated at the point $$x$$ (that is, the **Dirac measure**). Also recall that if $$\pi : X \rightarrow Y$$ a measurable transformation, $$\mu$$ a measure on $$X$$, then the **pushforward measure** is defined by

$$\pi^*(\mu)(E) = \mu(\pi^{-1}(E)).$$

Finally if $$\pi : X \rightarrow Y$$ is continuous, $$T : X \rightarrow X$$ is continuoius, $$S : Y \rightarrow Y$$ is continuous, and $$\pi T = S \pi$$, then we say that $$S$$ is a **factor** of $$T$$.

# Theorem

With all of this, we can now actually state the major theorem (see Theorem 2.1 in the paper).

**Theorem:** Let $$X, Y$$ be compact metric spaces and let $$T : X \rightarrow X$$, $$S : Y \rightarrow Y$$, $$\pi : X \rightarrow Y$$ be continuous maps so that $$\pi$$ is surjective and $$\pi T = S \pi$$. Let $$f : X \rightarrow \mathbb{R}$$ be continuous and let $$\nu \in M(Y,S)$$. Then

$$ \sup \left\{h_\mu(T \mid S) + \int f d\mu : \mu \in M(X,T) \text{ and } \pi^*(\mu) = \nu\right\} = \int_Y P(T,f,\pi^{-1}(y))d\nu(y).$$

## Sketch of Proof

Throughout the proof, we assume the conditions of the theorem above, namely we assume that $$X, Y$$ are compact metric spaces, $$T :X  \rightarrow X$$, $$S : Y \rightarrow Y$$, $$\pi : X \rightarrow Y$$ are all continuous, $$\pi$$ is surjective, and $$S$$ is a factor of $$T$$. The first lemma says that conditional entropy with respects to maps behaves similar to conditional entropy with respect to partitions. This is Lemma 3.1 in the paper.

**Lemma:** Let $$Z$$ be a compact space and $$R$$ a factor of $$S$$ by $$\delta : Y \rightarrow Z$$. If $$\mu \in M(X,T)$$ then we have

$$h_\mu(T \mid R) = h_{\pi^*(\mu)}(S \mid R) + h_\mu(T \mid S).$$

The proof of this essentially follows from the so-called Pinsker's lemma (see [Rokhlin's lecture notes](https://iopscience.iop.org/article/10.1070/RM1967v022n05ABEH001224/pdf)). While a little technical, it is essentially the same as it's partition counterpart. The next lemma is also important, but a little bit technical. This is Lemma 3.2 in the paper.

**Lemma:** (i) Let $$\xi, \eta$$ be finite partitions of $$X$$, let $$\mu_1, \mu_2$$ be two probability measures on Borel subsets of $$X$$. If $$0 \leq p \leq 1$$ then

$$ p H_{\mu_1}(\xi \mid \eta\) + (1-p) H_{\mu_2} (\xi \mid \eta) \leq H_{p \mu_1 + (1-p)\mu_2}(\xi \mid \eta).$$

(ii) Suppose $$\xi$$ is a finite partition of $$X$$ and let $$\mu$$ be a finite Borel probability measure on $$X$$ with $$\mu(\partial \xi) = 0$$. Let $$\{\mu_n\}$$ be a sequence of Borel probability measures so that $$\mu_n \rightarrow \mu$$. Then

$$\lim_{n \rightarrow \infty} H_{\mu_n}(\xi \mid \eta) \leq H_\mu(\xi \mid \eta).$$

(iii) The function $$\mu \mapsto h_\mu(T \mid S)$$ defined on $$M(X,T)$$ is affine.

We omit the proof of this one as well. Observe that the point of the prior lemma was to be used for this lemma. With this in mind, if we let $$\|f\|$$ denote the supremum norm for $$C(X)$$ then we can set up the following lemma (this is Lemma 3.3 in the paper).

**Lemma:** Let $$f \in C(X)$$. The mappings $$y \mapsto P_n(T, f, \pi^{-1}(y), \delta)$$ of $$Y$$ to $$\mathbb{R}$$ are Borel measurable for $$n \geq 1$$. Moreover for each $$\delta > 0$$ there is a constant $$C(\delta)$$ so that

$$\frac{1}{n} \log(P_n(T, f, \pi^{-1}(y), \delta)) < C(\delta) \text{ for } n \geq 1, y \in Y.$$

**Sketch of Proof:** Recall that

$$P_n(T,f,\pi^{-1}(y), \delta)  := \sup \left\{ \sum_{x \in E} \exp(f_n(x)) : E \text{ is } (n,\delta) \text{ separated and } E \subseteq \pi^{-1}(y) \right\}.$$

Ledrappier-Walters breaks this up into smaller more manageable chunks which are easy to study. The idea is to fix $$k \in \mathbb{N}$$ and $$\delta > 0$$ and look at those chunks which have $$k$$ factors that stay roughly larger than $$e^{nt}$$ for some $$t \in \mathbb{R}$$. The first step is to look at the collection of $$k$$-tuples of points in $$X$$ who all project down into $$y$$. That is, we look at

$$D_k := \{(x_1, \ldots, x_k) \in X^k : \pi(x_1) = \cdots = \pi(x_k)\}.$$

Now we want them to stay separated, so look at

$$E_k^{n,\delta} := \{(x_1, \ldots, x_k) \in X^k : \max_{0 \leq m < n} d(T^m(x_i), T^m(x_j)) \geq \delta \text{ if } i \neq j\}.$$

Finally we want this approximately larger than the exponential sum, so

$$ F_{k,l}^{n,t} := \left\{ (x_1, \ldots, x_k) \in X^k : \sum_{i=1}^k \exp(f_n(x_i)) \geq e^{nt} + 1/l\right\}.$$

The advantage now is that each of these sets are going to be closed. The first one is the preimage of a closed set under a continuous map, the second is the intersection of a bunch of closed sets, and the third one is the preimage of a closed set under a continuous map. Let $$\phi : X^k \rightarrow Y, \phi(x_1, \ldots, x_k) = \pi(x_1)$$. Taking the intersection and mapping it through $$\phi$$, we have

$$G_{k,l}^{n,\delta,t} = \phi(D_k \cap E_k^{n,\delta} \cap F_{k,l}^{n,t}).$$

This is a compact set, and furthermore these are the slices (in terms of $$k$$ and $$l$$) of things we actually care about. Taking the union over all $$k$$ and $$l$$ gives us a Borel set which is exactly

$$\bigcup_{k,l} G_{k,l}^{n,\delta,t} = \{y : P_n(T, f, \pi^{-1}(y), \delta) > e^{nt}\}.$$

This tells us the mapping is Borel. If one makes the observation that $$P_n(T,f,\pi^{-1}(y), \delta) \leq e^{n \|f\|} s_n(T,\pi^{-1}(y), \delta),$$ then the last condition follows easily. $$\blacksquare$$

The final lemma is one that should seem familiar from ergodic theory. This is Lemma 3.4 in the paper.

**Lemma:** If $$K \subseteq X$$ compact and $$m \in \mathbb{N}$$ then

$$ P(T^m, f_m, K) = m P(T,f,K).$$

**Sketch of Proof:** It's mostly just a matter of running through definitions. Suppose $$E$$ is $$(n,\delta)$$ separated for $$T^m$$. This means that for $$x \neq y$$ in $$E$$ we have

$$\max_{0 \leq i < nm} d(T^i(x), T^i(y)) \geq \max_{0 \leq k < n\} d(T^{km}(x), T^{km}(y)) \geq \delta.$$

Thus $$E$$ is an $$(mn,\delta)$$ separated set for $$T$$. Now

$$P_n(T^m, f_m, K, \delta) \leq P_{nm}(T,f,K, \delta).$$


Thus

$$ \frac{1}{n} \log(P_n(T^m, f_m, K, \delta)) \leq m \cdot \frac{1}{nm} \log(P_{nm}(T,f,K,\delta)).$$

Take the limit as $$n \rightarrow \infty$$ and $$\delta \rightarrow 0$$ to get the inequality going in one direction. The other direction follows from a clever choice of $$\delta$$ and $$\delta'$$ and then doing the same kind of inequality tricks. $$\blacksquare$$
