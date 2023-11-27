---
layout: post
title: Recitation Twenty Three
tag: [MA1172]
---

In this recitation, we covered limits and continuity of functions of several variables. I was out of town for this recitation, and [Linus Ge](https://math.osu.edu/people/ge.409) covered for me.

# Open and Closed Sets

It'll be important to recall how we measure the distance between points in $$\mathbb{R}^n$$. Given $$x, y \in \mathbb{R}^n$$, which we can write as

$$x = (x_1, \ldots, x_n) \text{ and } y = (y_1, \ldots, y_n),$$

the **distance** between $$x$$ and $$y$$ is defined to be

$$d(x,y) := \sqrt{(x_1 - y_1)^2 + \cdots + (x_n - y_n)^2}.$$

When doing calculus, a lot of our work was focused on open intervals. This was fine, since we were working on $$\mathbb{R}$$, but in higher dimensions we are interested in more "general" versions of open intervals. The goal of this section is to explore what that might mean.

Recall that a **set** is a collection of objects. For us, this generally meant numbers, but now it can mean a collection of tuples (since we are exploring higher dimensions). One example of a set is

$$ A := \{(x,y) \in \mathbb{R}^2 \ : \ x^2 + y^2 = 1\}.$$

This is the collection of all pairs $$(x,y)$$ of real numbers which satisfy the condition that $$x^2 + y^2 = 1$$. As we know from earlier trigonometry, these numbers also take the form of $$(\cos(\theta), \sin(\theta))$$ for $$\theta \in \mathbb{R}$$. There may be a lot of equivalent ways of writing sets, so it is important to know how to relate one set to another.

Given a set $$A$$ (of anything), we say that $$a$$ is in the set $$A$$ if it is a distinct element, and we write $$a \in A$$. For example, $$(1,0) \in A$$ in the above example, while $$(2,0) \notin A$$ since $$2^2 + 0^2 \neq 1$$.

Given two sets $$A$$ and $$B$$, we say that $$A$$ is a **subset** of $$B$$ if for every $$a \in A$$, we have $$a \in B$$. For example, let

$$B = \{(x,y) \ : \ x^2 + y^2 \leq 1\}.$$

If $$(x,y) \in A$$ for $$A$$ given above, then $$x^2 + y^2 = 1$$, so in particular $$x^2 + y^2 \leq 1$$ and we have $$(x,y) \in B$$. So $$A \subseteq B$$.

This leads us to a special kind of subset that we are interested in (the generalization of an open interval). Given $$x \in \mathbb{R}^n$$, so $$x = (x_1, \ldots, x_n)$$, and $$R > 0$$, we define the **open ball of radius $$R$$ centered at $$x$$** to be the set

$$B_r(x) := \{y \in \mathbb{R}^n \ : \ (x_1 - y_1)^2 + \cdots + (x_n - y_n)^2 < R^2\}.$$

In other words, this is the collection of all points $$y \in \mathbb{R}^n$$ whose distance to $$x$$ is less than $$R$$ (strictly).

**Remark:** Notice that if $$n = 1$$, then the open ball of radius $$R$$ is just an open interval.

Given a subset $$S \subseteq \mathbb{R}^n$$, we say that $$x \in \mathbb{R}^n$$ is an **interior point** if there is an $$R > 0$$ so that $$B_R(x) \subseteq S$$. In other words, $$x$$ is an interior point if we can find an open ball containing $$x$$ which lives entirely inside of $$S$$. If for every $$R>0$$ we have $$B_R(x)$$ is not contained in $$S$$, then we say that $$x$$ is a **boundary point**.

**Observation:** Notice that if $$x \in \mathbb{R}^n$$ is an interior point for $$S$$, then necessarily $$x \in S$$. However, if $$x$$ is a boundary point for $$S$$, it does not have to live in $$S$$. For example, in $$\mathbb{R}^2$$ if we look at

$$ S = \{(x,y) \in \mathbb{R}^2 \ : \ x^2 + y^2 < 1\},$$

then $$(1,0)$$ is a boundary point for $$S$$ but $$(1,0) \notin S$$.

We denote the boundary of a set $$S$$ by $$\partial S$$.

We say that a set $$S$$ is **open** if every $$x \in S$$ is an interior point, and it is **closed** if $$\partial S \subseteq S$$ (or, in English, if $$S$$ contains all of its boundary points). In English, we generally think of closed and open as opposites, but in math things can be both open and closed. For example, $$\mathbb{R}$$ is open, since given $$x \in \mathbb{R}$$ and any $$ R > 0$$ we have $$B_R(x) \subseteq \mathbb{R}$$ by construction, and it is also closed (since there are no boundary points).

Finally, a set $$S \subseteq \mathbb{R}^n$$ is **bounded** if there is an $$R > 0$$ so that $$S \subseteq B_R(0)$$, where $$0 = (0, \ldots, 0)$$ for shorthand. A set which is not bounded is called **unbounded**. For example, the set

$$ \{(x,y) \in \mathbb{R}^2 \ : \ x^2 + y^2 < 1 \}$$

is bounded, since it is the open ball of radius $$1$$. On the other hand, the set

$$ \{(x,y) \in \mathbb{R}^2 \ : \ \mid x + y \mid < 1 \}$$

is unbounded, since given any $$y$$ we can take $$x = -y + \frac{1}{2}$$ and it'll satisfy the condition, and

$$ x^2 + y^2 = 2y^2 - y + \frac{1}{4}$$

can be as big as we want by letting $$y \rightarrow \infty$$ (so it cannot be contained in any open ball).

# Limits and Continuity

Limits in higher dimensions is close to what we would expect from the one-dimensional case, but there's a little bit of a trick to it. We'll focus on the two-dimensional case, but it works the same for higher dimensions. We write

$$ \lim_{(x,y) \rightarrow (a,b)} F(x,y) = L$$

if as $$(x,y)$$ gets closer to $$(a,b)$$ we have that $$F(x,y)$$ gets closer to $$L$$. More precisely, if for every $$\epsilon > 0$$ there is a $$\delta$$ so that $$d((x,y), (a,b)) < \delta$$ implies $$\mid F(x,y) - L \mid < \epsilon$$, then we say that $$\lim_{(x,y) \rightarrow (a,b)} F(x,y) = L$$. Don't be deceived, though. In one dimension, there were only two ways to approach a given point, either from the left or right. Now we have infinitely many different ways of approaching a given point, and as we take any of these different approaches we must have that the limit is the same. For example, consider the function

$$F(x,y) := \frac{3xy}{x^2 + y^2}.$$

We wish to calculate $$\lim_{(x,y) \rightarrow (0,0)} F(x,y)$$. If we consider the path $$x = y$$, then we have

$$ \lim_{x \rightarrow 0} F(x,x) = \lim_{x \rightarrow 0} \frac{3x^2}{x^2 + x^2} = \frac{3}{2}.$$

One might say that the limit is $$3/2$$ based off of this. However, we can also just take the path $$y = 0$$, in which case

$$ \lim_{x \rightarrow 0} F(x,0) = \lim_{x \rightarrow 0} \frac{0}{x^2} = 0.$$

These are both valid paths to the point $$(0,0)$$, and they give different answers. As a result, the limit must not exist.

While it seems hopelessly difficult to prove that a limit actually does exist, it's generally not so bad if the variables aren't mingling together. All of the usual limit laws apply for the multivariable case, so let's use this to our advantage. For example, consider $$F(x,y) = x^2 + y^2$$. Notice that

$$ \lim_{(x,y) \rightarrow (0,0)} F(x,y) = \lim_{(x,y) \rightarrow (0,0)} (x^2 + y^2) = (\lim_{(x,y) \rightarrow (0,0)} x^2) + (\lim_{(x,y) \rightarrow (0,0)} y^2).$$

Now there are no $$y$$'s in the first expression, so we can just ignore that in our limit calculation:

$$\lim_{(x,y) \rightarrow (0,0)} x^2 = \lim_{x \rightarrow 0} x^2 = 0.$$

The same applies for the other expression (but replace $$y$$ with $$x$$), and we get

$$ \lim_{(x,y) \rightarrow (0,0)} F(x,y) = 0.$$

Continuity applies the same as usual, and so I'll skip over this. The hard part of this section is checking whether or not a limit exists, and so I recommend practicing this. It will test your algebra skills!
