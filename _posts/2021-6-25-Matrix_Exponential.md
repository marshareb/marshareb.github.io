---
layout: post
title: Matrix Exponentials
tag: diffeq
categories: ["Differential Equations"]
---

In this post, I review the matrix exponential.

# Introduction

Recently I've been learning more symplectic geometry in the hopes of understanding magnetic flows better. I've been following along Ivo's course in symplectic geometry (found [here](https://www.asc.ohio-state.edu/terekcouto.1/teaching/SG_su21)), and he discussed an interesting example of Hamiltonians showing up in harmonic oscillators. If you took any undergraduate physics, you probably know what this entails, but I have very little experience when it comes to physics. Along the way I realized that I didn't actually remember that much from my ODE course (if we even covered this), so the goal is to work out some matrix exponential facts.

# Matrix Exponentials

To start, let's review how the matrix exponential works. Here we'll follow Hall's book on Lie groups, Lie algebras, and representations.

Recall that the exponential function on the real numbers has many different definitions which are all equivalent. In the context of this post, there are two properties we care about:

(1) $$\frac{d}{dt} e^t = e^t;$$

(2) $$e^t = \sum_{k=0}^\infty \frac{t^k}{k!}.$$

The first property is of interest for differential equations. Let's see why this is the case now. Suppose we have a function $$x(t) : \mathbb{R} \rightarrow \mathbb{R}$$ which satisfies the following differential equation:

$$ x'(t) = a x(t), \ \ x(0) = x_0.$$

Based on the first property, a guess for one solution of this differential equation is $$x(t) = e^{at}x_0$$. Differentiating, we see that $$x'(t) = a e^{at}x_0 = a x(t),$$ which is exactly the above. Now suppose we have another solution to the differential equation, fix it as $$x(t)$$ with $$x(0) = x_0$$. We can set $$y(t) = e^{-at} x(t).$$ Then notice that

$$ y'(t) = -a e^{-at} x(t) + e^{-at} x'(t) = - a e^{-at} x(t) + a e^{-at} x(t) = 0.$$

Since this holds for all $$t$$, we get that $$y(t)$$ is constant. Setting $$t=0$$, we get $$y(0) = e^{-a(0)}x(0) = x(0) = x_0$$, so

$$y(t) = e^{-at} x(t) = x_0,$$

or rearranging the equation, we have

$$ x(t) = e^{at} x_0,$$

which is exactly the desired solution. So just having *some* function which satisfies property (1), we get that we can solve linear differential equations!

The issue with the first property is that, while it is a defining characteristic for the function, it's harder to work with once we abstract the exponential to different spaces. Focusing in on matrices in general, we have a notion of multiplying matrices and we have a notion of a length of a matrix (something called a [matrix norm](https://en.wikipedia.org/wiki/Matrix_norm)), so we can actually just plug in the second property as a definition and be done. Namely, if $$X$$ is an $$n \times n$$ matrix (with real or complex coefficients), then the **matrix exponential** of $$X$$ is going to be

$$ \exp(X) = I + \sum_{k=1}^\infty \frac{X^k}{k!}.$$

Let's be a little careless here and just say that $$X^0 = I$$ **for every $$X$$** and $$0! = 1$$. In that case the definition can be rewritten as

$$ \exp(X) = \sum_{k=0}^\infty \frac{X^k}{k!}.$$

