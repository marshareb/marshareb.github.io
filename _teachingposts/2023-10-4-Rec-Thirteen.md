---
layout: post
title: Recitation Thirteen
tag: [MA1172]
---

In this recitation, we covered series.

# Series

Given a sequence $$(a_n)_{n \geq 0}$$, we can form the sequence of **partial sums**:

$$ s_n := \sum_{k=0}^n a_k.$$

From our old sequence, we have generated a new sequence. We are interested in determining when this new sequence converges, just like with sequences. There's not much new in terms of theory, but we do need to practice the new notation.

**Example:** Consider a geometric sequence $$a_n = c \cdot r^n$$. Let's look at the partial sums:

$$s_n = \sum_{k=0}^n a_k = \sum_{k=0}^n c r^k = c \left( \sum_{k=0}^n r^k \right).$$

Let's do a trick. Notice

$$ \sum_{k=0}^{n} (r^{k+1} - r^k) = \sum_{k=1}^{n+1} r^k - \sum_{k=0}^n r^k =  r^{n+1} - 1.$$

Also notice

$$ \sum_{k=0}^{n} (r^{k+1} - r^k) = \sum_{k=0}^{n+1}r^k(r - 1) = (r-1) \sum_{k=0}^{n} r^k.$$

So rearranging, we get

$$ \sum_{k=0}^n r^k = \frac{r^{n+1}-1}{r-1} = \frac{1 - r^{n+1}}{1-r}.$$

This tells us that the partial sums are

$$s_n = \frac{c(1-r^{n+1})}{1-r}.$$

Now if $$-1 < r < 1$$ then we can take a limit on the inside to get

$$\lim_{n \rightarrow \infty} s_n = \sum_{k=0}^\infty r^k = \frac{c}{1-r}.$$

Otherwise, the series diverges.

A property we observed above is telescoping. Given a sequence $$(a_n)$$, we can form a new sequence called a **telescoping sequence** which consists of the difference of consecutive elements:

$$t_n = a_{n+1} - a_n.$$

If we take the partial sums of a telescoping sequence, then we have

$$ \sum_{k=1}^n t_k = \sum_{k=1}^n (a_{k+1} - a_k) = (a_2 - a_1) + (a_3 - a_2) + \cdots + (a_{n+1} - a_n).$$

Notice that things cancel:

$$ \sum_{k=1}^n t_k = \sum_{k=1}^n (a_{k+1} - a_k) = a_{n+1} - a_1.$$

This will always happen for a telescoping sequence.

**Example:** Fix your favorite positive integer $$r$$ and consider the sequence

$$a_n = \frac{1}{(n+r)n}.$$

Using partial fractions, we can write this as

$$\frac{1}{(n+r)n} = \frac{A}{n+r} + \frac{B}{n}.$$

Rearranging:

$$ 1 = A(n) + B(n+r).$$

If we plug in $$n =0$$, we get that $$Br = 1$$, or $$B = \frac{1}{r}.$$ If we plug in $$n= -r$$, we get $$1 = A(-r)$$ or $$A = -1/r.$$ So we can write

$$ \frac{1}{(n+r)n} = -\frac{1}{r(n+r)} + \frac{1}{(n)r}.$$

Notice if $$r=1$$ then we have

$$ \frac{1}{(n+1)n} = \frac{1}{n} - \frac{1}{n+1}.$$

This is a telescoping sequence! From the earlier principle, we see that

$$ \sum_{k=1}^n \frac{1}{(k+1)k} = 1 - \frac{1}{n+1},$$

and taking the limit we get

$$ \sum_{k=1}^\infty \frac{1}{(k+1)k} = 1.$$

For general $$r > 1$$, it's not quite telescoping, but it is close. I'll come back to this problem later, but I just want to point out telescoping is not always the answer.

The final thing to mention for this section is the tail of a series. Given a sequence $$(a_n)_{n \geq 0}$$, we form the partial sums by looking at

$$ \sum_{k=0}^n a_k.$$

The **tail** of this sequence is any partial sum which doesn't start at $$k=0$$. For example, if we start at $$3$$ instead, we have

$$ \sum_{k=3}^n a_k$$

is the tail of the series. Suppose we have a tail starting at $$k_0$$, then we can always write

$$ \sum_{k=0}^\infty a_k = \sum_{k=0}^{k_0-1} a_k + \sum_{k=k_0}^\infty a_k.$$

Notice that the middle term is a finite sum of real numbers, so this is always finite. We can conclude the following powerful fact.

**Fact:** A series converges if and only if every tail converges.

In other words, the term on the left is finite if and only if the term on the far right is finite for any choice of $$k_0$$. The above equation is also useful for calculating the tail of a series.

**Example:** Suppose we know

$$ \sum_{k=1}^\infty \frac{1}{k^2} = \frac{\pi^2}{6}.$$

Let's calculate

$$\sum_{k=3}^\infty \frac{1}{k^2}.$$

Using the previous expression, we can write

$$ \frac{\pi^2}{6} = \sum_{k=1}^\infty \frac{1}{k^2} = \sum_{k=1}^2 \frac{1}{k^2} + \sum_{k=3}^\infty \frac{1}{k^2}.$$

It's easy to calculate the middle term:

$$ \sum_{k=1}^2 \frac{1}{k^2} = 1 + \frac{1}{4} = \frac{5}{4}.$$

So we rearrange and get

$$ \frac{\pi^2}{6} - \frac{5}{4} = \sum_{k=3}^\infty \frac{1}{k^2}.$$

**Remark:** The original series (starting at $$k=1$$) is a hard one, and we don't have the tools to actually figure out this answer. If you are interested, this is [Basel's problem](https://en.wikipedia.org/wiki/Basel_problem).
