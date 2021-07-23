---
layout: post
title: Linearly Independent Vector Fields on the n-Sphere.
tag: geometry
categories: ["Geometry"]
---

In this post, I outline some results on linearly independent vector fields on the $$n$$-sphere.

# Vector Fields

The inspiration for this post comes from Section 1.2 in Conlon's Differentiable Manifolds.

We define the $$n$$-sphere to be

$$S^n := \{ v \in \mathbb{R}^{n+1} : \|v\| = 1\},$$

where here the norm is the usual Euclidean one induced by the dot product. On it, we can define the tangent space in a variety of different ways. There's the intrinsic definition which involves studying curves on the sphere and looking at their derivatives or looking at the space of derivations, but we'll take the more geometry extrinsic definition here following Conlon. We define the tangent space to be

$$ TS^n := \{(v,w) \in \mathbb{R}^{n+1} \times \mathbb{R}^{n+1} : \|v\| = 1, w \cdot v = 0\}.$$

This comes with a natural projection $$ \pi : TS^n \rightarrow S^n$$ defined by $$\pi(v,w) = v.$$ This is also sometimes referred to as the **footprint map.** Viewing this both as topological spaces with respect to the subspace topology induced by $$\mathbb{R}^n$$, we claim that this gives us a continuous surjective map. This is not too hard to see -- let $$(v_n, w_n) \subseteq TS^n$$ be a sequence which converges to $$(v,w)$$, we have that the dot product is continuous and the norm is continuous, so $$\|v\| = 1$$ and $$w \cdot v = 0$$ so that $$(v,w) \in TS^n$$. Furthermore, $$\pi(v_n, w_n) = v_n \rightarrow v = \pi(v,w)$$, so the map is continuous.

We remark that $$TS^n$$ is a vector space when restricted to a point. That is, if we consider the space

$$ \pi^{-1}(v) = T_v S^n = \{(v,w) \in TS^n\},$$

then this is a vector space with vector space operations defined on the orthogonal vectors. So

$$r \cdot (v,w) = (v, rw),$$

$$(v,w) + (v,w') = (v, w + w').$$

This follows since we have a linear map $$v^* : \mathbb{R}^{n+1} \rightarrow \mathbb{R}^{n+1}$$ defined by $$v^*(w) = w \cdot v,$$ and so we can alternatively view the tangent space as

$$ T_v S^n = \{v\} \times \ker(v^*).$$

A **vector field** in this context is a map $$s : S^n \rightarrow TS^n$$ which satisfies the property that $$\pi \circ s = \text{Id}$$. Two vector fields $$s_0, s_1$$ are said to be **linearly independent** if for each $$v \in S^n$$ we have $$\{s_0(v), s_1(v)\} \subseteq T_v S^n$$ are linearly independent. One question to ask at this point is what is the maximum number of linearly independent vector fields for $$S^n$$? We can define a function $$r(n)$$ whose value is exactly the maximum number, and thus the question boils down to understanding $$r$$.

# Parallelizability

