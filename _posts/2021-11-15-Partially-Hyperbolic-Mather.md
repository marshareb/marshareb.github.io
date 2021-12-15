---
layout: post
title: Mather Spectrum Part 1
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss a result on the spectrum of diffeomorphisms. Credit to Thomas O'Hare for discussing the result with me and showing me a proof.

# Set Up

Here, we'll be following [Mather's paper](https://www.sciencedirect.com/science/article/pii/S1385725868500593?via%3Dihub) and [Pesin's book](https://www-ems-ph-org.proxy.lib.ohio-state.edu/books/book.php?proj_nr=16) in order to prove a nice result connecting the Mather spectrum to dynamical properties. First let's set up some notation and definitions.

Let $$f : M \rightarrow M$$ be a $$C^1$$ diffeomorphism on a smooth Riemannian manifold. We can consider the module $$\Gamma^0(TM)$$, which is the module of continuous vector fields on $$M$$. Alternatively, we can also just view this as a real vector space (which will be useful in the future). We can convert $$f$$ into an operator. Let $$f_* : \Gamma^0(TM) \rightarrow \Gamma^0(TM)$$ be the operator defined by

$$f_*(v)(x) = df(v(f^{-1}(x))).$$

Note this is a continuous linear operator. Recall the complexification of $$f_*$$ is the operator $$T : \Gamma^0(TM) \otimes \mathbb{C} \rightarrow \Gamma^0(TM) \otimes \mathbb{C}$$ which is defined by $$T(v \otimes z) = f_*(v) \otimes z.$$ We define the **Mather spectrum** of $$f$$ to be the spectrum of $$T_f$$ (Note: some authors continue to write this as $$f_*$$). Thus the Mather spectrum is going to be the set of all $$\lambda \in \mathbb{C}$$ so that $$T_f - \lambda I$$ is not invertible. We denote it by $$\text{sp}(T_f)$$.

# Main Result and Proofs

## Main Result

The idea is that we've converted dynamical data into functional data -- that is, we've converted the study of the diffeomorphism $$f$$ into the study of this operator $$T_f$$. The natural questions are as follows: What info do we get on $$T_f$$ from $$f$$ and what info do we recover from $$f$$ using $$T_f$$? It turns out a surprising amount of data can be encoded in this operator. Namely, Mather claims the following in his paper:

**Theorem:** We have that $$f$$ is an Anosov diffeomorphism if and only if $$1 \notin \text{sp}(T_f)$$.

The goal of this post is to show the proof for the following technical lemma.

**Lemma:** If the non-periodic points of $$f$$ are dense, $$\mu \in \text{sp}(T_f)$$ and $$\lambda \in \mathbb{C}$$ is such that $$\|\lambda\| = 1$$, then $$\lambda \mu \in \text{sp}(T_f)$$.

## Proof of Lemma

Let $$r > 0$$ and consider the set

$$S_r := \{\lambda \in \mathbb{C} : \|\lambda\| = r\}.$$

In the complex plane, this is just the ball of radius $$r$$. Suppose that there is a $$\mu \in \text{sp}(T_f)$$ and there is a $$\lambda$$ so that $$\lambda \mu \notin \text{sp}(T_f)$$. In particular this means that for $$r = \|\mu\|$$ we have $$S_r \cap \text{sp}(T_f) \neq S_r$$ nor $$\varnothing$$. Let $$\mu \in \partial \text{sp}(T_f)$$ be one boundary point. Our goal is to show that there cannot be such a $$\mu$$. Mather breaks this up into two steps.

**Step 1:** We wish to show that there is no $$\epsilon > 0$$ so that

$$\|(T_f - \mu I)\xi\| \geq \epsilon \|\xi\| \text{ for all } \xi \in \Gamma^0(TM).$$

Suppose one did exist for contradiction. Our goal is to show that $$\mu$$ cannot be a boundary point, which gives us our contradiction. If such an $$\epsilon$$ exists, then we have that $$T_f - \mu I$$ is injective since the kernel must be trivial by the above $$\epsilon$$. We claim the image must be closed and proper. Let $$Y := (T_f - \mu I)(X)$$.

**Claim:** $$Y$$ is closed and proper.

**Proof:** To show that it is closed, let $$(y_n) \subseteq Y$$ be such that $$y_n \rightarrow y$$. The goal is to show $$y \in Y$$. We may write $$y_n = (T_f - \mu I)(x_n)$$ for some $$(x_n) \subseteq \Gamma^0(TM)$$. Notice that we have

$$ \|(T_f - \mu I)(x_n)\| \geq \epsilon \|x_n\|.$$

In particular,

$$ \|x_n - x_m\| \leq \epsilon^{-1} \|(T_f - \mu I)(x_n - x_m)\| = \epsilon^{-1} \|y_n - y_m\| \rightarrow 0.$$

Thus $$(x_n)$$ is a Cauchy sequence, so $$x_n \rightarrow x$$. Now $$T_f - \mu I$$ is continuous, so $$Y$$ is closed. Notice that $$Y$$ cannot be the entire subspace since $$\mu \in \text{sp}(T_f)$$. $$\blacksquare$$

Now $$Y$$ is closed and proper implies that we can find $$x \in \Gamma^0(TM)$$ so that

$$ \inf_{y \in Y} \|y - x\| =: \delta > 0.$$

Now let

$$B := \{ y \in \Gamma^0(TM) : \|y\| \leq 2 \epsilon^{-1} \|x\| \}.$$

We wish to show that for sufficiently small $$\alpha$$ we have $$T_f - (\mu + \alpha)I$$ fails to be surjective (in particular fails to hit $$x$$) and so $$\mu$$ cannot be a boundary point. Let's examine the image $$(T_f - (\mu + \alpha)I)(B^c).$$ Notice that $$z \in B^c$$ implies that

$$\|z\| > 2 \epsilon^{-1} \|x\|.$$

Now using this and the reverse triangle inequality we get

$$\|(T_f - (\mu + \alpha)I)(z)\| = \|(T_f - \mu I)(z) - \alpha z\| \geq \|(T_f - \mu I)(z)\| - \|\alpha z\| \geq \epsilon \|z\| - \|\alpha\| \|z\|.$$

If we assume that $$\|\alpha\| < \epsilon/2$$ then we have

$$ \|(T_f - (\mu + \alpha)I)(z)\| > \frac{\epsilon}{2} \|z\| > \|x\|$$

since $$z \in B^c$$. Thus if $$\|\alpha\| < \epsilon/2$$ then $$x \notin (T_f - (\mu + \alpha)I)(B^c)$$. On the other hand, let $$z \in B$$, so

$$\|z\| \leq 2 \epsilon^{-1} \|x\|.$$

Then we have

$$\|(T_f - (\mu + \alpha)I)(z)\| = \|(T_f - \mu I)(z) - (\alpha z)\| = \|(T_f - \mu I)(z) - \alpha x + \alpha x - (\alpha z)\| \leq \|\alpha\| \delta + \|\alpha\| \|x -  z\|.$$

Now we know that

$$\|x - z\| \leq \|x\| + \|z\| \leq (1 + 2/\epsilon)\|x\|.$$

Plugging this in, we get

$$\|(T_f - (\mu + \alpha)I)(z)\| \leq \|\alpha\| (\delta + 1 + 2/\epsilon) \|x\|.

We want to choose $\alpha$ so that

$$\|\alpha\| (\delta + 1 + 2/\epsilon) < 1.$$

So if we choose $\alpha$ so that

$$ \|\alpha\| < \min \left\{ \frac{\epsilon}{2}, \delta + 1 + \frac{2}{\epsilon} \right\},$$

then the result follows. But this means that $$\mu$$ cannot be a boundary point, which results in a contradiction. This establishes Step 1.

**Step 2:** As an intermediate step, let's assume that we can show that for every $$\epsilon > 0$$ we can find a $$w \in \Gamma^0(TM)$$ with $$\|w\| = 1$$ so that

$$\|(T_f - \lambda \mu I)(w)\| \leq \epsilon.$$

We claim that this is establishes that $$\lambda \mu \in \text{sp}(T_f)$$. In particular, for each $$n$$ we can find $$w_n$$ with $$\|w_n\| = 1$$ so that

$$\|(T_f - \lambda \mu I)(w_n)\| \leq 1/n.$$

We have $$(w_n)$$ lives in the unit sphere which is compact. We can take a subsequence so that $$w_n \rightarrow w$$ with $$\|w\| = 1$$. Notice by continuity this tells us that

$$\|(T_f - \lambda \mu I)(w)\| = 0.$$

Thus we get that the operator fails to be injective, and so this is an eigenvalue.


**Step 3:** Step 2 illustrates our goal. We wish to show that for every $$\epsilon > 0$$ we can find $$w \in \Gamma^0(TM)$$ so that

$$ \|(T_f - \lambda \mu I)(w)\| \leq \epsilon.$$

By Step 1, we know that for every $$\epsilon > 0$$ there is a $$v \in \Gamma^0(TM)$$ so that $$\|v\| = 1$$ and

$$ \|(T_f - \mu I)(v)\| \leq \epsilon.$$

In particular, fixing $$\epsilon > 0$$, we may assume

$$ \|(T_f - \mu I)(v)\| \leq \frac{\epsilon}{4}.$$

By density, we can find a non-periodic point $$x \in M$$ so that

$$ \|v(x)\| \geq \frac{1}{2}.$$

Let $$n$$ be so that $$ n \geq 4\|\mu\|/\epsilon$$. Observe that since it is not periodic we can find a neighborhood $$U$$ of $$x$$ so that

$$ f^j(U) \cap f^k(U) = \varnothing \text{ for } -n \leq j < k \leq n.$$

Let $$\phi : U \rightarrow [0,1]$$ be a continuous function with compact support contained in $$U$$ so that $$\phi(x) = 1$$. Let

$$W := \bigcup_{k=-n}^n f^k(U).$$

We define

$$\psi(y) := \begin{cases}0 \text{ if } y \notin W, \\ \left(1 - \frac{\mid k \mid}{n} \right) \lambda^{-k} (\phi \circ f^{-k})(y) \text{ if } y \in f^k(U).\end{cases} $$

We observe that $$\psi$$ is continuous, since it is continuous on the bands $$f^k(U)$$ and the bands are disjoint. Observe that if $$\eta := \psi v \in \Gamma^0(TM)$$ then

$$\|\eta \| \geq \|\eta(x)\| = \|\psi(x)\| \|v (x)\|.$$

We then observe that $$\|\psi(x)\| = 1$$ and by choice we have $$\|v(x)\| \geq 1/2$$, so

$$\|\eta \| = \|\psi(x)\| \|v(x)\| \geq \frac{1}{2}.$$

In particular, this is a non-zero vector field. Now notice that

$$ T_f(w)(x) = Df(w(f^{-1}(x))) = Df( \psi(f^{-1}(x)) v(f^{-1}(x))) = \psi(f^{-1}(x)) Df(v(f^{-1}(x))).$$

Rearranging terms, we get

$$ T_f(w) = (\psi \circ f^{-1}) T_f(v).$$

Now using this we have

$$ \|(T_f - \lambda \mu I)(\eta)\| = \| (\psi \circ f^{-1}) T_f(v) - \mu \lambda \psi v\|.$$

Our goal is to try to ignore the $$\lambda$$ term. We rewrite this as


$$ \|(T_f - \lambda \mu I)(\eta)\| = \| (\psi \circ f^{-1}) T_f(v) - (\psi \circ f^{-1})\mu v + (\psi \circ f^{-1})\mu v - \mu \lambda \psi v\|.$$

By the triangle inequality,

$$ \|(T_f - \lambda \mu I)(\eta)\| \leq \| T_f(v) - \mu v\| + \|(\psi \circ f^{-1})\mu v - \mu \lambda \psi v\|.$$

Apriori we know that $$\|T_f(v) - \mu v\| \leq \epsilon/4$$. On the other hand, we can rewrite the next term as

$$ \|(\psi \circ f^{-1})\mu v - \mu \lambda \psi v\| = \|\mu\| \|(\psi \circ f^{-1}) - \lambda \psi\| \|v\|.$$

Now notice that if $$y \in W$$ then $$y \in f^k(U)$$ for some $$k$$. This implies that $$z := f^{-1}(y)$$ would be in $$f^{k-1}(U)$$. Suppose they are both in $$W$$. This tells us that

$$\psi(z) = \left(1 - \frac{k-1}{n} \right) \lambda^{-k+1} (\phi \circ f^{-k+1})(z) = \left(1 - \frac{k-1}{n} \right) \lambda^{-k+1} (\phi \circ f^{-k})(y).$$

On the other hand,

$$ \psi(y) = \left(1 - \frac{k}{n} \right) \lambda^{-k} (\phi \circ f^{-k})(y).$$

Thus

$$\psi(f^{-1}(y)) - \lambda \psi(y)  =\left(1 - \frac{k-1}{n} \right) \lambda^{-k+1} (\phi \circ f^{-k})(y) -  \left(1 - \frac{k}{n} \right) \lambda^{-k+1} (\phi \circ f^{-k})(y) = \frac{1}{n}(\phi \circ f^{-k})(y).$$

Wrapping this in an absolute value sign gives us

$$\| \psi \circ f^{-1} - \lambda \psi\| \leq \frac{1}{n}.$$

There are some other extraneous cases to consider, but all of them lead to a similar situation. Thus we have

$$ \|(T_f - \lambda \mu I)(\eta)\| \leq \frac{\epsilon}{4} + \frac{\|\mu\|}{n} \leq \frac{\epsilon}{2}.$$

Let $$w := \eta/\|\eta\|$$. Then $$w$$ is such that

$$\|(T_f - \lambda \mu)(w)\| \leq \epsilon.$$

Since we can do this for any $$\epsilon$$, we conclude that $$\lambda \mu \in \text{sp}(T_f)$$, as desired. $$\blacksquare$$

We'll pick up next time with proving the theorem.
