---
layout: post
title: Recitation Sixteen
tag: [MA1172]
---

In this recitation, we covered power series.

# Power Series

Last time, we talked about Taylor polynomials. Recall that if we can take enough derivatives, then the $$n$$th Taylor polynomial of $$f(x)$$ centered at $$x=a$$ is given by

$$ p_n(x) = \sum_{k=0}^n \frac{f^{(k)}(a)}{k!}(x-a)^k.$$

We now want to think about what happens as we let $$n \rightarrow \infty$$. We don't really have the proper tools to attack this, though. The series we looked at beforehand were all sums of constants, and now this is a sum with a variable. The goal of this section is to build the theory necessary for us to analyze series of this form.

A **power series** is a series of the form

$$ \sum_{k=0}^\infty a_k (x-c)^k,$$

where the $$a_k$$'s are the **coefficients** and $$c$$ is the **center**. Notice that this definition [apriori](https://www.merriam-webster.com/dictionary/a%20priori) has nothing to do with Taylor series -- this is just an abstract series which has some coefficients and variables. Just like before, we are interested in whether or not this series converges, but now we are interested in when this series converges for different $$x$$ values. For example, let's look at the series

$$ \sum_{k=0}^\infty x^k.$$

This is a power series with coefficients $$a_k = 1$$ and center $$c = 0$$. If we plug in $$x = 0.5$$, then this series converges because it is a geometric series. In fact, we can plug in any $$-1 < x < 1$$ and this series will converge. But plugging in $$x > 1$$ or $$x < -1$$ leads us to problems, as we saw earlier. The "output" of this function only makes sense on the domain $$-1 < x < 1$$.

Let's go back to the abstract definition of a power series:

$$ \sum_{k=0}^\infty a_k (x-c)^k.$$

If we plug in $$x=c$$, then clearly the series converges regardless of the coefficients. What happens if the series diverges for some $$x$$ but also converges for some $$x \neq c$$? It is a fact that there is going to be some $$R > 0$$ so that the series converges for all $$x$$ satisfying $$c-R < x < c+R$$ and diverges for all $$x < c-R$$ and for all $$x > c+R$$. Notice that I'm careful to avoid talking about $$x = c-R$$ and $$x = c+R$$ -- we'll come back to this later. We call this $$R$$ the **radius of convergence**. Let's look at an example.

**Example:** Consider the power series

$$ \sum_{k=0}^\infty \frac{x^k}{k!}.$$

Given any fixed $$x$$, we claim the series converges. Assuming $$x$$ is fixed, let

$$a_k := \frac{x^k}{k!}, \text{ so } a_{k+1} = \frac{x^{k+1}}{(k+1)!} = \frac{x}{k+1} a_k.$$

Rearranging yields

$$\frac{a_{k+1}}{a_k} = \frac{x}{k+1}.$$

Since $$x$$ is fixed, the right hand side goes to zero as $$k$$ tends to infinity. By the ratio test, the series converges for any $$x$$, so the radius of convergence is infinity.

**Example:** Suppose we have

$$ \sum_{k=3}^\infty a_k (x-3)^k$$

converges when $$x = 7$$ and diverges when $$x = -1$$. Notice that $$7-3 = 4$$, so the radius of convergence $$R$$ must be bigger than $$4$$. This means that for every $$x$$ in the interval $$(3-4, 3+4) = (-1,7)$$, the series converges. In particular, the series will converge at $$x=4$$.

**Example:** Consider the series

$$ \sum_{k=2}^\infty \frac{(x-2)^k}{k \cdot 3^k}.$$

Fixing $$x$$, let

$$a_k = \frac{(x-2)^k}{k \cdot 3^k}, \text{ so } a_{k+1} = \frac{(x-2)^{k+1}}{(k+1) 3^{k+1}} = \frac{x-2}{(k+1) 3} \frac{(x-2)^k}{3^k}.$$

We can rewrite this as

$$a_{k+1} = \frac{k(x-2)}{(k+1)3} a_k \text{ or } \frac{a_{k+1}}{a_k} = \frac{k(x-2)}{3(k+1)}.$$

The dominant term on top is $$(x-2)k$$ and the dominant term on the bottom is $$3k$$. As long as $$-3 < x-2 < 3,$$ then the ratio test tells us that the series converges. We can rewrite this as $$-1 < x < 5.$$ Notice the ratio test tells us nothing about when $$x = -1$$ or $$x=5$$. Plugging in $$x=5$$ gives us a divergent series, since we would have

