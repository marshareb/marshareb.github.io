---
layout: post
title: Subcohomology using thermodynamic formalism
tags:
  - dynamics
categories:
  - Dynamics
---

In this post, we discuss some basics on subcohomology by proving a non-positive result by Savchenko, as well as discussing Bousch's realization theorem.

# Set up

## Main motivation

As in our previous post, let $\sigma : X_A \rightarrow X_A$ be a shift of finite type which is not reversible, and for a continuous function $\psi : X_A \rightarrow \mathbb{R}$ we will write 

$$ \psi^n(x) := \sum_{k=0}^{n-1} \psi(\sigma^k(x)).$$
Let $P$ be the set of periodic points, i.e., 

$$ P := \bigcup_{n \geq 0} \text{Fix}(\sigma^n).$$

Our goal is to understand what the behavior of $\psi$ on $P$ dictates for its global behavior. Recall that the Livshits theorem tell us that if for all $x \in P$ such that $\sigma^n(x) = x$ we have $\psi^n(x) = 0$, then there is a continuous function $u : X_A \rightarrow \mathbb{R}$ such that $\psi = u \circ \sigma - u$. If we let $\mathcal{M}$ denote the set of invariant probability measures for $\sigma$, then notice that this says for all $\mu \in \mathcal{M}$ we have

$$ \int_{X_A} \psi d\mu = 0.$$

In other words, the behavior of $\psi$ on $P$ dictates the behavior of $\psi$ for all $\mu \in \mathcal{M}$. The game now is that we want to replace the equality in our assumption with an inequality. We will also be working with higher regularity than just continuous: let 

$$ \text{Var}_n(\psi) := \sup\{|\psi(x) - \psi(y)| : x_i = y_i \text{ for all } 0 \leq i < n\}, $$ 
and 

$$  C^\theta(X_A) := \{ \psi \in C(X_A) : \text{there exists } C > 0 \text{ such that }\text{Var}_n(\psi) \leq C \theta^n \text{ for all } n \geq 0\}.$$

 In other words, our question is the following: *Let $\psi \in C^\theta(X_A)$. If for all $n$ and all $x \in \text{Fix}(\sigma^n)$ we have $\psi^n(x) \leq 0$, does there exist a function $u \in C^\theta(X_A)$ such that $\psi \leq u \circ \sigma - u$?*