Skipping over some facts, let's just assume we're handed a submultiplicative complete norm on matrices denoted $$\|\cdot\|$$. Since the space of $$n \times n$$ matrices is a finite dimensional vector space, we [know](https://kconrad.math.uconn.edu/blurbs/gradnumthy/equivnorms.pdf) that all norms are equivalent, so it suffices to just pick our favorite (in fact, this fact is saying that [every norm is complete](https://math.stackexchange.com/questions/168275/proof-that-every-finite-dimensional-normed-vector-space-is-complete), so this was an unnecessary adjective). If it isn't satisfying enough to know that one exists, you can use the [Hilbert-Schmidt norm](https://en.wikipedia.org/wiki/Hilbert%E2%80%93Schmidt_operator) and prove it satisfies all of the desired properties, and then use the equivalence of norms to relate it to what we've done here. In particular, since it is a submultiplicative norm, we have four nice properties:

(1) $$\|X + Y\| \leq \|X\| + \|Y\|;$$

(2) $$ \|XY\| \leq \|X\| \|Y\|;$$

(3) Assuming $$(X_m)$$ is a sequence of matrices, we have $$X_m \rightarrow X$$ if and only if $$\|X_m - X\| \rightarrow 0$$ (here, we use the equivalence of norms);

(4) Every sequence which is Cauchy with respect to the norm converges, and [in particular](https://math.stackexchange.com/questions/1452751/absolute-convergence-of-a-series-defined-as-a-cauchy-sequence) every absolutely convergent series converges (in the sense of property 3) to some matrix.

Property (3) is a little misleading. Without a notion of topology, I can't say what convergence of matrices means. Normally when people say a sequence of matrices converge, they are saying that each of the coefficients converge (so basically what you would guess if you didn't know any better). This is actually convergence in the sense of a norm, so we can invoke the equivalence of norms on a finite dimensional vector space to get property (3).

Now with this in mind, we use property (2) to get $$\|X^k\| \leq \|X\|^k$$, and hence

$$ \sum_{k=0}^N \left\|\frac{X^k}{k!} \right\| \leq \sum_{k=0}^N \frac{\|X\|^k}{k!} \leq \sum_{k=0}^\infty \frac{\|X\|^k}{k!}.$$

This holds for every $$N$$, so we can deduce that

$$ \sum_{k=0}^N \left\|\frac{X^k}{k!} \right\| \leq \sum_{k=0}^\infty \frac{\|X\|^k}{k!}.$$

Now since $$ \|X\|$$ is a fixed real number, we know that the series on the right converges, thus this is an absolutely convergent series. Invoking property (4), we get that it is a convergent series.

In fact, we can get from this that the exponential function is also continuous by using the [Weierstrass M-test](https://en.wikipedia.org/wiki/Weierstrass_M-test). So we have a nice well-defined continuous function $$\exp : M_n(F) \rightarrow M_n(F)$$, where here I'm using $$M_n(F)$$ to denote $$n \times n$$ matrices over the field $$F$$ which is either $$\mathbb{R}$$ or $$\mathbb{C}$$.

Let's now check some nice properties of this matrix exponential:

(1) $$\exp(0) = I_n$$:

$$ \exp(0) = \sum_{k=0}^\infty \frac{0_n^k}{k!} = I_n + \sum_{k=1}^\infty \frac{0_n^k}{k!} = I_n.$$

**Remark:** Remember this is a consequence of our assumption that $$X^0 = I$$ for every $$X$$.

(2) If $$X$$ and $$Y$$ commute, then $$\exp(X+Y) = \exp(X)\exp(Y)$$: This is a tricky fact. Let's write out the definition:

$$\exp(X+Y) = \sum_{k=0}^\infty \frac{(X+Y)^k}{k!}.$$

Now, using the binomial theorem and commutativity, we can write

$$(X+Y)^k = \sum_{j=0}^k \frac{k!}{j! (k-j)!} X^j Y^{k-j}.$$

Plugging this in,

$$\exp(X+Y) = \sum_{k=0}^\infty \sum_{j=0}^k \frac{k!}{j! (k-j)!} \frac{1}{k!} X^j Y^{k-j} = \sum_{k=0}^\infty \sum_{j=0}^k \frac{X^j}{j!} \frac{Y^{k-j}}{(k-j)!}.$$

On the other hand,

$$\exp(X) \exp(Y) = \left( \sum_{k=0}^\infty \frac{X^k}{k!} \right) \left( \sum_{j=0}^\infty \frac{Y^j}{j!}\right).$$

Let's work with finite sums. We have

$$\left( \sum_{k=0}^0 \frac{X^k}{k!} \right) \left( \sum_{j=0}^0 \frac{Y^j}{j!}\right) = I,$$

$$\left( \sum_{k=0}^1 \frac{X^k}{k!} \right) \left( \sum_{j=0}^1 \frac{Y^j}{j!}\right) = (I + X)(I + Y) = I + X + Y + XY,$$

$$\left( \sum_{k=0}^2 \frac{X^k}{k!} \right) \left( \sum_{j=0}^2 \frac{Y^j}{j!}\right) = (I + X + X^2/2)(I + Y + Y^2/2) = I + Y + Y^2/2 + X + XY + XY^2/2 + X^2/2 + X^2/2Y + (XY)^2/2.$$

Rewriting this last sum,

$$\left( \sum_{k=0}^2 \frac{X^k}{k!} \right) \left( \sum_{j=0}^2 \frac{Y^j}{j!}\right) = (I + X + X^2/2)(I + Y + Y^2/2) = I + Y + Y^2/2 + X + XY + XY^2/2 + X^2/2 + X^2/2Y + (XY)^2/2 = I + (X + Y) + (Y^2/2 + XY + X^2/2) + (XY^2/2 + YX^2/2) + (XY)^2/2,$$

where here we collected terms based on the total degree. By inducting and then taking a limit, we have

$$\exp(X) \exp(Y) = \sum_{k=0}^\infty \sum_{j=0}^k \frac{X^j}{j!} \frac{Y^{k-j}}{(k-j)!} = \exp(X+Y).$$


(3) If $$\exp(X)$$ is invertible, then $$\exp(-X) = (\exp(X))^{-1}$$: This follows easily from the prior points, since $$X$$ and $$-X$$ commute and $$X - X = 0$$. Thus

$$ \exp(-X)\exp(X) = \exp((-X) + X) = \exp(0) = I_n = \exp(0) = \exp(X + (-X)) = \exp(X)\exp(-X).$$

(4) For all $$a, b \in F$$, we have $$\exp((a+b)X) = \exp(aX) \exp(bX)$$: Again, this is just (2) written in a fancy way. Notice $$aXbX = (ab)X^2 = (ba)X^2 = bXaX$$, so we have

$$\exp((a+b)X) = \exp(aX + bX) = \exp(aX)\exp(bX).$$

(5) If $$Y$$ is invertible, then $$\exp(YXY^{-1}) = Y \exp(X) Y^{-1}$$: Notice that for $$k \geq 0$$ an integer we have

$$ (YXY^{-1})^k = YX^kY^{-1},$$

so

$$\exp(YXY^{-1}) = \sum_{k=0}^\infty \frac{(YXY^{-1})^k}{k!} = \sum_{k=0}^\infty Y \frac{X^k}{k!} Y^{-1} = Y\left( \sum_{k=0}^\infty \frac{X^k}{k!}\right)Y^{-1} = Y \exp(X) Y^{-1}.$$

The final property is the most important, and is reminiscent of what we wrote earlier with the normal exponential function.

(6) Consider the curve $$t \mapsto \exp(tX)$$, then this is a smooth curve with

$$ \frac{d}{dt} \exp(tX) = X \exp(tX):$$

To prove this fact, recall what we mean by derivative at a point. If $$f : \mathbb{R} \rightarrow M_n(F)$$ a function, then it has a derivative at a point $$t = t_0$$ if

$$ \lim_{h \rightarrow 0} \frac{f(t_0 + h) - f(t_0)}{h} =: \frac{d}{dt} f(t) \bigg|_{t=t_0}$$

exists. In our case then, we fix a $$t_0$$ and we examine

$$ \lim_{h \rightarrow 0} \frac{\exp((t_0 + h)X) - \exp(t_0X)}{h}.$$

Recall from earlier properties that this limit can be rewritten as

$$ \lim_{h \rightarrow 0} \frac{\exp(t_0X) \exp(hX) - \exp(t_0X)}{h} = \lim_{h \rightarrow 0} \frac{\exp(t_0X) [\exp(hX) - 1]}{h}.$$

By factoring out, we see that

$$ \frac{d}{dt} \exp(tX) \bigg|_{t = t_0} = \exp(t_0 X) \left( \frac{d}{dt} \exp(tX) \bigg|_{t = 0} \right).$$

So it's just a matter of figuring out what the derivative is at $$0$$. Expanding using the definition, we have

$$ \lim_{h \rightarrow 0} \frac{\exp(hX) - 1}{h}$$ = $$\lim_{h \rightarrow 0} \frac{1}{h} \left( \sum_{k=1}^\infty \frac{h^kX^k}{k!} \right).$$

Since the sum is convergent, for each fixed $$h$$ we can bring in $$1/h$$ under the sum and we are left with

$$ \lim_{h \rightarrow 0} \sum_{k=1}^\infty \frac{h^{k-1}X^k}{k!}.$$

The question now is whether we can bring the limit under the sum. Since the convergence is nice, we can, and so we are left Without

$$ \lim_{h \rightarrow 0} \sum_{k=1}^\infty \frac{h^{k-1}X^k}{k!} = X.$$

Thus we have that the derivative at any point $$t_0$$ is going to be $$X \exp(t_0 X)$, and this is exactly our goal.

Now, suppose we have a function $$x(t) : \mathbb{R} \rightarrow \mathbb{R}^n$$, and suppose that this function satisfies the differential equations

$$ x'(t) = A x(t), \ \ x(0) = x_0 \in \mathbb{R}^n,$$

where $$A \in M_n(\mathbb{R})$$ an $$n \times n$$ matrix. Just like in the one-dimensional case, we can solve this with a matrix exponential. Using the above properties, we see that the matrix exponential gives us a solution, since

$$ x(t) = x_0 e^{At} \implies x'(t) = A x_0 e^{At} = A x(t).$$

Moreover it gives us the only solution, since if we had another solution $$x(t)$$ then we can set $$y(t) = e^{-tA}x(t)$$, and

$$ y'(t) = -A e^{-tA} x(t) + e^{-tA} x'(t) = -A e^{-tA} x(t) + A e^{-tA} x(t) = 0.$$

So this function is constant, and we know $$y(0) = x(0) = x_0$$, so

$$x_0 = e^{-tA} x(t) \implies e^{tA} x_0 = x(t).$$

There are other interesting properties of the matrix exponential I'd like to explore, but this at least covers the ODE I've forgotten. 