[Bott](https://en.wikipedia.org/wiki/Raoul_Bott) and [Milnor](https://en.wikipedia.org/wiki/John_Milnor) along with [Kervaire](https://en.wikipedia.org/wiki/Michel_Kervaire) were able to prove that $$r(n) = n$$ if and only if $$n = 0,1,3,$$ or $$7$$. If $$r(n) = n$$ we call $$S^n$$ **parallelizable**, so the only time the sphere is parallelizable is if we have the above conditions. It turns out the question of being parallelizable is related to another question, namely whether or not there exists a bilinear multiplication on $$\mathbb{R}^n$$ without zero divisors. Let's check the connection now by establishing that if $$R^{n+1}$$ admits a multiplication without zero divisors then $$S^n$$ is parallelizable.

The case $$n=1$$ is illuminative (the case $$n=0$$ is trivial) so we start there. Let $$\mu : \mathbb{R}^2 \times \mathbb{R}^2 \rightarrow \mathbb{R}^2$$ be a bilinear multiplication without zero divisors. This implies there is an identity element, say $$e \in \mathbb{R}^2$$. Let $$v = \frac{e}{\|e\|}$$ and let $$\{e_1, e_2\}$$ be a basis for $$\ker(v^*)$$. We can define a map $$l : S^1 \rightarrow \mathbb{R}^2$$ by $$l(w) = \mu(w, e_1)$$. We can then set $$F : S^1 \rightarrow \mathbb{R}^2$$ to be

$$F(w) = l(w) - \langle l(w), w \rangle w.$$

Here I'm switching to the inner product notation for the dot product, so recall this means that

$$ \langle l(w), w \rangle = l(w) \cdot w.$$

Now the dot product is continuous, subtraction is continuous, and $$l$$ is continuous (since multiplication is continuous), so $$F$$ is a continuous map. Furthermore, we claim that $$F(w) \in \ker(w^*)$$. To see this, notice that we have

$$\langle w, F(w) \rangle = \langle w, l(w) \rangle - \langle l(w), w \rangle \langle w, w \rangle = 0.$$

Thus we've constructed a continuous map $$F : S^1 \rightarrow \mathbb{R}^2$$ with $$F(w) \in \ker(w^*)$$ for every $$w \in S^1$$. Now define the map $$\hat{F} : S^1 \rightarrow TS^1$$ with $$\hat{F}(w) = (w, F(w)).$$ This is a continuous map since it's continuous in each component, and furthermore $$\pi \circ \hat{F} = \text{Id}$$, so we've constructed a continuous section!

Let's now move to the case $$n \geq 2$$ with a bilinear multiplication. As before, we choose $$e$$ the identity for the multiplication and set $$v = \frac{e}{\|e\|} \in S^n$$. Take a basis $$\{e_1, \ldots, e_n\}$$ for $$\ker(v^*)$$. Define maps

$$ l_i : S^n \rightarrow \mathbb{R}^{n+1}, \ \ l_i(w) = \mu(w, e_i).$$

We claim that $$\{w, l_1(w), \ldots, l_n(w)\}$$ are all linearly independent in $$\mathbb{R}^{n+1}.$$ Assume we have

$$ \sum_{i=1}^n a_i l_i(w) + a_0 w = 0.$$

Using bilinearity of $$\mu$$ and the fact that $$\mu(w, e) = w$$, we can simplify the term on the right to get

$$
\begin{split}
\sum_{i=1}^n a_i l_i(w) + a_0 w = \sum_{i=1}^n a_i \mu(w, e_i) + a_0 \mu(w, e) \\
= \mu \left(w, \sum_{i=1}^n a_i e_i + a_0 e\right) = 0.
\end{split}
$$

Since there are no zero divisors and $$w \neq 0$$ (since it has norm $$1$$) we have

$$ \sum_{i=1}^n a_i e_i + a_0 e = 0.$$

These are all linearly independent by construction, so this forces

$$ a_i = 0, 0 \leq i \leq n.$$

Thus the original set was linearly independent. Now we define

$$ F_i : S^n \rightarrow \mathbb{R}^{n+1}, \ \ F_i(w) = l_i(w) - \langle l_i(w), w \rangle w.$$

In the same way as before, we see that $$F_i(w) \in \ker(w^*)$$ for each $$w \in S^n.$$ Furthermore we have that for each $$w \in S^n$$ $$\{F_1(w), \ldots, F_n(w)\}$$ is linearly independent. To see this, suppose we have

$$ \sum_{i=1}^n a_i F_i(w) = 0.$$

Writing out the definition, we see that

$$ \sum_{i=1}^n a_i l_i(w) - \sum_{i=1}^n a_i \langle l_i(w), w \rangle w = 0.$$

Let  $$ a_0 = - \sum_{i=1}^n a_i \langle l_i(w), w \rangle,$$ then we have

$$ \sum_{i=1}^n a_i l_i(w) + a_0 w = 0.$$

By the linear independence result from earlier, we see this forces

$$a_i = 0 , 0 \leq i \leq n.$$

Furthermore, as before, each of the $$F_i$$ are continuous, so we can construct continuous maps $$\hat{F}_i : S^n \rightarrow TS^n$$ defined by $$\hat{F}_i(w) = (w, F_i(w))$$ which satisfy $$\pi \circ \hat{F}_i = \text{Id}$$. This gives us $$n$$ linearly independent vector fields. Thus the existence of a bilinear multiplication without zero divisors on $$\mathbb{R}^{n+1}$$ implies that $$S^n$$ is parallelizable. Assuming the result by Bott, Milnor, and Kervaire as well as the [result on existence of bilinear multiplications without zero divisors on $$\mathbb{R}^n$$](https://www.math.csusb.edu/faculty/pmclough/CP.pdf) we get the other direction as well. So $$S^n$$ is parallelizable if and only if there exists a bilinear multiplication on $$\mathbb{R}^{n+1}$$ without zero divisors.

# Adams' theorem

[Frank Adams](https://en.wikipedia.org/wiki/Frank_Adams) gave a full solution to the problem of the number of maximal linearly independent vector fields on the $$n$$-sphere. Define the function $$\rho(n)$$ for $$n \geq 1$$ to be such that $$S^{n-1}$$ admits $$\rho(n)-1$$ linearly independent vector fields but not $$\rho(n)$$ (so this is the maximal number of linearly independent vector fields). Using the division algorithm modulo $$4$$, we're able to write each number uniquely as

$$ n = (2r+1) 2^{c+4d},$$

where $$r,c,d \geq 0$$ and $$c \leq 3.$$ Adams theorem states that we have $$\rho(n) = 2^c + 8d.$$ Notice immediately that if $$n$$ is odd, we must have $$c = d = 0$$ in the above, so $$\rho(n) = 1.$$ This implies that $$S^{2n} = 0$$ -- thus we have the famous [hairy ball theorem](https://en.wikipedia.org/wiki/Hairy_ball_theorem).

Adams theorem also gives us an alternate way of approaching the prior problem. That is, we wish to show that $$\rho(n) = n$$ if and only if $$n= 1,2,4,$$ or $$8$$ assuming Adams theorem. Let's do the implication (the other direction is clear by a modulo four calculation). Suppose $$\rho(n) = n$$. We have four cases to consider: $$c = 0, 1,2,3.$$ Assume first that $$c = 0$$. Then

$$1 + 8d = (2r+1)2^{4d}.$$

Notice that if $$d \geq 1$$, the number on the left is odd and the number on the right is even. So we must have $$d = 0$$, but this then forces $$1 = (2r+1)$$, which means $$r = 0$$. Thus $$n=1$$.

Next, assume that $$c = 1$$. We have

$$(2r+1)2^{1+4d} = 2 + 8d.$$

Dividing both sides by $$2$$, we're left with

$$ (2r+1) 2^{4d} = 1 + 4d.$$

We again run into the same issue with $$d \geq 1$$, so we're left with $$c = 1,$$ $$r = d = 0$$, which means $$n = 2$$. Now if $$c = 2,$$ we can do the same approach and we're left with

$$ (2r+1) 2^{4d} = 1 + 2d,$$

and again the same argument gives us that $$c = 2$$, $$r = d = 0$$, so $$n =4$$. Finally if $$c = 3$$, we're left with

$$ (2r+1) 2^{4d} = 1 + d.$$

We can't abuse the same argument here. Let

$$f(x) = 2^{4x} - 1 - x.$$

We see that

$$f'(x) = 4{2x+1} \log(2) - 1.$$

Assuming $$x \geq 0$$, we have that $$f'(x) > 0$$, so it is strictly increasing. Furthermore,

$$f(0) = 0,$$

so for all $$x > 0$$ we have $$f(x) > 0$$. This means that

$$ 2^{4d} > 1 + d \text{ if } d > 0,$$

and for all $$r \geq 0$$ we also have

$$ (2r+1) 2^{4d} > 1 + d \text{ if } d > 0.$$

Thus for equality we must have $$d = 0$$, which means

$$ (2r+1) = 1 \implies r = 0.$$

So we essentially have the same result as before -- we must have $$r = d = 0$$ and $$c = 3,$$ so $$n = 8$$. This exhausts all possible cases and the result follows.
