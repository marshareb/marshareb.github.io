---
layout: post
title: Unique Ergodicity and Square Roots (Weekly Update 10)
tag: weekly-update
categories: ["Weekly Update"]
---

In this post, I describe a nice example of a homeomorphism of a compact space which is not minimal but is
uniquely ergodic, as well as a condition for a complex matrix to have a square root.

# Personal Life

I'm moving tomorrow, so a lot of things are thrown off balance. Most of my free time (and a little of my work time) is devoted to getting ready for the move. I'm not excited to move during a pandemic, but we managed to get a week overlap between apartments, so I think it shouldn't be as bad as I originally expected.

This post also marks the last weekly update for the summer semester. Next week I start TA training, which will become the focus of most of my time. I may continue reading a little dynamics and functional analysis when I'm bored, but I doubt it will be at the same level as the past two and a half months.

# Dynamics

One of the main problems for this week was trying to find a homeomorphism on a compact manifold which is uniquely ergodic but is not minimal. This sort of question came up when I was first learning the definitions, as I wanted to know the relation between these topological dynamical properties and these ergodic properties. In some settings, I think one should expect them to have a relation, but in general they do not. There is a nice MathOverflow post (check [here](https://mathoverflow.net/questions/114326/connection-between-properties-of-dynamical-and-ergodic-systems)) which actually outlines a bunch of examples one can use. However, I found a [paper](http://homepages.math.uic.edu/~furman/preprints/intro-ET.pdf) by [Alex Furman](http://homepages.math.uic.edu/~furman/) which gives a neat example as well (this is **Exercise 1.16**). We outline it here.

Consider the one point compactification of $$\mathbb{Z}$$. That is, consider $$\hat{\mathbb{Z}} = \mathbb{Z} \cup \{\infty\}$$, where the open sets are going to be the usual open sets on $$\mathbb{Z}$$ (this is the discrete topology, so take collections of points) as well as the open sets given by the [one point compactification](https://en.wikipedia.org/wiki/Alexandroff_extension#The_one-point_compactification) (so open sets of the form $$V = C^c \cup \{\infty\}$$, where $$C$$ a closed set). This makes it into a compact space. Now take the shift operator $$T : \hat{\mathbb{Z}} \rightarrow \hat{\mathbb{Z}}$$ defined by $$T(n) = n+1$$ (note $$T(\infty) = \infty$$). Note that a closed set is going to be some finite collection of points, $$C =\{a_1, \ldots, a_n\}$$, so $$C^c$$ is going to be all integers except those union infinity. Shifting is continuous on the usual topology on the integers, so it suffices to show that the preimage of $$V = C^c \cup \{\infty\}$$ is also open, but this follows since this is all but finitely many points as well as the point at infinity. So $$T$$ is a continuous map on $$\hat{\mathbb{Z}}$$. It's inverse is $$T^{-1}(n) = n-1$$, which we note is continuous as well by the same reasoning above. Thus this is a homeomorphism of a compact space.

Note that this is not minimal. We see $$\mathcal{O}_T(\infty) = \{\infty\}$$, since adding or subtracting one from infinity still gives us infinity. It follows that this orbit is not dense; take for example the point $$0$$. One open neighborhood if $$\{0\}$$ (by the discrete topology), and we see that $$\{\infty\} \cap \{0\} = \varnothing$$, so $$0 \notin \overline{\{\infty\}}$$. It turns out this *is* topologically transitive; examine

$$ \mathcal{O}_T(0) = \{T^n(0) : n \in \mathbb{Z}\} = \mathbb{Z}.$$

Notice for every open neighborhood of $$\{\infty\}$$, we have a collection of all but finitely many points and $$\infty$$ which intersects $$\mathbb{Z}$$ non-trivially. So $$\overline{\mathbb{Z}} = \hat{\mathbb{Z}}$$.

We now need to show that $$T$$ is uniquely ergodic. If $$X$$ is a compact space, recall that a continuous function $$T : X \rightarrow X$$ is *uniquely ergodic* if there is a *unique* invariant Borel probability measure for $$T$$. Equivalently, the function $$T$$ is uniquely ergodic if we have that for every $$f \in C(X)$$,

$$ \frac{1}{n}\sum_{j=0}^{n-1} f(T^j(x)) \xrightarrow[]{u} D(f), $$

where $$D(f)$$ is some constant. Note the arrow with $$u$$ over it means uniform convergence, and note that $$C(X) = \{f : X \rightarrow \mathbb{R} : f \text{ is continuous.}\}$$. As long as this is constant, we can actually weaken the uniform convergence to pointwise convergence (the argument is not hard to show this equivalence, but [here](https://mathoverflow.net/questions/152132/uniform-convergence-of-birkhoff-averages-and-unique-ergodicity) is a reference).

We'd like to utilize this idea to prove the unique ergodicity of the shift function. Blindly, let's take $$f \in C(\hat{\mathbb{Z}})$$ (note that this means $$f$$ is continuous, bounded, and $$f(\infty)$$ is a well-defined value). We see that
$$ \frac{1}{n} \sum_{j=0}^{n-1} f(T^j(x)) = \frac{1}{n}\sum_{j=0}^{n-1} f(x+j).$$
This sort of looks like a Riemann sum, except the issue is that the values are getting more spread out over time. As we get larger and larger, we have values "closer and closer" to infinity, so we might expect this to converge to $$f(\infty)$$. Let's test to see if that happens.

Keep in mind that $$\lim_{n \rightarrow \infty} f(n) = f(\infty)$$, so for all $$\epsilon > 0$$ there is a sufficiently large $$N$$ so that for all $$m \geq N$$ we have $$|f(m) - f(\infty)| < \epsilon$$. Take $$\epsilon > 0$$ arbitrary, and let $$N$$ be large enough so for all $$m \geq N$$, $$|f(x+m) - f(\infty)| < \epsilon$$. Writing things out, we have
for $$n$$ (say much) larger than $$N$$
$$\begin{split} \left| \frac{1}{n} \sum_{j=0}^{n-1} f(T^j(x)) - f(\infty)\right| = \left| \frac{1}{n} \sum_{j=0}^{N-1} f(T^j(x)) + \frac{1}{n}\sum_{j=N}^{n-1}f(T^j(x)) - f(\infty)\right| \\
= \left|\frac{1}{n} \sum_{j=0}^{N-1} f(T^j(x)) + \frac{1}{n}\sum_{j=N}^{n-1}f(T^j(x)) - \frac{1}{n}[ (N)f(\infty) + (n-1-N) f(\infty)]\right| \\
= \left|\frac{1}{n} \sum_{j=0}^{N-1} f(T^j(x)) + \frac{1}{n}\sum_{j=N}^{n-1}[f(x+j) - f(\infty)] - \frac{N}{n} f(\infty) \right|. \end{split}$$

Now let's use the fact that $$f$$ bounded, so $$|f| \leq M < \infty$$. Invoking this and the triangle inequality, we get an upper bound of

$$ \frac{MN}{n} + \frac{1}{n} \sum_{j=N}^{n-1} |f(x+j) - f(\infty)| + \frac{N}{n}f(\infty).$$

Since $$N$$ is appropriately chosen, notice that we have a strict upper bound of

$$ |A_n(f)(x) - f(\infty)| < \frac{MN}{n} + \frac{(n-1-N) \epsilon}{n} + \frac{N}{n} f(\infty).$$

Take $$n \rightarrow \infty$$ on both sides to get

$$ |A(f)(x) - f(\infty)| < \epsilon,$$

where

$$ A(f)(x) = \lim_{n \rightarrow \infty} A_n(f)(x).$$

We chose $$\epsilon > 0$$ arbitrary, so this implies that $$A(f)(x) = f(\infty)$$. The choice of $$x$$ doesn't matter here, so pointwise we have pointwise convergence to $$f(\infty)$$. By the above claim, this implies unique ergodicity, and moreover that the unique invariant Borel probability measure is given by the delta distribution.

Convergence was established with [Thomas O'Hare](https://math.osu.edu/people/ohare.26).

# Functional Analysis

Another thing Thomas and I worked on this week was the following question: "When does $$A \in M_n(\mathbb{C})$$ have a square root?" This was proposed to us by [David Penneys](https://people.math.osu.edu/penneys.2/) and apparently was proposed to others in [this](https://sbseminar.wordpress.com/2008/11/26/two-fun-problems/) blog post. They give the gist of it, but hopefully I outline some more details here.

Using [Jordan normal form](https://en.wikipedia.org/wiki/Jordan_normal_form), we can take our matrix $$A$$ and rewrite it using some invertible matrix $$P$$ as $$PAP^{-1} = \text{diag}(J_1, \ldots, J_k)$$, where the $$J_i$$ are Jordan blocks corresponding to different $$\lambda \in \sigma(A)$$. If this $$PAP^{-1}$$ has a square root, say $$B$$, then we have

$$ B^2 = PAP^{-1} \Leftrightarrow P^{-1}B^2 P = A.$$

Now notice

$$ (P^{-1} B P)^2 = (P^{-1} B P)(P^{-1} B P) = P^{-1} B^2 P = A.$$

So if we can find a square root up to conjugation, we can find a square root. Without loss of generality, assume that $$A$$ was originally in Jordan normal form. Now, let's conjugate to rearrange our Jordan blocks so that the first $$k_1$$ of them are Jordan blocks corresponding to non-zero eigenvalues, and the last $$k_2$$ of them are what we will call nilpotent Jordan blocks, meaning Jordan blocks with $$0$$ eigenvalue. Recall an element $$A$$ is nilpotent if there is some $$N$$ with $$A^N = 0$$. We can then decompose $$PAP^{-1}$$ into a direct sum, say $$PAP^{-1} = J \oplus N$$, where $$J = \text{diag}(J_1, \ldots, J_{k_1})$$, $$N = \text{diag}\{J_{k_1 + 1}, \ldots, J_{k_1 + k_2}\}$$. Let's assume without loss of generality again that $$A$$ was given to us in this form.

The first step is to note that every invertible matrix has a square root, so this $$J$$ component has a square root. First, note that a diagonalizable matrix has a square root. This follows since if $$J = \text{diag}(\lambda_1, \ldots, \lambda_k)$$, then $$J^2 = \text{diag}(\lambda_1^2, \ldots, \lambda_k^2)$$, and since we have a square root on $$\mathbb{C}$$ we get the result. Next, we note that the Jordan blocks in this invertible matrix are non-zero on the diagonal, so

$$ J_j =
\begin{pmatrix}
\lambda & 1 & 0 & \cdots & 0 \\
0 & \lambda & 1 & \cdots & 0 \\
\vdots & \vdots & \ddots & \ddots &  \vdots \\
0 & 0 & \cdots & \lambda & 1 \\
0 & 0 & \cdots & \cdots & \lambda
\end{pmatrix},$$

$$\lambda \in \sigma(J)$$, $$\lambda \neq 0$$. We can rewrite this as

$$ J_j = \lambda (I + N),$$

where

$$ N =
\begin{pmatrix}
0 & 1/\lambda & 0 & \cdots & 0 \\
0 & 0 & 1/\lambda & \cdots & 0 \\
\vdots & \vdots & \ddots & \ddots &  \vdots \\
0 & 0 & \cdots & 0 & 1/\lambda \\
0 & 0 & \cdots & \cdots & 0
\end{pmatrix}.$$

We note that $$N$$ is nilpotent (powers of $$N$$ move shift the $$1/\lambda$$ values to the right). Recall that the Taylor series of $$\sqrt{1+x}$$ around $$0$$ is

$$ \sqrt{1+x} = 1 + \sum_{k=1}^{\infty} \frac{\prod_{n=1}^{k-1}(1/2 - (n-1))}{k!} x^k.$$

We can use holomorphic functional calculus now. Let $$f(x) = \sqrt{1+x}$$. This is a holomorphic function, and so taking $$U$$ a neighborhood around $$0$$ we have

$$ \widetilde{f}(N) = \sqrt{I+N} = I + \sum_{k=1}^\infty \frac{\prod_{n=1}^{k-1}(1/2 - (n-1))}{k!} N^k. $$

Since $$N$$ is nilpotent, we have that there is some $$n$$ with $$N^n = 0$$. So the series can be rewritten as

$$ \sqrt{I+N} = I + \sum_{k=1}^{n-1} \frac{\prod_{n=1}^{k-1}(1/2 - (n-1))}{k!} N^k.  $$

This gives us a square root of $$I + N$$. Thus, we get a square root of $$J_j$$ for each $$j$$. Notice

$$ \text{diag}(\sqrt{J_1}, \ldots, \sqrt{J_{k_1}})^2 = J,$$

so $$J$$ has a square root.

Going back to $$A = J \oplus N$$, we note that if $$N$$ does *not* have a square root, then $$A$$ does not have a square root. If $$A$$ does have a square root, say $$B$$, then we can (after conjugating) write $$B = J' \oplus N'$$, $$J'$$ invertible and $$N'$$ invertible. Squaring, we get $$B^2 = J'^2 \oplus N'^2 = A$$. The square of an invertible matrix is invertible, and the square of a nilpotent matrix is nilpotent, so we must have that the nilpotent and invertible portions agree (after conjugating, which will also not affect invertibility/nilpotency). Thus if $$A$$ has a square root, then $$N$$ has a square root, and taking the contrapositive implies if $$N$$ does not have a square root, then $$A$$ does not have a square root.

So we've now boiled the question down to the following: "When does a nilpotent $$A \in M_n(\mathbb{C})$$ have a square root?" We first show that, individually, the nilpotent Jordan blocks of dimension $$\geq 2$$ do *not* have square roots. First, note the easy claim that if $$N$$ is a $$n \times n$$ nilpotent matrix, we have $$A^n = 0$$. This is a direct consequence of [Cayley-Hamilton](https://en.wikipedia.org/wiki/Cayley%E2%80%93Hamilton_theorem) and examining the [characteristic polynomial](https://en.wikipedia.org/wiki/Characteristic_polynomial). If $$m$$ is the characteristic polynomial and $$N^k = 0$$ for some $$k$$, then $$m \mid x^k$$. We know $$j = \deg(m) \leq n$$, so Cayley-Hamilton says $$N^j = 0$$ for some $$j \leq n$$, implying $$N^n = 0$$ as well.

Now, suppose $$N$$ did have a square root, say $$B^2 = N$$. Suppose as well $$N$$ is a $$n \times n$$ nilpotent Jordan block, $$n \geq 2$$. We know (from observation) that $$N^{n-1} \neq 0$$, $$N^n = 0$$. We see as well $$B^{2n} = 0$$, $$B^n = 0$$. Notice that $$B^{2n-2} = N^{n-1}$$. Notice as well that, since $$n \geq 2$$, we have $$n-2 \geq 0$$ or $$2n - 2 \geq n$$. Since $$B^n = 0$$, this forces $$B^{2n-2} = 0$$, contradicting the fact that we had $$N^{n-1} \neq 0$$. So individually, nilpotent Jordan blocks do *not* have square roots.

Take a nilpotent Jordan block of size $$2n$$, call it $$N$$. Recall that we have $$N^2$$ shifts all of the $$1$$ values to the right. We now want to take the Jordan normal form of $$N^2$$. We know the eigenvalues are $$0$$, so it suffices to figure out how big the nilpotent Jordan blocks will be. To calculate this, notice that $$N e_j = e_{j-2}$$, where $$1 \leq j \leq n$$. So we get two Jordan blocks, corresponding to $$\{e_1, e_3, \ldots, e_{2n-1}\}$$, $$\{e_2, e_4, \ldots, e_{2n}\}$$. That is, we have two Jordan blocks of size $$n$$. If our nilpotent Jordan block was of size $$2n+1$$, we get that the Jordan normal form if its square gives us two nilpotent Jordan blocks, one of size $$n$$ and one of size $$n+1$$.

This gives us essentially all of the information we need to start figuring out the square root. Now $$N$$ goes back to representing a nilpotent operator, so we write

$$ N = \text{diag}(J_1, \ldots, J_k).$$

Recall conjugating doesn't affect anything, so we can rearrange these Jordan blocks however we wish. Write them in descending order with respect to their size. If $$k$$ is odd, throw on a size $$0$$ nilpotent Jordan block to make it even (this doesn't change the operator at all). So without loss of generality, we get that $$k$$ is even. Let $$(a_j)_{1 \leq j \leq k}$$ be the sizes of the $$j$$th nilpotent Jordan block. We examine the sequence $$(a_1 - a_2, a_3 - a_4, \ldots, a_{k-1} - a_k)$$. The claim is that the maximum in this sequence is $$\leq 1$$  if and only if $$N$$ has a square root. (If this strategy is unclear, check out the solution by Oscar Cunningham found [here](https://math.stackexchange.com/a/1849928/333294), specifically the last paragraph.)

Based on our discussion above, we know one direction pretty easy. If the maximum in this sequence is $$\leq 1$$, we can create appropriately sized nilpotent Jordan blocks which, when squared, will be (up to conjugation) the two paired up Jordan blocks. Since conjugation doesn't affect anything, this gives us a square root.

The other direction is a little trickier, but we have a few facts that we can use here. Suppose $$N$$ has a square root, call it $$B$$. Since $$N$$ is nilpotent, we know that $$B$$ is also nilpotent. Write $$B$$ in its Jordan normal form. Squaring this squares the respective blocks, and so when we take the Jordan normal form of the square of the Jordan normal form, we have a Jordan normal form that is similar to the Jordan normal form of $$N$$. Note that Jordan normal form is unique up to rearranging the blocks, so this tells us three facts: (1) the number of Jordan blocks in both are the same (2) the size of the Jordan blocks in both are the same (3) the spectrum for both are the same (but we already knew this). We now are going to use facts (1) and (2), and the fact that the square of a nilpotent Jordan block gives you two blocks of size roughly half. Since we're squaring each of these nilpotent Jordan blocks, we're going to get double the Jordan blocks, so in particular we have $$k/2$$ nilpotent Jordan blocks in $$B$$. Next, when we square them, we are going to get two matrices of size roughly half. That is, their difference in size can only be at most $$1$$. When we rearrange these matrices in increasing order, this implies that the above sequence has maximum at most $$1$$ (we have these "admissable" pairs which will go together).

This shows that if $$N$$ has a square root, then the max of $$(a_1 - a_2, \ldots, a_{k-1} - a_k)$$ is $$\leq 1$$, and we've shown that if the max is at most $$1$$ then we have a square root. This gives us our necessary and sufficient condition.

Two interesting questions which follow from this are the following:
- When does $$A \in M_n(\mathbb{R})$$ have a square root? I think this sort of method with maybe [rational canonical form](https://mathworld.wolfram.com/RationalCanonicalForm.html) might work. [This](https://arxiv.org/pdf/0805.0245.pdf) paper gives a solution.
- When does $$A \in M_n(\mathbb{C})$$ have a finitely many square roots? [This](https://yutsumura.com/noinfinitely-many-square-roots-of-2-by-2-matrices/) gives some motivation for this thought. [This](https://math.stackexchange.com/questions/562566/are-there-sometimes-only-finitely-many-square-roots-of-a-positive-matrix) gives a sketch of a solution.


Again, credit to [Scott Carnahan](http://www.math.tsukuba.ac.jp/~carnahan/) and [Ben Webster](https://uwaterloo.ca/scholar/b2webste/home) for their discussions on the blog posts found [here](https://sbseminar.wordpress.com/2008/11/26/two-fun-problems/) and [here](https://sbseminar.wordpress.com/2008/12/02/square-roots-of-nilpotent-matrices/). [Lukas Scheiwiller](https://lsa.umich.edu/math/people/phd-students/Lukas_Scheiwiller.html) and [Andrew Krenz](http://www.math.wisc.edu/~krenz3/) also had an interesting approach to the invertible part using [polar decomposition of a complex matrix](https://en.wikipedia.org/wiki/Polar_decomposition).
