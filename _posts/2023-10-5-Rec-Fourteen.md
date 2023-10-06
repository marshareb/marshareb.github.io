---
layout: post
title: Recitation Fourteen
tag: [MA1172]
---

In this recitation, we covered the divergence test and the ratio test.

# The problem of convergence

Sometimes, it is more useful to know that a series or sequence converges than to know what it converges to. For example, a famous problem is the [twin prime conjecture](https://www.britannica.com/science/twin-prime-conjecture), which says there are infinitely many [prime numbers](https://en.wikipedia.org/wiki/List_of_prime_numbers) (numbers whose only factors are $$1$$ and itself) which differ by $$2$$. Knowing the behavior of primes is important for things like [cryptography](https://en.wikipedia.org/wiki/Cryptography), and while the twin prime conjecture by itself may not be immediately useful, the techniques used to solve it could be very useful.

One can "rewrite" the twin prime conjecture as follows. Let $$(p_n)$$ be the sequence of prime numbers, so $$p_1 = 2, p_2 = 3, p_3 = 5, p_4 = 7, p_5 = 11,$$ and so on. We can create a new sequence by setting

$$a_n = \begin{cases}1 \text{ if } p_n+2 \text{ is prime}, \\ 0 \text{ otherwise}. \end{cases}$$

Writing out a few terms, $$a_1 = 0$$ (since $$2+2=4$$), $$a_2 = 1$$ (since $$3+2=5$$), $$a_3 = 1, a_4 = 0, a_5 = 1,$$ and so on. If there are infinitely many twin primes, then the series

$$ \sum_{n=1}^\infty a_n$$

diverges, otherwise it converges. It doesn't really matter what it converges to (although I guess it would be nice to know how many twin primes there are), but rather we just want to know if it does converge. The [Riemann hypothesis](https://en.wikipedia.org/wiki/Riemann_hypothesis), another famous problem, can also be encoded into a series like this (though the set up is very complicated), and determining the convergence of this series would get you a million dollars (and you would also solve many of math's deep problems).

As engineers, you will probably not be thinking about such complicated series, but series do come up a lot. For example, [Fourier analysis](https://en.wikipedia.org/wiki/Fourier_analysis) is going to be a useful tool for solving [differential equations](https://en.wikipedia.org/wiki/Differential_equation), and you will probably be using stuff like this throughout your entire career. Fourier analysis is built on the back of convergent series, and to even know if it works we have to have tools that tell us the convergence of series. This leads us into the next few sections.

# Divergence test

The divergence test is a useful tool which tells us when we shouldn't even bother trying to study the convergence of a series. We have to be careful though -- its easy to get confused when using it.

Suppose $$(a_n)$$ is a sequence and $$(s_n)$$ is the sequence of partial sums. Let's suppose $$\lim_{n \rightarrow \infty} a_n = 2$$ (the number doesn't matter, as long as it is not zero). Recall that for "very large" $$n$$, we have that $$a_n$$ is "close" to $$2$$. Let's say that $$N$$ is large enough so that for all $$n \geq N$$, we have $$a_n$$ is between $$1.5$$ and $$2.5$$ (which has to happen for some $$N$$ since it converges). Recall from the previous recitation that the series converges if and only if its tails converge, so let's just study the tail

$$\sum_{n=N}^\infty a_n.$$

Since $$1.5 \leq a_n \leq 2.5$$, we have

$$ \sum_{n=N}^\infty 1.5 \leq \sum_{n=N} a_n \leq \sum_{n=N}^\infty 2.5.$$

On the left and right, we have an infinite series with a constant, so these diverge to infinity. By the squeeze theorem, we get that the middle has to also diverge to infinity, and so the series diverges. One can take this logic and generalize it as follows.

**Theorem:** If $$(a_n)$$ is a sequence with $$\lim_{n \rightarrow \infty} a_n \neq 0$$ (which includes diverging), then $$\sum_{n=0}^\infty a_n$$ diverges.

**Warning:** If $$\lim_{n \rightarrow \infty} a_n = 0$$, then we don't know anything. For example, consider the series

$$\sum_{k=1}^\infty \ln \left( \frac{k+1}{k} \right).$$

This series is associated to the sequence

$$a_k = \ln \left( \frac{k+1}{k} \right).$$

Since natural log is continuous, we have

$$\lim_{k \rightarrow \infty} a_k = \ln \left( \lim_{k \rightarrow \infty} \frac{k+1}{k}\right) = \ln(1) = 0.$$

However, we can also write

$$  \ln \left( \frac{k+1}{k} \right) = \ln(k+1) - \ln(k),$$

so this is a telescoping series, and

$$\sum_{k=1}^n  \ln \left( \frac{k+1}{k} \right) = \ln(n).$$