This result has been proven several times over the years, but we'll be sketching [Savchenko's](https://link.springer.com/article/10.1007/BF02465212) proof of this fact. We want to emphasize that the advantage of this proof is that it uses thermodynamic formalism to prove this fact, as opposed maybe more topological proofs. After proving Savchenko's result, we'll discuss how we can use the work of Bousch to upgrade this to get a result that relates quantities from ergodic optimization to cohomology classes.

**Remark:** As it will come up later, we define 

$$ \vert u \vert_\theta := \sup_{n \geq 0} \left\{ \frac{\text{Var}_n(u)}{\theta^n} \right\},$$

and the $\theta$-Lipschitz norm by

$$ \|u\|_\theta := \vert u \vert_\theta + \|u\|_\infty.$$
## Transfer operator

Recall that the *transfer operator* is given by

$$ L_\psi : C^\theta(X_A) \rightarrow C^\theta(X_A), \quad L_\psi(g)(x) := \sum_{\sigma(y) = x} e^{\psi(y)}g(y).$$

As an easy observation, we notice that iterating the transfer operator yields the following:

$$ L^n_\psi(g)(x) = \sum_{\sigma^n(y) = x} e^{\psi^n(y)} g(y).$$

The famous *Ruelle-Perron-Frobenius theorem* says the following (see Theorem 2.2 in [Parry and Pollicott's book](https://www.numdam.org/item/AST_1990__187-188__1_0.pdf).

**Theorem:** Let $\psi \in C^\theta(X_A)$. Then 
- there is a simple maximal positive eigenvalue $\beta$ of $L_\psi$ which corresponds to a strictly positive eigenfunction $h \in C^\theta(X_A)$,
- the remainder of the spectrum of $L_\psi$ is contained in a disc of radius strictly smaller than $\beta$,
- there is a unique probability measure $\mu$ such that for all $\eta \in C^\theta(X_A)$, we have
 
$$ \int_{X_A} L_\psi(\eta) d\mu = \beta \int_{X_A} \eta d\mu,$$

- for all $\eta \in C^\theta(X_A)$,

$$\lim_{n \rightarrow \infty} \beta^{-n} L_\psi^n(\eta) = h \int_{X_A} \eta d\mu,$$

and this convergence is uniform. $\square$

**Remark:** Part of the proof of the RPF theorem is showing that $h$ satisfies the following: if $x, y \in X_A$ are such that $x_i = y_i$ for $0 \leq i < m$, then 

$$ h_n(x) \leq h_n(y) e^{2 \vert \psi_n \vert_\theta (1-\theta)^{-1} \theta^{m-1}}.  \square$$

We will use the notation $1$ to indicate the function $1(x) = 1$. Let $h$ be such that $L_\psi(h) = \beta h$, where $\beta$ and $h$ are from the RPF theorem. Let $u(x) := \log(h(x))$, and let $\psi'(x) := \psi(x) - u(\sigma(x)) + u(x).$ Observe that 

$$ L_{\psi'}(1) = \sum_{\sigma(y) =x} e^{\psi'(y)} = \sum_{\sigma(y) = x} e^{\psi(y) - u(x) + u(y)} = e^{-u(x)} \sum_{\sigma(y) = x} e^{\psi(y)}h(y) = \frac{1}{h(x)} L_\psi(h)(x).$$

By construction of $h$, we know that $L_\psi(h)(x) = \beta h(x)$, so putting it all together, we have that $L_{\psi'}(1) = \beta$. Finally, we can normalize our $\psi'$; let's now reassign $\psi'(x) := \psi(x) - u(\sigma(x)) + u(x) - \log(\beta)$, then our argument shows that $L_{\psi'}(1) = 1$.

**Claim:** Let $\psi \in C^\theta(X_A)$. If $L_\psi(1) = 1$, then $\psi \leq 0$.

**Proof:** Let $y \in X_A$ be arbitrary, and let $x = \sigma(y)$. Observe that  

$$  1 = L_{\psi}(1)(x) = \sum_{\sigma(y) = x} e^{\psi(y)} \geq e^{\psi(y)}.$$

We deduce that $\psi(y) \leq 0$ for all $y \in X_A$. $\square$

Combining our claim with the above observation, we have shown the following (which we will call the *RPF non-positive lemma*).

**Lemma:** Given any $\psi \in C^\theta(X_A)$, let $h$ and $\beta$ be as-in the RPF theorem. The function $\psi'(x) := \psi(x) - \log(h(\sigma(x))) + \log(h(x)) - \log(\beta)$ is non-positive. $\square$

**Remark:** We can express $\beta$ in terms of the pressure of $\psi$. Namely, we have $\beta = e^{P(\psi)}$. $\square$
# Savchenko-Bousch Realization theorem

With all of this out of the way, we can now get to the first result.

**Theorem:** Let $\sigma : X_A \rightarrow X_A$ be a shift of finite type, let $\psi \in C^\theta(X_A)$, and suppose that for all $n \geq 0$ and $x \in \text{Fix}(\sigma^n)$ we have $\psi^n(x) \leq 0$. Then there is a $u \in C^\theta(X_A)$ such that $\psi \leq u \circ \sigma - u$. 

**Proof:** For each $n$, let $\psi_n(x) := n \psi(x)$. Let $h_n$ and $\beta_n$ be the quantities from the RPF theorem corresponding to $\psi_n$. We now consider the sequence of functions

$$ \psi_n'(x) = \psi(x) - \frac{1}{n}\log(h_n(\sigma(x)) + \frac{1}{n} \log(h(x)) - \frac{P(n \psi)}{n},$$

where the sequence of functions $h_n$ are coming from the RPF theorem. Using the RPF non-positive lemma, we know that $\psi_n' \leq 0$. The game now is to use the Arzela-Ascoli theorem to conclude that the sequence of functions $u_n(x) := \frac{1}{n} \log(h_n(x))$ converges to a function $u$ along some subsequence. In order to do this, we need to show that $u_n$ is bounded in the $\|\cdot\|_\theta$ norm.

**Step 1:** Let's show that $\vert u_n \vert_\theta$ is bounded. Let $x, y \in X_A$ be such that $x_i = y_i$ for $0 \leq i < m$. We observe that 

$$ \vert u_n(x) - u_n(y) \vert = \frac{1}{n} \vert \log(h_n(x)/h_n(y))\vert.$$

Using our key inequality (see the remark after the RPF theorem), recall that 

$$ h_n(x) \leq h_n(y) e^{2 \vert \psi_n \vert_\theta (1-\theta)^{-1} \theta^{m-1}}.$$

Thus, we get

$$ \vert u_n(x) - u_n(y) \vert \leq 2 \vert \psi \vert_\theta (1-\theta)^{-1} \theta^{m-1},$$

here using that $\psi_n = n \psi$. This shows us that $\vert u_n \vert_\theta$ is bounded.  $\square$

**Step 2:** Note that $\|u_n\|_\infty$ being bounded follows from the inequality

$$C^{-1} e^{-M P(\psi_n) - M \|\psi_n\|_\infty - 2 \vert \psi \vert_\theta (1-\theta)^{-1} \theta} \leq h_n(x) \leq Ce^{M P(\psi_n) + M \|\psi_n\|_\infty + 2 \vert \psi \vert_\theta (1-\theta)^{-1} \theta}, $$

where $C>0$ and $M > 0$ is an integer such that the entries of the matrix $A^M$ are all positive. $\square$

Combining Steps 1 and 2, we get that $\|u_n\|_\theta$ is bounded, and so using Arzela-Ascoli we can take a subsequence so that $u_n \rightarrow u$. We take one more step to understand what is going on with the pressure.

**Step 3:** Let's observe that the variational principle gives us

$$ P(n \psi) = \sup_{\mu \in \mathcal{M}} \left\{ h_\mu + n \mu(\psi) \right\}.$$

Furthermore, this supremum is achieved for some measure, say $\mu_n$. Observe now that 

$$ \frac{P(n\psi)}{n} = \frac{h_{\mu_n}}{n} + \mu_n(\psi).$$

It is now well-known that the limit exists (see, for example [this note](https://arxiv.org/abs/1305.2396) on ergodic optimization). Let

$$ M(\psi) := \sup_{\mu \in \mathcal{M}} \{\mu(\psi)\},$$

we have 

$$ \lim_{n \rightarrow \infty} \frac{P(n\psi)}{n} = M(\psi).$$

Finally, we can use [Sigmund's theorem](https://www.ams.org/journals/tran/1974-190-00/S0002-9947-1974-0352411-X/home.html) to deduce that $M(\psi) \leq 0$ using our assumption. $\square$ 

Taking the limit along our subsequence, we have 

$$ \psi - u \circ \sigma + u \leq \psi - u \circ \sigma + u - M(\psi) \leq 0,$$

as desired. $\square$

**Remark:** If we remove our assumption that $\psi^n(x) \leq 0$ for all appropriate $x$ and $n$, then the above theorem shows that we can construct a $u$ such that 

$$ \psi \leq u \circ \sigma - u + M(\psi).$$

Playing the same game in reverse time and letting $m(\psi)$ be the infimum of the integral of $\psi$ over all invariant measures, we can also construct a $v$ such that 

$$ \psi \geq v \circ \sigma - v + m(\psi). \ \ \square$$

In light of the above remark, it is curious to see whether we can combine $u$ and $v$ into a single solution. We now observe the following, due to [Bousch](https://www.imo.universite-paris-saclay.fr/~thierry.bousch/preprints/manebi.pdf). 

**Theorem:** For $\psi \in C^\theta(X_A)$, if there exists $u,v \in C^\theta(X_A)$ such that 

$$ v \circ \sigma - v + m(\psi) \leq  \psi \leq u \circ \sigma - u + M(\psi),$$

then there exists $w \in C^\theta(X_A)$ such that $m(\psi) \leq \psi - w \circ \sigma + u \leq M(\psi).$ $\square$

Thus, combining Savchenko and Bousch, we deduce the following *Savchenko-Bousch realization theorem*.

**Theorem:** For $\psi \in C^\theta(X_A)$, there always exists a $u \in C^\theta(X_A)$ such that 

$$m(\psi) \leq \psi - u \circ \sigma + u \leq M(\psi). \ \square$$

Recall that two functions $\psi, \eta \in C^\theta(X_A)$ are *cohomologous* if there is a $u \in C^\theta(X_A)$ such that $\psi = u \circ \sigma - u + \eta$. Thus, the *cohomology class* of $\psi$ is the set 

$$[\psi] := \{\psi - u \circ \sigma + u : u \in C^\theta(X_A)\}. $$

One way of interpreting the Savchenko-Bousch realization theorem is the following: *For every function $\psi \in C^\theta(X_A)$, there is a representative $\eta$ in the cohomology class which is bounded between $m(\psi)$ and $M(\psi)$.* 