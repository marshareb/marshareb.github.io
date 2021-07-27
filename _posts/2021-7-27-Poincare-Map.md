---
layout: post
title: Poincare Map
tag: dynamics
categories: ["Dynamics"]
---

In this post, I discuss how to prove the existence of a Poincare map.

# Poincare Map

Let $$\phi^t : M \rightarrow M$$ be a $$C^1$$ flow on a smooth compact manifold. Let $$K \subseteq M$$ be a **cross-section**, in the sense that it satisfies three conditions:

1) $$K$$ is transversal to the flow.

2) $$K$$ is a closed connected $$C^1$$ submanifold.

3) For every $$x \in M$$, there exists a $$|t| > 0$$ so that $$\phi^t(x) \in K$$.

The **Poincare map** then takes a point on the cross section and sends it to another point on the flow line which intersects the cross section. Generally (at least in the one-dimensional case) this is defined by the first time the flow line returns to $$K$$, and hence the Poincare map is called the **first return map.** The proof, as I've seen it, generally invokes the implicit function theorem (see, for example, [Fried](https://www.sciencedirect.com/science/article/pii/0040938382900179)). In this post, I'll attempt to prove the existence of a continuous map in a slightly different manner. With the implicit function theorem, one will get a $$C^1$$ Poincare map, so there's a slight advantage to that method. However, I'm hoping that the method in this post generalizes much more easily than the implicit function theorem method. For more info on the Poincare map, see [this post](https://marshareb.github.io/Metrization-and-Flow/) and [this post](https://marshareb.github.io/An-Ergodic-Theorem/) (while not directly applicable, Poincare recurrence gives us the measurable version of the Poincare map).

## Proof of Existence

To help with writing, we'll denote $$\phi^s(x)$$ as $$s \cdot x$$ (thus converting our flow to a $$C^1$$ $$\mathbb{R}$$-action).

Define the set

$$B(x,S) := \{ s \cdot x : 0 < \mid s \mid \leq S\}.$$

We define a map $$T : K \rightarrow (0,\infty)$$ by

$$ T(x) = \inf\{S > 0 : B(x,S) \cap K \neq \varnothing\}.$$

Notice that if $$B(x,S') \cap K \neq \varnothing$$ and $$S \geq S'$$, then we also have $$B(x,S) \cap K \neq \varnothing$$, so the infimum makes sense here. Suppose now that we have $$T(x) = 0$$ for some $$x$$. Then for each $$n \geq 1$$, we have $$B(x, 1/n) \cap K \neq \varnothing.$$ Take $$s_n$$ with the property that $$s_n \cdot x \in K$$ and $$ 0 < \mid s_n \mid \leq 1/n.$$ Notice that we have the endpoints of orbits accumulating at $$x$$. We can use this to contradict transversality, so it is impossible for $$T(x) = 0$$.

The next claim is that the infimum is achieved. Fix $$x \in K$$ and for notational simplicity let $$T := T(x).$$ Let $$(T_n) \subseteq (0,\infty)$$ be such that $$B(x, T_n) \cap K \neq \varnothing$$ and $$T_n \searrow T$$. For each $$n$$, we can choose $$s_n$$ with $$0 < \mid s_n \mid \leq T_n$$ so that $$s_n \cdot x =: y_n \in K$$. By compactness we can refine the sequence so that $$s_n \rightarrow s$$ and $$y_n \rightarrow y.$$ If we have $$s_n \rightarrow 0$$, we get a collection of orbits which accumulate at $$x$$, contradicting transversality again. Thus we must have $$s_n \rightarrow s \neq 0$$ and $$s_n \cdot x \rightarrow s \cdot x = y \in K.$$ Moreover we have that $$0 < \mid s \mid < T,$$ so $$B(x,T) \cap K \neq \varnothing.$$ Thus the infimum is a achieved for each $$x \in K$$.

We now claim that $$T$$ is a continuous function. Let $$(a,b) \subseteq [0,\infty)$$ be such that $$0 \leq a < b < \infty.$$ We examine

$$X := T^{-1}((a,b)) = \{x \in K : a < T(x) < b\}.$$

Since intervals of this form generate the topology, showing that $$X$$ is open implies that $$T$$ is continuous. Our goal is thus to show that $$X$$ is open. Let

$$ Y_1 := \{x \in K : 0 \leq T(x) \leq a\}, \ \ Y_2 := \{x \in K : b \leq T(x) < \infty\}.$$

Observe that we have $$X^c = Y_1 \cup Y_2.$$ If we can show $$Y_1, Y_2$$ are closed sets, we get that $$X$$ is open. Let's proceed with this now. We first show that $$Y_1$$ is closed. Suppose $$(x_n) \subseteq Y_1$$ is a sequence with $$x_n \rightarrow x.$$ Observe that for each $$n$$, we can find $$(s_n) \subseteq \mathbb{R}$$ with $$0 \leq \mid s_n \mid \leq a$$ so that $$s_n \cdot x_n =: y_n \in K.$$ This then gives us a sequence $$(y_n) \subseteq K$$. Notice that we can use compactness to refine the sequence so that $$s_n \rightarrow s$$ with $$0 \leq \mid s \mid \leq a.$$ Since $$s_n \rightarrow s$$, $$x_n \rightarrow x$$, we can use the continuity of the flow to get that $$s_n \cdot x_n \rightarrow s \cdot x.$$ Furthermore, we can use the compactness of $$K$$ to refine the sequence further so that $$y_n \rightarrow y \in K$$. Since the sequence converges to both $$s \cdot x$$ and $$y$$, we must have $$s \cdot x \in K$$, and hence $$0 \leq T(x) \leq \mid s \mid \leq a$$. Thus $$Y_1$$ is a closed set.

Now we show that $$Y_2$$ is a closed set. This is a trickier thing before and we'll need to use transversality of the flow again. Consider the set

$$K(\epsilon) := \{s \cdot x : x \in K, 0 \leq \mid s \mid < \epsilon\}.$$

Considering a coordinate chart around a point $$x \in K$$, we can intersect it with $$K(\epsilon)$$ for $$\epsilon$$ sufficiently small and get that this is homeomorphic to an open cylinder in $$\mathbb{R}^n$$, where $$n$$ is the dimension of the manifold. Doing this around each $$x \in K$$ shows that $$K(\epsilon)$$ is an open set.

Let $$(x_n) \subseteq Y_2$$ and suppose $$x_n \rightarrow x.$$ Assume for contradiction that $$T(x) < b.$$ Choose $$\epsilon > 0$$ sufficiently small so that $$T(x) + \epsilon < b$$. Let $$s$$ be such that $$\mid s \mid = T(x)$$ and $$s \cdot x \in K$$. We have that $$s \cdot x_n \rightarrow s \cdot x,$$ and since $$s \cdot x \in K(\epsilon)$$ we see that for large enough $$n$$ we have $$s \cdot x_n \in K(\epsilon).$$ But this implies that there is some $$t$$ with $$0 \leq \mid t \mid < \epsilon$$ and $$(s+t) \cdot x_n \in K.$$ Notice that we then have

$$ \mid s + t \mid \leq \mid s \mid  + \mid t \mid < \mid s \mid + \epsilon < b \leq T(x_n).$$

This gives us a contradiction, so we must have $$T(x) \geq b$$ as desired. Thus $$Y_2$$ is closed as well, and we can conclude $$X$$ is open. Moreover, we can conclude that $$T$$ is continuous.

Here we'll diverge a little from the goal and do something specialized to the case of $$\mathbb{R}$$. Consider

$$ R : K \rightarrow (0,\infty), \ \ R(x) = \inf\{ s > 0 : s \cdot x \in K\}.$$

Assuming that $$R(x) < \infty$$ for each $$x$$, all of the arguments above fall through for $$R$$. Moreover it should be obvious how to define our Poincare map at this point -- define $$r : K \rightarrow K$$ by $$r(x) = R(x) \cdot x.$$ This gives us a continuous map from $$K$$ to itself. However, notice that in Condition (3) for a cross section we didn't assume that there was necessarily a *positive* $$s$$ so that $$s \cdot x \in K,$$ just that there is a *non-zero* $$s$$. It is then possible that for all $$s > 0$$ we have $$s \cdot x \notin K.$$ Let's show this is not the case.

Let

$$ U(x,R) := \{ s \cdot x : 0 \leq \mid s \mid \leq R\}.$$

Define a new function $$S : M \rightarrow [0,\infty)$$ by

$$ S(x) = \inf\{ T \geq 0 : U(x,T) \cap K \neq \varnothing\}.$$

All of the arguments from above work for $$S$$, so we have a well-defined continuous function. Moreover, $$M$$ compact implies that $$S$$ is bounded from above, so for all $$x \in M$$ we have $$S(x) \leq Q.$$ Thus every flow line of length $$Q$$ must hit $$K$$. Let $$x \in K,$$ and consider $$2Q \cdot x.$$ We have that $$U(2Q \cdot x, Q) \cap K \neq \varnothing,$$ so there is some $$s$$ with $$ 0 \leq \mid s \mid \leq Q$$ so that $$(s + 2Q) \cdot x \in K.$$ Notice that

$$ \mid s + 2Q \mid \geq 2Q - \mid s \mid \geq Q > 0.$$

Thus we can equivalently say that for every $$x \in K$$ there is a positive $$s > 0$$ so that $$s \cdot x \in K.$$ We're now in the situation prior, so we have our Poincare map as desired.

Let's briefly talk about the implicit function theorem approach in tandem with this approach. Since everything is nice and $$C^1$$, we can take a coordinate chart around every $$x \in K$$ and treat things as functions on $$\mathbb{R}^n.$$ This gives us a neighborhood $$U$$ around $$x$$ and a $$C^1$$ function $$t : U \rightarrow (0,\infty)$$ so that for all $$y \in U$$ we have $$t(y) \cdot y \in K.$$ We claim that on this neighborhood $$t$$ agrees with the $$R$$ from prior. If we set up our definitions correctly, this will be the case. Since this is the case for each point in $$K$$, we get that the function $$t$$ will be exactly the function $$R$$ from earlier, so we can upgrade it to a $$C^1$$ function. The moral of the story is that once we have a cohesive way of choosing points, we can use the implicit function theorem to upgrade our map.