Taking the limit of this as $$n$$ tends to infinity shows this diverges.

**Example:** Suppose $$(a_n)$$ is a sequence and we know that $$\sum_{n=1}^\infty a_n = 0$$. Let

$$s_n = \sum_{k=1}^n a_k.$$

The divergence test tells us that
- $$\lim_{n \rightarrow \infty} a_n = 0$$ by the divergence test, since the series is convergent.
- $$\lim_{n \rightarrow \infty} s_n = 0$$, by definition.
- $$\sum_{k=1}^\infty s_k$$ converges by the divergence test, since the limit is zero.

Note if the series converges to a number that is not zero, then the last series (with the $$s_k$$) would be divergent.

# Ratio test

There are many monotonic sequences whose corresponding series diverge. It's clear that an additive relationship doesn't give us much interesting information when it comes to studying convergence. One might try to guess that having multiplicative information might be more valuable. For example, let's suppose that we know $$a_{n+1}/a_n > 0$$ for all $$n$$ and

$$ \lim_{n \rightarrow \infty} \frac{a_{n+1}}{a_n} = L > 0.$$

This means that for every large $$n$$, we have that $$a_{n+1}/a_n$$ is close to $$L$$. In particular, if $$\epsilon$$ is very small, then this tells us that there is an $$N$$ so that for all $$n \geq N$$ we have

$$ (L-\epsilon) a_n \leq a_{n+1} \leq (L+\epsilon) a_n.$$

Notice we can iterate this:

$$ (L-\epsilon)^2 a_{n} \leq (L-\epsilon)a_{n+1} \leq  a_{n+2} \leq (L+\epsilon)a_{n+1} \leq (L+\epsilon)^2 a_n.$$

In particular, we can keep iterating this to deduce that for all $$k \geq 0$$ we have

$$(L-\epsilon)^k a_n \leq a_{n+k} \leq (L+\epsilon)^k a_n.$$

There are two cases of interest for us. First, let's think about what happens if $$L > 1$$. If $$L > 1$$ and $$\epsilon$$ is small enough so that $$L-\epsilon > 1$$, then the above inequality tells us

$$ a_N \sum_{k=N}^\infty (L-\epsilon)^k \leq \sum_{k=N}^\infty a_k \leq a_N \sum_{k=N}^\infty (L+\epsilon)^k.$$

Notice that the left and right series are geometric series. Since $$L-\epsilon > 1$$, we can use the squeeze theorem to deduce that the middle has to diverge. Since the tail diverges, our good old fact tells us that the original series diverges as well.

Next, what happens if $$L < 1$$? Suppose $$\epsilon$$ is small enough so that $$L + \epsilon < 1$$. Then the above inequality again tells us

$$ a_N \sum_{k=N}^\infty (L-\epsilon)^k \leq \sum_{k=N}^\infty a_k \leq a_N \sum_{k=N}^\infty (L+\epsilon)^k.$$

Again, a geometric series, except this time $$0 < L-\epsilon < L + \epsilon < 1$$. We can deduce that the outside series converge, so the squeeze theorem forces the inside to converge. Since the tail converges, the original series converges.

What happens if $$L = 1$$? Well, things are complicated. Essentially the left series will always converge and the right series will always diverge, so we don't know anything about the middle series.

I made a few unnecessary assumptions above, mostly because the math compiler for this website does not like the absolute value sign. In reality, things don't have to be positive, the above arguments work just the same. We can summarize with the following.

**Theorem:** Suppose $$(a_n)$$ is a sequence such that $$\lim_{n \rightarrow \infty} \mid a_{n+1}/a_n \mid = L.$$
- If $$0 \leq L < 1$$, then the series converges.
- If $$L > 1$$, then the series diverges.

**Warning:** If $$L=1$$, then the above theorem says nothing. The series could converge or diverge.

The ratio test is useful for things which are defined recursively or which have nice behavior when it comes to addition (think exponents).

**Example:** Does the series

$$ \sum_{k=10}^\infty \frac{3^k}{(k+1)!}$$

converge or diverge? The first step should be to apply the divergence test. Recall from growth rates that $$(k+1)!$$ grows faster than $$3^k$$, so the limit of the sequence is zero and the divergence test is inconclusive. Now let's try the ratio test. If we let

$$a_k = \frac{3^k}{(k+1)!},$$

then

$$a_{k+1} = \frac{3^{k+1}}{(k+2)!} = \frac{3^k \cdot 3}{(k+1)! \cdot (k+2)} = \frac{3}{k+2} \cdot a_k.$$

So

$$ \frac{a_{k+1}}{a_k} = \frac{3}{k+2}.$$

The limit of this is zero, so the ratio test tells us the series converges.