$$ \sum_{k=2}^\infty \frac{(5-2)^k}{k \cdot 3^k} = \sum_{k=2}^\infty \frac{1}{k},$$

while plugging in $$x = -1$$ will give us a convergent series (the [alternating harmonic series](https://mathworld.wolfram.com/AlternatingHarmonicSeries.html)):

$$ \sum_{k=2}^\infty \frac{(-1-2)^k}{k \cdot 3^k} = \sum_{k=2}^\infty \frac{(-1)^k}{k}.$$

# Algebra of Power Series

We'll write power series functionally from now on. Let

$$f(x) := \sum_{n=0}^\infty a_n (x-c)^n \text{ and } g(x) := \sum_{n=0}^\infty b_n (x-c)^n.$$

If $$f(x)$$ and $$g(x)$$ both converge absolutely for $$x$$ in the interval $$(c-R, c+R)$$, then

$$ f(x) \pm g(x) = \sum_{n=0}^\infty (a_n \pm b_n) (x-c)^n.$$

Multiplication is trickier. Let's approach this with partial sums. Define

$$f_N(x) := \sum_{n=0}^N a_n (x-c)^n \text{ and } g_N(x) := \sum_{n=0}^N b_n (x-c)^n.$$

For $$N=0$$, we clearly have

$$f_0(x) g_0(x) = a_0b_0.$$

For $$N=1$$, we have

$$ f_1(x) g_1(x) = (f_0(x) + a_1(x-c))(g_0(x) + b_1(x-c)) = f_0(x)g_0(x) + f_0(x) b_1(x-c) + g_0(x) a_1(x-c) + a_1b_1(x-c)^2.$$

Combining like terms:

$$ f_1(x) g_1(x) = (f_0(x) + a_1(x-c))(g_0(x) + b_1(x-c)) = a_0b_0 + [a_0b_1 + b_1 a_0] (x-c)+ a_1b_1(x-c)^2.$$

Let's do one more. Notice

$$ f_2(x) g_2(x) = (f_1(x) + a_2(x-c)^2)(g_1(x) + b_2(x-c)^2) = f_1(x)g_1(x) + f_1(x) b_2(x-c)^2 + g_1(x) a_2(x-c)^2 + a_2b_2(x-c)^4.$$

Notice

$$f_1(x) b_2(x-c)^2 = (a_0 + a_1(x-c)) b_2(x-c)^2 = a_0b_2 (x-c)^2 + a_1 b_2 (x-c)^3.$$

Something similar happens with $$g$$. Combining like terms:

$$ f_2(x) g_2(x) = (f_1(x) + a_2(x-c)^2)(g_1(x) + b_2(x-c)^2) = f_1(x)g_1(x) + (a_0 b_2 + a_2 b_0)(x-c)^2 + (a_1b_2 + a_2b_1)(x-c)^3 + a_2b_2(x-c)^4.$$

Finally, substitute in our previous answer to get

$$ f_2(x)g_2(x) = a_0b_0 + (a_1b_0 + a_0b_1)(x-c) + (a_2 b_0 + a_1b_1 + a_2b_0)(x-c)^2 + (a_2b_1 + a_1b_2)(x-c)^3 + a_2b_2(x-c)^4.$$

Notice that the degree of $$(x-c)$$ multiplied to $$a_k b_j$$ is $$k+j$$. We can deduce the following formula:

$$f(x) g(x) = \sum_{n=0}^\infty \left( \sum_{k=0}^n a_k b_{n-k} \right)(x-c)^n.$$

Notice we have a double sum here.

Finally, for a continuous function $$h(x)$$, as long as $$c-R < h(x) < c+R$$, then we have

$$f(h(x)) = \sum_{n=0}^\infty a_n (h(x) - c)^n.$$

We will also be sloppy, and as long as the series converges we'll say that we can take derivatives and integrate (note that in general this is hard to prove and may not even be true). Using this, though, we can get away with a lot of cool tricks.

**Example:** Recall

$$ \sin(x) = \sum_{k=0}^\infty \frac{(-1)^k x^{2k+1}}{(2k+1)!}.$$

Notice that if we ignore issues with convergence, we can write

$$ \frac{\sin(x)}{x} = \sum_{k=0}^\infty \frac{(-1)^k x^{2k}}{(2k+1)!}.$$

Here are some fun identities we can deduce. If we plug in $$x = \pi$$, then

$$ \frac{\sin(\pi)}{\pi} = 0 = \sum_{k=0}^\infty \frac{(-1)^k \pi^{2k}}{(2k+1)!}.$$

If we take the limit as $$x$$ tends to $$0$$, we get

$$ \lim_{x \rightarrow 0} \frac{\sin(x)}{x} = \sum_{k=0}^\infty \frac{(-1)^k 0^{2k}}{(2k+1)!} = 1,$$

so we rederive that formula again.




# Applications

As you have experienced at this point, it is really annoying that there is no real number such that $$x^2 + 1 = 0$$. In other words, we wish we could take the square root of negative numbers. What we could do is make up a symbol $$i$$ which represents what this quantity should be, i.e. $$i$$ satisfies $$i^2 = -1$$. Note that this should not be upsetting to you, since this is exactly what we're doing when we look at something like $$\sqrt{2}$$ -- this is just some up symbol which represents a solution to $$x^2 - 2 = 0.$$ Doing so opens up a world of math called [complex analysis](https://mathworld.wolfram.com/ComplexAnalysis.html#:~:text=Complex%20analysis%20is%20the%20study,the%20solution%20of%20physical%20problems.). We won't really get into it now, but I will spoil a nice feature of complex analysis. We will be skipping over a lot of rigor, so it is okay to be confused and have questions.

Taking the Taylor series of $$e^x$$ centered at $$x=0$$, we get the following power series representation:

$$e^x = \sum_{k=0}^\infty \frac{x^k}{k!}.$$

Let's blindly plug in $$ix$$ for $$x$$ and see what happens. Notice that

$$i^1 = i, \ i^2 = -1, \ i^3 = -i, \ i^4 = 1, \ i^5 = i, \ldots$$

Recall the remainder function from the previous recitation: $$R(n)$$ represents the remainder of $$n$$ after dividing by $$4$$. We can write

$$i^k = \begin{cases} 1 \text{ if } R(k) = 0 \\ i \text{ if } R(k) = 1 \\ -1 \text{ if } R(k) = 2 \\ -i \text{ if } R(k) = 3. \end{cases}$$

Plugging this into the series (and ignoring issues of convergence), we get

$$e^{ix} = \sum_{k=0}^\infty \frac{(ix)^k}{k!} = \sum_{k=0}^\infty \frac{(-1)^k x^{2k}}{(2k)!} + i \sum_{k=0}^\infty \frac{(-1)^{k} x^{2k+1}}{(2k+1)!}.$$

These series seem familiar -- they are the Taylor series of $$\cos(x)$$ and $$\sin(x)$$ centered at $$x=0$$. So we can write

$$e^{ix} = \cos(x) + i \sin(x).$$

This is called [Euler's formula](https://en.wikipedia.org/wiki/Euler%27s_identity). This is a powerful identity that let's us do trigonometry without having to really do anything. For example, since $$\cos(x)$$ is an [even function](https://www.mathsisfun.com/algebra/functions-odd-even.html) and $$\sin(x)$$ is an [odd function](https://www.mathsisfun.com/algebra/functions-odd-even.html), we have

$$e^{-ix} = \cos(-x) + i \sin(-x) = \cos(x) - i \sin(x).$$

So

$$ e^{ix} + e^{-ix} = 2 \cos(x) \implies \cos(x) = \frac{e^{ix} + e^{-ix}}{2}.$$

On the other hand,

$$ e^{ix} - e^{-ix} = 2 i \sin(x) \implies \sin(x) = \frac{e^{ix} - e^{-ix}}{2i}.$$

Let's prove the half-angle identity using this. We see that

$$ \cos^2(x) = \left(\frac{e^{ix} + e^{-ix}}{2} \right) \left(\frac{e^{ix} + e^{-ix}}{2} \right) = \frac{e^{2 ix} + 2 + e^{-2ix}}{4} = \frac{e^{2ix} + e^{-2ix}}{4} + \frac{1}{2}.$$

Now

$$ \frac{e^{2ix} + e^{-2ix}}{4} = \frac{1}{2} \left( \frac{e^{2ix} + e^{-2ix}}{2} \right) = \frac{\cos(2x)}{2},$$

so we can rewrite this as

$$\cos^2(x) = \frac{\cos(2x) + 1}{2}.$$

No triangles needed!
