---
layout: post
title: Recitation Fifteen
tag: [MA1172]
---

In this recitation, we covered Taylor series.

# Approximations

One way of framing calculus is that we want to study nice enough functions which "locally" look like lines. This leads us to the concept of derivatives and tangent lines; the derivative is the slope of the tangent line, and the tangent line is the best linear approximation at a point. However, a really good question to ask is how good of an approximation this is? For example, if we're given a line, then the tangent line is equal to the line, and so the approximation isn't even an approximation; it is an equality. On other hand, if we look at the function $$f(x) = x^2$$, then the tangent line at $$x=0$$ is

$$ L_0(x) := f(0) + x f'(0) = 0.$$

This is a bad approximation the further we get from $$x=0$$, so we should probably avoid using it. The question now boils down to the following:
1) Is there a way to get a better approximation than a line?
2) Is there a way to tell how bad of an approximation we have?

The answer to both questions can be found in Taylor polynomials. Before going into Taylor polynomials, let's review the tangent line. Remember that the goal of constructing a tangent line at $$x=a$$ is to find a line $$L_a(x)$$ which is the "best approximation" of $$f(x)$$ at the point $$x=a$$. Since it is a line, we know

$$L_a(x) = mx + b,$$

for some $$m$$ and $$b$$. If we plug in $$x=a$$, then we should have

$$L_a(a) = f(a) = ma + b.$$

So we can rearrange our original equation to be in terms of one variable:

$$ L_a(x) = mx + (f(a) - ma) = m(x-a) + f(a).$$

To figure out what $$m$$ is, we want the derivatives of $$f(x)$$ and $$L_a(x)$$ to be the same at $$x=a$$ (i.e. the slope of the infinitesmal line should be the same). Taking the derivative, we have

$$L_a'(x) = m = f'(a),$$

and this eliminates the last variable. We can write

$$L_a(x) = f'(a) (x-a) + f(a).$$

What if we try to do the same thing with a quadratic instead? Let's write

$$Q_a(x) = t_0 + t_1 x + t_2 x^2,$$

where we need to figure out $$t_0, t_1,$$ and $$t_2$$. Again, we want them to be the same at $$x=a$$, so we should have

$$Q_a(a) = t_0 + t_1 a + t_2 a^2 = f(a),$$

and we can solve for $$t_0$$ and substitute this in to get

$$Q_a(x) = f(a) + t_1(x-a) + t_2 (x^2 - a^2).$$

Next, we want the derivatives to be the same, so we have

$$Q_a'(a) = t_1 + 2 t_2 a = f'(a).$$

If we solve for $$t_1$$ and plug it in to the original equation, we have

$$Q_a(x) = f(a) + f'(a)(x-a) + t_2 (x^2 - a^2 - 2ax + 2a^2) = f(a) + f'(a) (x-a) + t_2(x^2 - 2ax + a^2).$$

Notice

$$(x-a)^2 = x^2 - 2ax + a^2,$$

so we can factor the last part as

$$Q_a(x) = f(a) + f'(a)(x-a) + t_2 (x^2 - a^2 - 2ax + 2a^2) = f(a) + f'(a) (x-a) + t_2(x-a)^2.$$

If we want to eliminate this last variable, we will need $$f(x)$$ to have a second derivative. If we assume that, then we want the second derivatives to agree, and we get

$$Q_a''(a) = 2 t_2 = f''(a).$$

Solving for $$t_2$$, we get

$$Q_a(x) = f(a) + f'(a) (x-a) + \frac{f''(a)}{2} (x-a)^2.$$

# Taylor Polynomials

Let's call $$p_n^a(x)$$ the **$$n$$th order Taylor polynomial** at $$x=a$$. We found $$p_1$$ (which is the tangent line) and $$p_2$$ (which is this $$Q_a$$ I wrote a second ago). In general, one can show that

$$p_n^a(x) = \sum_{k=0}^n \frac{f^{(k)}(a)}{k!} (x-a)^k,$$

where $$f^{(k)}(x)$$ is the $$k$$th derivative of $$f(x)$$. Note that we have a nice recursive definition for finding the next Taylor polynomial:

$$ p_{n+1}^a(x) = p_n^a(x) + \frac{f^{(n+1)}(a)}{(n+1)!}(x-a)^{n+1}.$$

This can be useful if we are given partial information about the Taylor polynomial. Intuitively, it might be clear that a higher order Taylor polynomial gives a better approximation, and this is indeed the case. One might also wonder what happens when we keep taking derivatives -- maybe a function is infinitely differentiable. Is this an alternative way of expressing the same function?

**Example:** Recall that derivatives of $$\sin(x)$$ follow a nice pattern. For an integer $$n$$, let's denote $$R(n)$$ to be the remainder of the integer when we divide by $$4$$. For example, $$R(1) = 1, R(2) = 2, R(3) = 3, R(4) = 0, R(5) = 1, R(6) = 2, \ldots$$. We have the following pattern:

$$ \frac{d^k}{dx^k} \sin(x) = \begin{cases} \sin(x) \text{ if } R(k) = 0 \\ \cos(x) \text{ if } R(k) = 1 \\ -\sin(x) \text{ if } R(k) = 2, \\ - \cos(x) \text{ if } R(k) = 3. \end{cases}$$

If we want to find the $$n$$th order Taylor polynomial for $$\sin(x)$$ at $$x=0$$, we would have

$$p_n(x) = \sum_{k=0}^n \frac{(-1)^k}{(2k+1)!} x^{2k+1}.$$

We'll explore soon whether or not

$$\sin(x) = \sum_{k=0}^\infty  \frac{(-1)^k}{(2k+1)!} x^{2k+1},$$

but if you want to play around with this, try plugging in some values into Wolfram and see if they agree. Notice there's a big question here that I am ignoring -- does the series on the right even converge? We'll also explore this soon.
