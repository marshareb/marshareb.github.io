---
layout: post
title: A Cute Group Theory Problem
tag: algebra
categories: ["Algebra"]
---

In this post, I outline a solution for a problem someone sent me.

# The problem and solution

This is the first time that a complete stranger messaged me a problem for whatever reason. I'm not sure how they got a hold of my information, but I decided to try working out the problem and I thought it was fun enough to include it as a blog post. Maybe someone else will get a kick out of it. I think my use of abelian is implicit, but I didn't want to do all of the work for you (so exercise: figure out why we had to use our group is abelian).

Throughout, let $$G$$ be a finite group. For $$g \in G$$, let $$\mid g \mid$$ be the order of $$g$$, meaning the smallest positive integer so that $$g^n = e$$. For any group $$H$$, let

$$ Z(H) = \{g \in H : gh = hg \text{ for all } h \in H\}.$$

This is called the center of the group. Finally, $$f : H \rightarrow H$$ is an automorphism if it is bijective and a homomorphism. With the language, we can write the problem.

**Problem:** If $$G$$ is a finite abelian group such that for all $$g \in G$$, the order of $$g$$ divides $$3$$, then we have
$$ Z(\text{Aut}(G)) \cong \mathbb{Z}/2\mathbb{Z}.$$

**Gist of solution:** We need to look at $$H = Z(\text{Aut}(G))$$. We can write this as

$$ H = \{f \in \text{Aut}(G) : \text{ for all } g \in \text{Aut}(G), f = g^{-1} \circ f \circ g\}.$$

We have that automorphisms are totally determined by one quality - namely, if $$x \in G$$ has order three, then $$g(x)$$ must also have order $$3$$ for $$g$$ an automorphism. Let

$$ T =\{x_1, \ldots, x_n\} $$

be the collection of elements of order $$3$$ so that if $$g \in G$$, then $$g \in \langle x_j \rangle$$ for some $$1 \leq j \leq n$$ and $$x_i^2 \neq x_j$$ for any $$i,j$$ (the existence of such a set follows from the fact that the order of element divides $$3$$, so must be trivial or must be contained in a cyclic group of order $$3$$). Let's think about $$f \in H$$. For $$x_i \in T$$, we have either $$f(x_i) = x_i^2$$ or $$f(x_i) = x_j$$ or $$f(x_i) = x_j^2$$ for some $$1 \leq j \leq i$$. Think about the case where $$f(x_i) = x_i^2$$. We can construct $$g \in \text{Aut}(G)$$ so that $$g(x_j) = x_i^2$$. Then $$f \in H$$ says that

$$ f(x_j) = g^{-1} \circ f \circ g(x_j) = g^{-1} \circ f(x_i^2) = (g^{-1} \circ f (x_i))^2 $$

$$ =g^{-1}(x_i^2)^2 = x_j^2.$$

Now we can do this for all $$x_j \in T$$, and once we know that $$f(x_j) = x_j^2$$, we know that $$f(x_j^2) = x_j$$, since

$$ f(x_j^2) = f(x_j)^2 = (x_j^2)^2 = x_j^4 = x_j.$$

So $$f$$ is completely determined by this fact. Moreover, we know that $$f \circ f = \text{Id}$$, so $$f$$ has order $$2$$.

Assume that in our construction of $$T$$ we have $$n \geq 3$$. Suppose that $$f \in H$$ is such that $$f(x_i) = x_j$$ for $$x_i \neq x_j \in T$$. The goal is to show that this is not possible. By the earlier argument, we know that $$f(x_k) \neq x_k^2$$ for any $$x_k \in T$$. Notice that

$$ f = g^{-1} \circ f \circ g \text{ for all } g \in \text{Aut}(G).$$

We see that
$$x_j = f(x_i) = g^{-1}(f(g(x_i)))$$. Set $$g(x_i) = x_i$$ and $$g(x_k) = x_j$$ for some $$x_k \neq x_j \in T$$. Then

$$ x_j = f(x_i) = g^{-1}(f(g(x_i))) = g^{-1}(f(x_i)) = g^{-1}(x_j) = x_k.$$

We see we have a contradiction, so this is not possible. The same kind of argument shows that $$f(x_i) \neq x_j^2$$ for any $$x_j \in T$$. Since our only possibilities for $$f(x_i)$$ is either $$f(x_i) = x_i$$ (so the identity map) $$f(x_i) = x_i^2$$ (which determines $$f$$ as before), $$f(x_i) = x_j$$ for some $$x_j \in T$$ (which is impossible), and $$f(x_i) = x_j^2$$ for some $$x_j \in T$$ (which is impossible), we have that $$H$$ is only two elements.

If $$n = 1$$, then $$G = \langle x_1 \rangle$$, and we know from the first paragraph that $$H \cong \mathbb{Z}_2$$. Let's show that $$n = 2$$ is impossible. If $$n = 2$$, we have that for all $$g \in G$$, $$g \in \langle x_1 \rangle$$ or $$g \in \langle x_2 \rangle$$, with $$x_1 \neq x_2$$, and this completely determines the group. Thus $$G = \{e, x_1, x_1^2, x_2, x_2^2\}.$$ We assumed that $$G$$ was abelian, so we have $$x_1 x_2 = x_2 x_1$$. Moreover, $$x_1x_2 \in \langle x_1 \rangle$$ or $$x_1x_2 \in \langle x_2 \rangle$$. If $$x_1x_2 \in \langle x_1\rangle$$, then $$x_1x_2 = e,$$ $$x_1x_2 = x_1,$$ or $$x_1x_2 = x_1^2$$. If $$x_1x_2 = x_1$$, then this implies $$x_2 = e$$ which is a contradiction. If $$x_1x_2 = x_1^2$$, then multiplying by $$x_1^2$$ on the left of both sides gives $$x_2 = x_1$$, which is a contradiction. If $$x_1x_2 = e$$, then multiplying by $$x_1^2$$ on both sides gives $$x_2 = x_1^2$$, and we assumed $$x_2 \notin \langle x_1 \rangle$$, so this is a contradiction. Thus $$x_1x_2 \notin \langle x_1\rangle.$$ The same argument shows us that $$x_1x_2 \notin \langle x_2 \rangle.$$ This contradicts the fact that $$G$$ is a group, so constructing such a group is impossible. Thus if we construct a $$T$$ as above, we must have $$n = 1$$ or $$n \geq 3$$, and the argument follows.
