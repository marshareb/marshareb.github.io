---
layout: post
title: Recitation Twelve
tag: [MA1172]
---

In this recitation, we covered sequences and their limits.

# Sequences

In general, a **sequence** is a collection of objects which appear in "sequential order." More precisely, a **sequence** is a function whose domain is an interval of integers. Ahead of time, the range could be anything, however we're going to be mostly focused on **real-valued sequences**, so functions whose range is a subset of the real numbers. For example, the function

$$f : \{0, 1, 2, \ldots\} \rightarrow \mathbb{R}, \ \ f(n) = 2n+1,$$

is a sequence. However, in this course, we don't usually use this notation. Instead, we denote the sequence by

$$a_n = 2n+1 \text{ for } n \geq 0.$$

This is just two different ways of writing the same thing, but I figured it's a good idea to include the "definition." We're going to use the second way to denote sequences, but remember they are related by setting

$$ f(n) \coloneqq a_n \text{ or } a_n \coloneqq f(n).$$

I'll also write $$(a_n)$$ to denote a sequence. This is just a shorthand for writing

$$(a_n) = (a_n)_{n \geq 0} = \{a_0, a_1, a_2, \ldots\}.$$

If we are not starting at $$0$$, I will try to indicate it with a subscript.

Sequences are useful models for measuring the change of quantities with respect to **discrete time.** When we were talking about functions and limits, we were thinking about things in terms of **continuous time,** which usually makes things more complicated. Arguably, this is taught a little backwards -- we *maybe* should have started with sequences and went into limits of functions from there, but c'est la vie.

We say that a sequence is given in **closed form** if there is a formula expressing all terms. The sequence

$$a_n = 2n + 4$$

is in closed form, since I can calculate $$a_{100}$$ without having to work through the other terms. A sequence is given **recursively** if we need prior information to determine the next entry. The sequence

$$a_n = a_{n-1} + a_{n-2}, \text{ with } a_0 = a_1 = 1,$$

is given recursively. When a sequence is given recursively, we need to know **initial conditions** in order to determine the rest of the sequence. For example, if I did not tell you that $$a_0 = a_1 = 1$$ in the above sequence, there is no way to determine what $$a_2$$ is.

There are two "basic" sequences we are interested in. We say that a sequence is **arithmetic** if the difference of subsequent terms is constant. In other words, we say $$(a_n)$$ is arithmetic if there is a constant $$C$$ so that for all $$n \geq 0$$ we have $$a_{n+1} - a_n = C$$. Notice that arithmetic sequences are defined recursively:

$$a_{n+1} = a_n + C.$$

Let's assume that we know $$a_0$$; maybe $$a_0 = D$$ for some constant $$D$$. Then

$$a_1 = a_0 + C = D + C, \ \ a_2 = a_1 + C = (D+C)+C = D+2C,$$

and so on. In fact, we can guess what the closed form is of an arithmetic sequence -- it probably looks like

$$a_n = a_0 + Cn = D + Cn.$$

