---
layout: post
title: Perron-Frobenius Operator
tag: dynamics
categories: ["Dynamics"]
---

In this post I discuss the Perron-Frobenius operator, also known as the [transfer operator](https://en.wikipedia.org/wiki/Transfer_operator).

# Definition and Properties

We'll be studying the space $$L^1 := L^1([0,1])$$, which is the space of integrable functions on $$[0,1]$$. We denote Lebesgue measure by $$m$$. Let $$T : [0,1] \rightarrow [0,1]$$ be a measurable transformation. We will assume it is **non-singular**, meaning that $$m(A) = 0$$ implies $$m(T^{-1}(A)) = 0$$. Observe that this implies that if $$m(A) = 1$$, then $$m(T^{-1}(A)) = 1$$ by taking complements. We define the **Perron-Frobenius operator** $$P_T$$ as a transformation on $$L^1$$ by

$$P_T f (x) = \frac{d}{dx} \int_{T^{-1}([0,x])} f(s)ds.$$

The goal of this article is to establish some well-known properties of $$P_T$$. Namely that $$P_T : L^1 \rightarrow L^1$$ is a continuous, linear transformation satisfying the following:

1) $$P_T$$ preserves integrals in the sense that

$$ \int_E P_T f dm = \int_{T^{-1}(E)} f dm.$$

2) $$P_T$$ satisfies the property that for all $$\phi \in L^\infty$$ we have

$$ \int_0^1 \phi(x) P_T f(x) dx = \int_0^1 \phi \circ T(x) f(x) dx.$$

3) $$P_T$$ is positive, in the sense that if $$f \geq 0$$ almost everywhere then $$P_Tf \geq 0$$ almost everywhere.

4) The operator respects iterates in the sense that

$$ P_{T^n} = P_T^n.$$

5) We have $$P_T(f) = f$$ almost everywhere if and only if the measure $$d\mu = f dm$$ is invariant under $$T$$.

**Remark:** There are a few other definitions for the Perron-Frobenius operator which are all equivalent. The most general one is just by taking the Radon-Nikodym derivative, which is in some sense the same thing as property (1). Another one is by showing (2) actually completely characterizes the operator and thus defining it via distributions. We'll see in proving the other properties how useful these other definitions are.

## Linearity and Continuity

Let's first check that the image is in $$L^1$$. Given $$f \in L^1$$, we can let

$$ F(x) := \int_{T^{-1}([0,x])} \mid f  (s) \mid ds.$$

Then

$$ \int_0^1 P_T (\mid f \mid)(x) dx = \int_0^1 F'(x) dx = F(1) - F(0).$$

Since $$T$$ is non-singular, we have that $$F(1) = \|f\|_1$$ and $$F(0) = 0$$. Since $$f \in L^1$$ we have that this is finite. Finally observe that

$$ \mid P_T f (x) \mid \leq P_T( \mid f \mid)(x),$$

so we get that $$\|P_T f\|_1 \leq \|f\|_1$$. Thus the image is in $$L^1$$.

It's an easy check to see that $$P_T$$ is linear. Take $$a \in \mathbb{R}$$ and $$f,g \in L^1$$. We have

$$ P_T (af + g)(x) = \frac{d}{dx} \int_{T^{-1}([0,x])} (af + g)(s) ds = a \frac{d}{dx} \int_{T^{-1}([0,x])}f(s) ds + \frac{d}{ds} \int_{T^{-1}([0,x])} g(s) ds = a P_T f(x) + P_T g(x).$$

We can now deduce that $$P_T$$ is continuous with respect to the $$L^1$$ topology. Let $$f_n \rightarrow f$$ in $$L^1$$. Then

$$ \|P_T (f_n) - P_T(f)\|_1 = \|P_T(f_n - f)\|_1 \leq \| f_n - f\|_1 \rightarrow 0.$$

## Condition 1)

We now check that $$P_T$$ preserves integrals. Notice that we have that the following holds on any interval $$[a,b] \subseteq [0,1]$$:

$$ \int_a^b P_T f dm = \int_a^b \frac{d}{dx} \int_{T^{-1}([0,x])} f(s) ds dx = \int_{T^{-1}([a,b])} f dm.$$

Since singular points have measure zero, this holds for all types of intervals. An open set can be written as a disjoint union of open intervals, so given any $$U \subseteq [0,1]$$ open we can write

$$ \int_U P_Tf dm = \sum_{n=0}^\infty \int_{I_n} P_T f dm = \sum_{n=0}^\infty \int_{T^{-1}(I_n)} f dm = \int_{T^{-1}(U)} f dm.$$

