---
layout: post
title: Recitation Fifteen
tag: [MA1172]
---

In this recitation, we covered Taylor series and some problems from the mock series midterm.

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

# Mock Series Midterm

Here are some variations of the harder problems from the mock series midterm.

**Problem:** Taylor is asked to determine if

$$ \sum_{k=1}^\infty [\ln(k+4) - \ln(k+3)]$$

converges. They give the following argument: Since $$\ln(k+4) - \ln(k+3) = \ln \left(\frac{k+4}{k+3} \right)$$, we see that

$$ \lim_{k \rightarrow \infty} [\ln(k+4) - \ln(k+3)] = \ln(1) = 0,$$

so the series converges. We are supposed to evaluate Taylor's argument, and if it is wrong state a correct argument. The idea is that Taylor is trying to use the divergence test to prove convergence, which as we discussed is not useful. What they have shown is that the divergence test fails, but this does not tell us that the series converges. We need to do more in order to prove this.

Let $$a_k = \ln(k+3)$$, then $$a_{k+1} = \ln((k+1) + 3) = \ln(k+4)$$ and

$$ \sum_{k=1}^\infty [\ln(k+4) - \ln(k+3)] = \sum_{k=1}^\infty [a_{k+1} - a_k].$$

The series is telescoping! If we look at the partial sums, we have

$$ s_n := \sum_{k=1}^n [a_{k+1} - a_k] = (a_2 - a_1) + (a_3 - a_2) + \cdots + (a_n - a_{n-1}) + (a_{n+1} - a_n) = a_{n+1} - a_1.$$

 Plugging in numbers,

$$s_n = a_{n+1} - a_1 = \ln(n+4) - \ln(4) = \ln \left( \frac{n+4}{4} \right).$$

Taking the limit, we see that

$$ \sum_{k=1}^\infty  [\ln(k+4) - \ln(k+3)]  = \lim_{n \rightarrow \infty} s_n = \infty,$$

so the series diverges.

**Problem:** Brad needs to determine if the series

$$ \sum_{k=1}^\infty \frac{(2k+4)!}{2^{k^2}}$$

converges and is confused how to start. Observe that growth rates do not apply because it is a degree two polynomial in the exponent instead of a linear term. To determine if it converges, let's try a ratio test. Define

$$a_k = \frac{(2k+4)!}{2^{k^2}},$$

so

$$a_{k+1} = \frac{(2k+6)!}{2^{k^2 + 2k + 1}} = \frac{(2k+6)(2k+5)}{2^{2k+1}} a_k.$$

Rearranging, we get

$$ \frac{a_{k+1}}{a_k} = \frac{(2k+6)(2k+5)}{2 \cdot 4^k}.$$

An exponential grows faster than any polynomial, so we get $$\lim_{k \rightarrow \infty} a_{k+1}/a_k = 0.$$ The ratio test tells us the series converges. Since the series converges, notice that the divergence test tells us that

$$ \lim_{k \rightarrow \infty} \frac{(2k+4)!}{2^{k^2}} = 0.$$

**Problem:** We wish to calculate

$$ \lim_{n \rightarrow \infty} \left(1 - \frac{2}{n+1} \right)^{2n}.$$

Let

$$a_n = \left(1 - \frac{2}{n+1} \right)^{2n}.$$

For $$n$$ large we have that $$a_n > 0,$$ so

$$ a_n = e^{\ln(a_n)}.$$

Next, notice

$$ \ln(a_n) = 2n \ln \left(1 - \frac{2}{n+1} \right) = \frac{\ln \left( \frac{n-1}{n+1} \right)}{\frac{1}{2n}}.$$

This is indeterminate of the form $$0/0$$, so we can apply L'Hopital's rule:

$$ \lim_{n \rightarrow \infty} \ln(a_n) = \lim_{n \rightarrow \infty} -\frac{\frac{2}{n^2-1}}{ \frac{1}{2n^2}} = - \lim_{n \rightarrow \infty} \frac{4n^2}{n^2 - 1} = -4.$$

Here we use growth rates. By continuity of the exponential:

$$ \lim_{n \rightarrow \infty} a_n = e^{\lim_{n \rightarrow \infty} \ln(a_n)} = e^{-4}.$$

**Remark:** The definition of $$e$$ comes from compound interest. If we invest $$P$$ dollars into an account, then the idea behind interest is that we should earn a percentage back for each time interval (the number of times it is "compounded"). So if the interest rate is $$r$$ and it is compounded four times a year, then in two years we should have

$$ P \left(1 + \frac{r}{4} \right)^{2 \cdot 4}.$$

If it is compounded $$n$$ times a year, then after $$t$$ years we should have

$$ P \left(1 + \frac{r}{n} \right)^{nt}.$$

How much would we earn if it was continuously compounded? If we compound it "infinitely" often, then we would earn

$$ \lim_{n \rightarrow \infty} P \left(1 + \frac{r}{n} \right)^{nt}.$$

Dividing by $$P$$ and setting $$t=1$$ tells us the percentage we would earn after one year:

$$ \lim_{n \rightarrow \infty}  \left(1 + \frac{r}{n} \right)^{n}.$$

Just like in the previous problem, we can solve this using logarithms. Let

$$a_n =  \left(1 + \frac{r}{n} \right)^{n}, \text{ so } \ln(a_n) = n \ln \left(1 + \frac{r}{n} \right).$$

We can do the L'Hopital trick again:

$$ \lim_{n \rightarrow \infty} \ln(a_n) = \lim_{n \rightarrow \infty} \frac{\ln \left( \frac{n+r}{n} \right)}{\frac{1}{n}} = \lim_{n \rightarrow \infty} \frac{ \frac{r}{n(n+r)}}{\frac{1}{n^2}} = \lim_{n \rightarrow \infty} \frac{nr}{n+r} = r.$$

So

$$ \lim_{n \rightarrow \infty} a_n = e^{\lim_{n \rightarrow \infty} \ln(a_n)} = e^r.$$

So the percentage of money we've made after one year is $$e^r$$. If $$r=1$$, then we've rederived Euler's constant following in the footsteps of [Jacob Bernoulli](https://en.wikipedia.org/wiki/Jacob_Bernoulli); see also [here](https://en.wikipedia.org/wiki/Compound_interest#Calculation).

**Problem:** Consider

$$a_n = \frac{(4^n + n^5)^2}{2 \cdot 16^n + \ln(n)^1000}.$$

Suppose we wished to calculate $$\lim_{n \rightarrow \infty} a_n$$. Recall that logarithms grow slower than exponentials, so

$$ \lim_{n \rightarrow \infty} a_n = \frac{(4^n + n^5)^2}{2 \cdot 16^n}.$$

Since polynomials grow slower than exponentials:

$$ \lim_{n \rightarrow \infty} a_n = \frac{16^n}{2 \cdot 16^n} = \frac{1}{2}.$$

**Problem:** Consider

$$a_n = 5n^2 + 1.$$

Suppose we wished to calculate $$\lim_{n \rightarrow \infty} a_{n+1}/a_n.$$ Notice that using growth rates, we don't need to do anything -- $$a_{n+1}$$ grows at a rate of $$5n^2$$ and $$a_n$$ grows at a rate of $$5n^2$$, so this limit is one.