This just follows from iterating the recursive procedure $$n$$-times (if you are interested, you can prove this using [induction](https://en.wikipedia.org/wiki/Mathematical_induction)).

We say that a sequence is **geometric** if the ratio of subsequent terms is constant. In other words, we say $$(a_n)$$ is geometric if there is a constant $$C$$ so that for all $$n \geq 0$$ we have $$\frac{a_{n+1}}{a_n} = C.$$ Again, let's assume we know $$a_0 = D$$. We see that this gives us a recursive formula to determine the next term:

$$a_{n+1} = C a_n,$$

so we can use $$a_0$$ to get

$$ a_1 = C a_0 = C D, \ \ a_2 = C a_1 = C (CD) = C^2 D.$$

Like before, we can determine that the closed form for a geometric sequence is

$$ a_n = a_0 \cdot C^n = D \cdot C^n.$$

Finally, we say that a sequence $$(a_n)$$ is **modeled** by a function $$f : \mathbb{R} \rightarrow \mathbb{R}$$ if we have

$$f(n) = a_n \text{ for all } n \geq 0.$$

## Factorials

Before we go, let's review one recursive sequence we're going to use over and over. Let

$$a_0 = 1, \ \ a_n = n \cdot a_{n-1}.$$

Notice that

$$a_1 = 1 \cdot a_0 = 1, \ \ a_2 = 2 \cdot 1 = 2, \ \ a_3 = 3 \cdot 2 \cdot 1 = 6.$$

In fact, we see that in general, we have

$$a_n = n \cdot (n-1) \cdot (n-2) \cdot \cdots \cdot 1.$$

This is a special sequence called a **factorial**. You may have seen it written out like this:

$$ 0! = 1 \text{ and } n! = n \cdot (n-1)!.$$

This is the same thing, though. The "exclamation" is just useful notation to indicate that we are preforming the "factorial" operation. Notice that the factorial pops up in the [binomial theorem](https://en.wikipedia.org/wiki/Binomial_theorem). We sometimes write

$$\binom{n}{k} = \frac{n!}{k! \cdot (n-k)!};$$

this is called a **binomial coefficient**. These are useful in combinatorics, where $$\binom{n}{k}$$ is the number of ways to choose $$k$$ unordered things from a collection of $$n$$ things. You can try this out at home -- suppose I hand you four labeled rocks, which we'll denote by $$\{1,2,3,4\}$$. How many ways can I choose two rocks from this collection? On a piece of paper, we can write

$$\{1,2\}, \{1,3\}, \{1,4\}, \{2,3\}, \{2,4\}, \{3,4\}.$$

The "unordered" part means I don't distinguish $$\{1,2\}$$ and $$\{2,1\}$$. We can count six ways of choosing two rocks from a set of four. Notice

$$\binom{4}{2} = \frac{4!}{2! \cdot 2!} = \frac{24}{4} = 6.$$

Cool!

The binomial theorem says

$$(x+y)^n = \sum_{k=0}^n \binom{n}{k} x^k y^{n-k}.$$

Given the logic above, think for a little bit about why binomial coefficients appear. This has surpisingly deep applications in the theory of combinatorics.


# Limits of Sequences

## Definitions and Facts

Let $$(a_n)$$ be a sequence of real numbers. We say that $$a_n$$ **converges** to a number $$L$$ if as $$n$$ gets larger, $$a_n$$ gets closer to $$L$$, and we write

$$ \lim_{n \rightarrow \infty} a_n = L.$$

If a sequence does not converge to a *finite* number, then we say that it **diverges.**

There is a more formal definition for convergence, but we'll avoid it for now and just use the above definition.

**Remark:** Let $$\{n_0, n_1, \ldots\}$$ be a collection of numbers with $$n_k \geq 0$$ for each $$k$$ and $$n_{k+1} > n_k$$. Given a sequence $$(a_n)$$, we can form a new sequence $$(b_k)$$ by setting $$b_k = a_{n_k}.$$ Such a sequence is called a **subsequence**. Notice that if a sequence converges, then its subsequence must also converge, but the opposite is not true.

**Fact:** Let $$(a_n)$$ be a sequence.
- If we can find two subsequences $$(a_{n_k})$$ and $$(a_{n_j})$$ with
$$\lim_{k \rightarrow \infty} a_{n_k} = L \neq D = \lim_{j \rightarrow \infty} a_{n_j},$$
then the sequence $$(a_n)$$ diverges.
- If we can find a subsequence $$(a_{n_k})$$ such that $$\lim_{k \rightarrow \infty} a_{n_k} = \pm \infty$$ or does not exist, then $$a_n$$ diverges.

**Example:** Consider the sequence

$$ a_n = \frac{1}{n}.$$

We hopefully know at this point that $$\lim_{n \rightarrow \infty} a_n = 0$$, but maybe let's reflect on why we know this. Usually, you just wave your hands and say "Well its getting really really small, so of course it has to tend to zero!" To make this handwaving precise, we should show that given any number $$M > 0$$ we can find an $$N$$ so that $$0 < a_n < M$$ for all $$n \geq N$$. Consider $$\frac{1}{M} > 0$$ -- we can find $$N$$ large enough so that $$\frac{1}{M} < N.$$ Let $$n \geq N$$, so $$ \frac{1}{M} < N \leq n.$$ We can rewrite this fraction to get

$$0 < \frac{1}{n} \leq \frac{1}{N} < M.$$

Note we can do this for *any* number $$M > 0$$, so we have that the sequence $$(a_n)$$ will always eventually be smaller than $$M$$. This means that it is approaching zero as $$n$$ gets larger, and so we can conclude that the limit is zero.

**Example:** Consider the sequence

$$a_n = (-1)^n.$$

Let's use our fact above. Consider the subsequences

$$a_{2n} = (-1)^{2n} \text{ and } a_{2n+1} = (-1)^{2n+1}.$$

Notice we can rewrite these as

$$a_{2n} = (-1)^{2n} = ((-1)^2)^n = 1 \text{ and } a_{2n+1} = (-1) \cdot (-1)^{2n} = -1.$$

So $$\lim_{n \rightarrow \infty} a_{2n} = 1$$ and $$\lim_{n \rightarrow \infty} a_{2n+1} = -1$$. Since these are not the same, the original sequence $$(a_n)$$ diverges.

**Fact:** Let $$f(x)$$ be a function modeling the sequence $$a_n$$. If $$\lim_{x \rightarrow \infty} f(x) = L,$$ then $$\lim_{n \rightarrow \infty} a_n = L.$$

**Warning:** The above fact only goes in one direction. For example, the function $$f(x) = \sin(\pi x)$$ models the sequence $$a_n = \sin(\pi n)$$. We know that $$a_n = 0$$ for all $$n$$, so clearly

$$\lim_{n \rightarrow \infty} a_n = 0,$$

but from a graph we can see that

$$\lim_{x \rightarrow \infty} f(x) \text{ does not exist.}$$

## Growth Rates

Given two sequences $$a_n$$ and $$b_n$$, we say that the sequence $$b_n$$ **dominates** $$a_n$$ and write $$a_n \ll b_n$$ if

$$ \lim_{n \rightarrow \infty} \frac{a_n}{b_n} = 0.$$

Even though we're using a "less than" sign, we can't use this to compare any two sequences.

**Example:** Consider the sequences $$a_n = n$$ and $$b_n = 2n$$. Then

$$\lim_{n \rightarrow \infty} \frac{a_n}{b_n} = \frac{1}{2} \text{ and } \lim_{n \rightarrow \infty} \frac{b_n}{a_n} = 2.$$

So it's not true that $$a_n$$ dominates $$b_n$$ or vice versa.

**Example:** Consider a polynomial $$p(x) = a_k x^k + a_{k-1} x^{k-1} + \cdots + a_0$$, with $$a_k \neq 0$$. Consider the polynomial $$q(x) = a_{k-1} x^{k-1} + a_{k-2} x^{k-2} + \cdots + a_0$$; this polynomial has the same coefficients as the polynomial $$p(x)$$, but we took away the highest power. Notice that $$a_{k-1}$$ may be zero, so we don't know the degree of $$q(x)$$ -- we just know it has degree smaller than $$p(x)$$. We claim that $$a_k x^k$$ dominates $$q(x)$$. This formalizes a "trick" that we used in calculus a bunch, namely that the highest power dominates a polynomial when taking limits to infinity. So we're going to show that

$$ \lim_{n \rightarrow \infty} \frac{q(n)}{a_k n^k} = 0.$$

First, let's get rid of the $$a_k$$, as it does not really matter. We're done if we can show

$$ \lim_{n \rightarrow \infty} \frac{q(n)}{ n^k} = 0.$$

Now, we can break up our polynomial, and so we have

$$ \lim_{n \rightarrow \infty} \frac{q(n)}{ n^k} = a_{k-1} \lim_{n \rightarrow \infty} \frac{n^{k-1}}{n^k} + \cdots + a_0 \lim_{n \rightarrow \infty} \frac{1}{n^k}.$$

I'm lying a little bit here -- we can only break up the limits if we know that each term converges. However, it's not hard to see that each term does converge, since its of the form $$n^{-t}$$ for $$t \geq 1$$ a whole number. The limit as $$n$$ tends to infinity of this will be zero, so

$$ \lim_{n \rightarrow \infty} \frac{q(n)}{ n^k} = a_{k-1} \lim_{n \rightarrow \infty} \frac{n^{k-1}}{n^k} + \cdots + a_0 \lim_{n \rightarrow \infty} \frac{1}{n^k} = 0.$$

We're done!

The above example is important, as we're going to use dominant terms to evaluate limits of quotients.

**Fact:** Let $$p(x)$$ and $$q(x)$$ be two polynomials with the degree of $$p(x)$$ smaller than the degree of $$q(x)$$. We have

$$ \lim_{n \rightarrow \infty} \frac{p(n)}{q(n)} = 0.$$

**Example:** Let's calculate

$$ \lim_{n \rightarrow \infty} \frac{n^4}{(1+2n)^6}.$$

I'm lazy and I don't want to expand the polynomial on the bottom. Let's maybe use the [binomial theorem](https://en.wikipedia.org/wiki/Binomial_theorem) to eyeball it -- we know that

$$(1 + 2n)^6 = \sum_{k=0}^6 \binom{6}{k} (2n)^k (1)^{6-k} =  \sum_{k=0}^6 \binom{6}{k} (2n)^k.$$

I only care about the highest power, so this tells me it'll be $$2^6 n^6.$$ Multiplying the top and bottom by $$\frac{1}{n^6}$$, we have

$$ \lim_{n \rightarrow \infty} \frac{n^4}{(1+2n)^6} = \lim_{n \rightarrow \infty} \frac{\frac{n^4}{n^6}}{\frac{(1+2n)^6}{n^6}}.$$

By our previous example, we know that the bottom goes to $$2^6$$. The top is easy to do independently, and it goes to zero. So all together,

$$ \lim_{n \rightarrow \infty} \frac{n^4}{(1+2n)^6} = 0.$$

No need to expand any polynomials!

**Example:** Let's do a harder example and calculate

$$ \lim_{n \rightarrow \infty} \frac{n^2}{n!}.$$

Maybe you learned in calculus that the factorial grows faster than a polynomial, and so it dominates and you conclude that this is zero, but let's explore why this is true. Notice that for $$n \geq 4$$ we can write

$$ \frac{n^2}{n!} = \frac{n}{n} \cdot \frac{n}{(n-1)} \cdot \frac{1}{(n-2)!} = \frac{n}{n-1} \cdot \frac{1}{(n-2)!}.$$

The $$n \geq 4$$ is important for just making sure the factorial is defined. Now as we take the limits, it's clear that the term on the far right goes to zero, and we can use our previous work to see the limit on the left is one:

$$ \lim_{n \rightarrow \infty} \frac{n}{n-1} = 1 \text{ and } \lim_{n \rightarrow \infty} \frac{1}{(n-2)!} = 0.$$

All together, the limit exists and is equal to $$1 \cdot 0 = 0,$$ so $$n!$$ dominates $$n^2$$.

**Remark:** The above procedure works for all powers of $$n$$, and so we can conclude that $$n!$$ dominates any polynomial.

**Example:** Let's do an even harder example and calculate

$$ \lim_{n \rightarrow \infty} \frac{n!}{n^n}.$$

Let's try copying the logic from before:

$$ \frac{n!}{n^n} = \frac{n}{n} \cdot \frac{n-1}{n} \cdot \frac{n-2}{n} \cdots \cdot \frac{1}{n}.$$

Notice that for any $$k \geq 0$$ we have

$$ \frac{n-k}{n} < 1,$$

since the top is smaller than the bottom. Multiplying by a number smaller than one shrinks things, so we can use this to conclude that

$$0 < \frac{n!}{n^n} \leq \frac{1}{n}.$$

We might seem out of luck, but let's come back to this in a moment...


## Squeeze Theorem

Recall the famous squeeze/sandwich theorem.

**Theorem:** Let $$(a_n), (b_n), (c_n)$$ be sequences, and let $$N \geq 0$$ be fixed. Suppose we have

$$a_n \leq b_n \leq c_n \text{ for } n \geq N.$$

If

$$ \lim_{n \rightarrow \infty} a_n = L = \lim_{n \rightarrow \infty}c_n,$$

then

$$ \lim_{n \rightarrow \infty} b_n = L.$$

**Example:** Recall that we have

$$0 < \frac{n!}{n^n} \leq \frac{1}{n}.$$

Let $$a_n = 0$$ for all $$n \geq 0$$, $$b_n = n!/n^n$$ for all $$n \geq 0$$, and $$c_n = n^{-1}$$ for all $$n \geq 0$$. Then we have shown

$$a_n \leq b_n \leq c_n \text{ for all } n \geq 0.$$

We know that $$\lim_{n \rightarrow \infty} a_n = 0 = \lim_{n \rightarrow \infty} c_n,$$ so we can use the squeeze theorem to conclude that

$$\lim_{n \rightarrow \infty} \frac{n!}{n^n} = 0.$$

We conclude that $$n^n$$ dominates factorials.

**Example:** Let $$a_n = D \cdot C^n$$ with $$\mid C \mid < 1$$ and $$C < 0$$. For convenience, let's also let $$A = \mid C \mid.$$ Without the squeeze theorem, we are stuck: how do I take the limit

$$ \lim_{n \rightarrow \infty} a_n?$$

With the squeeze theorem though, we have

$$ -D A^n \leq a_n \leq D A^n.$$

Since $$0 < A < 1,$$ we can write

$$A^n = \frac{1}{B^n}, \text{ where } B > 1.$$

It's clear that this goes to zero as $$n \rightarrow \infty$$, and multiplying by $$\pm D$$ doesn't change the answer. By the squeeze theorem, we have

$$ \lim_{n \rightarrow \infty} a_n = 0.$$


## Monotone Convergence Theorem

Given a sequence $$(a_n)$$, we say it is
- **strictly increasing** if $$a_{n+1} > a_n,$$
- **increasing** if $$a_{n+1} \geq a_n,$$
- **strictly decreasing** if $$a_{n+1} < a_n,$$
- **decreasing** if $$a_{n+1} \leq a_n,$$
- **bounded from above** if there is a constant $$M$$ so that $$a_n \leq M$$ for all $$n \geq 0,$$ and
- **bounded from below** if there is a constant $$M$$ so that $$M \leq a_n$$ for all $$n \geq 0$$.

A sequence is **monotonic** if it is strictly increasing, increasing, strictly decreasing, or decreasing. It is **eventually monotonic** if there is an $$N \geq 0$$ so that $$(a_n)_{n \geq N}$$ is monotonic.

**Example:** If a sequence $$(a_n)$$ is increasing, then $$a_0 \leq a_1 \leq a_2 \leq \cdots \leq a_n \leq \cdots.$$ It's clear that it is bounded from below, since $$a_0 \leq a_n$$ for all $$n$$.

With this, we can state the famous [monotone convergence theorem](https://en.wikipedia.org/wiki/Monotone_convergence_theorem).

**Theorem:** If a sequence $$(a_n)$$ is monotonic and bounded, then $$\lim_{n \rightarrow \infty} a_n$$ exists.

**Remark:** Suppose a sequence $$(a_n)$$ is monotonic and not bounded. Since the only option for the sequence is for it to converge (and hence the limit exists) or diverge, we see that it must diverge.

**Example:** Consider the sequence

$$a_n = (\sqrt{2} - 2^{1/(2n+1)}) \cdot a_{n-1} \text{ with } a_1 = \sqrt{2} - 2^{1/3}.$$

Let's determine whether it converges. The first question to ask ourselves is whether or not this sequence is monotone. Since it's given recursively, it's not too hard to see that it is increasing as long as $$\sqrt{2} - 2^{1/(2n+1)} > 1$$ and decreasing if $$\sqrt{2} - 2^{1/(2n+1)} < 1$$ (this is determining whether or not we are multiplying by a number bigger than one or smaller than one). Which of these is reasonable? Using a calculator, we know $$\sqrt{2} \approx  1.414,$$ and its not hard to see that for large $$n$$ we have $$2^{1/(2n+1)}$$ is close to $$1$$. So it seems reasonable that it should be decreasing. To double check ourselves, notice we need to check

$$\sqrt{2} - 2^{1/(2n+1)} < 1 \leftrightarrow \sqrt{2} - 1 < 0.5 < 2^{1/(2n+1)}.$$

Raising everything by the $$2n+1$$ power, we have

$$(0.5)^{2n+1} < 1 < 2,$$

and so the inequality is true for all $$n \geq 1$$. In fact, we see that $$\sqrt{2} - 2^{1/(2n+1)} < 1$$ for all $$n \geq 1$$, so the sequence is monotone decreasing. Now let's see if the sequence is bounded from below. It's clear that $$a_1 > 0$$ (plug it into a calculator), and so we're done if we can show that $$a_n > 0$$ for all $$n \geq 1$$. We'll be done if we can show that

$$ \sqrt{2} - 2^{1/(2n+1)} > 0.$$

We can do the same trick to rewrite our inequality as

$$\sqrt{2} > 2^{1/(2n+1)} \leftrightarrow  2^{(2n+1)/2} > 2 \leftrightarrow 2^{(2n+1)/2 - 1} = 2^{(2n-1)/2} > 1.$$

Now, $$n \geq 1$$, so $$2n-1 \geq 1.$$ So we have a lower bound

$$ 2^{(2n-1)/2} \geq 2^{1/2},$$

and we know from earlier that $$\sqrt{2} > 1,$$ so the inequality is true. Our sequence is monotone and bounded from below, so the theorem says it converges. Try plotting it to see what it converges to!