Now any measurable set can be written as an open set minus a set of measure zero, so we use the non-singularity of $$T$$ to deduce the result.

## Condition 2)

Fix $$f \in L^1$$ throughout. Notice that we've shown the property on a dense set of $$L^\infty$$. Namely, we have shown it on the simple functions. To see this, take $$\chi_E$$ and observe that

$$ \int P_Tf(x) \chi_E(x) dx = \int_E P_Tf (x) dx = \int_{T^{-1}(E)} f(x) dx = \int \chi_E(T(x)) f(x) dx.$$

We get that it holds on simple functions by observing the above property holds over linear combinations. Now take $$\phi \in L^\infty$$ and fix $$\epsilon > 0$$. We can find a simple function $$ \psi$$ so that $$\|\phi - \psi\|_\infty < \epsilon$$. Hence

$$
\begin{split}
\text{abs} \left( \int_0^1 [\phi(x) P_Tf(x) - \phi(T(x)) f(x) ] dx  \right) = \text{abs} \left( \int_0^1 [\phi(x) P_Tf(x) - \psi(x) P_Tf(x) + \psi(T(x)) f(x) - \phi(T(x)) f(x) ] dx  \right) \\
\leq \int_0^1 \|\phi - \psi\|_\infty \mid P_T f(x) \mid dx + \int_0^1 \|\psi - \phi\|_\infty \mid f (x) \mid dx < 2 \epsilon \|f\|_1.
\end{split}
$$

Since the choice of $$\epsilon$$ was arbitrary, we can let $$\epsilon \rightarrow 0$$ to get that the integrals must be equal. The choice of $$\phi$$ was arbitrary, so the property holds for any such $$\phi$$.

## Condition 3)

To show that $$P_T$$ is positive, take $$f \geq 0$$. Let $$\phi$$ be the characteristic function on the set where $$P_Tf < 0$$. Then

$$  0 \leq \int \phi(T(x)) f(x) dx = \int \phi(x) P_Tf(x) dx \leq 0.$$

Thus we see that $$P_Tf > 0$$ almost everywhere.

## Condition 4)

We now check the iterates property. If we let $$E_x := T^{-1}([0,x])$$ then we see that

$$ P_T^2 f(x) = \frac{d}{dx} \int_0^1 \chi_{E_x}(t) P_Tf(t) dt = \frac{d}{dx} \int_0^1 \chi_{E_x}(T(t)) f(t) dt.$$

Observe that $$\chi_{E_x}(T(t)) = T^{-2}([0,x]),$$ so we get exactly that

$$ P_T^2 f(x) = \frac{d}{dx} \int_{T^{-2}([0,X])} f(t) dt.$$

An induction argument shows this holds for all $$n \geq 0$$.

## Condition 5)

Assume $$P_T(f) = f$$ almost everywhere. Then we have

$$ \int_E f(x) dx = \int_E P_Tf(x) dx = \int_{T^{-1}(E)} f(x) dx.$$

If we let $$d\mu = f dm$$, then the above implies $$ \mu(E) = \mu(T^{-1}(E))$$ and so $$\mu$$ is invariant under $$T$$. On the other hand, if $$\mu$$ is invariant under $$T$$, then we get that for every measurable set we have

$$ \int_E f(x) dx = \int_E P_T f(x) dx.$$

We do the usual trick here. Let $$E^+$$ be the set where $$f - P_Tf > 0$$ and $$E^-$$ the set where $$f - P_Tf < 0$$. The above says that

$$ \int_{E^-} [f(x) - P_Tf(x)]dx = 0.$$

The only way this can happen is if $$m(E^-) = 0$$. Similarly

$$ \int_{E^+} [P_Tf(x) - f(x)] dx = 0,$$

so $$m(E^+) = 0$$. We conclude that $$P_Tf = f$$ almost everywhere.

# References

(i) [On The Existence Of Invariant Measures For Piecewise Monotonic Transformations by Lasota and Yorke](https://www.ams.org/journals/tran/1973-186-00/S0002-9947-1973-0335758-1/S0002-9947-1973-0335758-1.pdf)

(ii) [Exact Dynamical Systems and the Frobenius-Perron Operator by Lasota and Yorke](https://www.ams.org/journals/tran/1982-273-01/S0002-9947-1982-0664049-X/S0002-9947-1982-0664049-X.pdf)

(iii) [Introduction to the Transfer Operator Method by Sarig](http://www.weizmann.ac.il/math/sarigo/sites/math.sarigo/files/uploads/transferoperatorcourse-bonn.pdf)
