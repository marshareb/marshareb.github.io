---
layout: post
title: Exploring Degree
tag: algebraic-topology
categories: ["Algebraic Topology"]
---

In this post, we explore the notion of degree for circles. This will mostly come from Hatcher and
Katok & Hasselblatt (A Panaroma of Dynamical Systems).

# Covering Space

A covering space is one that, in some sense, "properly" covers a space. Let $$X$$ be the space of interest. The idea is we want to find or examine a covering space $$\widetilde{X}$$ which covers our space evenly. The motivating example for this will be the circle. Consider $$S^1$$ to be the circle, and consider the map $$p : \mathbb{R} \rightarrow S^1$$ defined by $$p(c) = \exp(2\pi ic)$$. If we don't want to view the circle in $$\mathbb{C}$$, we could take the circle to be in $$\mathbb{R}^2$$ and $$p$$ to be the map $$p(c) = (\cos(2\pi c), \sin(2\pi c))$$. These notions are equivalent.

Notice that if we take any open arc $$(a,b) \subset S^1$$ (viewing it now as in $$\mathbb{R}$$ and a quotient, but this interpretation doesn't change anything of note) and we take the preimage, we get a bunch of open arcs which are all disjoint in $$\mathbb{R}$$. This is somehow the concept we wish to capture with a covering map: that is, if we take preimages of the space itself, we get disjoint copies of the space.

To make this more precise, we will say that the tuple $$(\widetilde{X}, p)$$ (sometimes just abbreviated to $$\widetilde{X}$$) is a *covering space* if it satisfies the following:
* $$p$$ is surjective (this is important, since we need to have disjoint copies of our space -- Hatcher gives an alternative if you don't want to require this).
* There is an open cover $$\{U_\alpha\}$$ of $$X$$ so that for each $$\alpha$$, $$p^{-1}(U_\alpha)$$ is a disjoint union of open sets in $$\widetilde{X}$$, each of which are homeomorphic to $$U_\alpha$$ via $$p$$.
* Furthermore, we will require $$\widetilde{X}$$ to be connected. (Hatcher doesn't require this property, but it doesn't hurt to throw it on).

We note that in the second property listed above, we had to use homeomorphisms to identify our copies as the same. This is since we're working with topology, so that's the only way we can test if things are the same.

If you drop the third condition, there are generally a lot of different options for a covering space. You could trivially take disjoint copies of the circle to be a covering space if you omit this third condition. Even with the third condition, there is generally a lot of different options for a covering space (for example, the circle is it's own covering space). Hatcher gives a few examples of how to cover $$S^1 \wedge S^1$$ which are interesting, but I don't feel the need to jump into.

We call a (continuous) curve $$\gamma : [0,1] \rightarrow X$$ simple if it satisfies the property that there are not distinct $$t_1, t_2 \in [0,1]$$ with $$\gamma(t_1) = \gamma(t_2)$$. In other words, the path does not cross itself. Recall that a space $$X$$ is said to be *simply connected* if it a path-connected domain (meaning for every two points $$x_0, x_1 \in X$$, we can find a path $$\gamma : [0,1] \rightarrow X$$ with $$\gamma$$ continuous and $$\gamma(0) = x_0$$, $$\gamma(1) = x_1$$) and if we have the property that any simple closed curve (closed meaning $$\gamma(0) = \gamma(1)$$) can be continuous shrunk to a point. Recall that continuously shrunk means there is a continuous path $$\Gamma : [0,1] \times [0,1] \rightarrow X$$ satisfying $$\Gamma(0, \cdot) = \gamma$$, $$\Gamma(1, \cdot) = x_0$$ (where $$x_0 \in X$$ a point).

We could have refined a little of the discussion above by taking $$\gamma : S^1 \rightarrow X$$ instead of the unit circle for a closed curve. This is not really any more enlightening in terms of notation, but it maybe paints the picture that this is a loop.

We have the easy examples for simply-connected spaces. For example, $$\mathbb{R}$$ is simply connected. The circle is not simply-connected (you cannot reduce the circle itself to a point continuously). If we add on a fourth condition, say the covering space is simply-connected, then we have what is called the *universal covering* of $$X$$. Notice that this cover cannot just be the circle itself, so we've reduced the set of covers that we're looking at.

Hatcher gives a construction describing how you can *always* find a simply-connected covering space of a topological space $$X$$. I'll leave it to the reader to look into it if they're interested.

One core reason to look into universal covering maps (or covering maps in general) is that they have a unique lifting property. The idea is that given a path in our underlying space, we can find a unique path in our covering space corresponding to our original path (in the sense that it factors through the surjective map). Taking a loop on our circle $$f : S^1 \rightarrow S^1$$, we can extend this to a map $$F : \mathbb{R} \rightarrow \mathbb{R}$$ which satisfies the property that $$p \circ F = f \circ p$$. This extension is unique up to a choice of an integer to start at.

# Degree for the Circle

We prove the more fundamental idea stated at the end of the last section. The content of this can be found in Katok & Hasselblatt, Proposition 4.3.1. We let $$f : S^1 \rightarrow S^1$$ be continuous. The first step is to show that there exists a lift $$F : \mathbb{R} \rightarrow \mathbb{R}$$ satisfying the property $$f \circ p = p \circ F$$, where $$p :
\mathbb{R} \rightarrow S^1$$ is just the usual quotient map (which agrees with a lot of the other definitions we've put out today). We do know that $$f$$ wraps around $$S^1$$ at least once (since the map is onto), so viewing the map on the square $$[0,1] \times [0,1]$$ we see that the set

$$A = \{x \in S^1 : \lim_{y \rightarrow x^-} f(y) = 1\}$$

is possibly nonempty (if it isn't, it means that our function loops around the circle once). Note to push the function onto the square and to ensure this is well-defined, we need to make some choices on endpoints, but whatever choices you decide to make will not affect this process. For example, our function could loop around the circle twice at a uniform speed. If this is the case, we just set $$f(1/2) = 1$$ and then have it continue afterwards as though it were from $$0$$.

Assume for now that $$A$$ is finite, $$f$$ is increasing. We can order $$A$$, so that we can write $$A = (y_n)_{n \geq 0}$$, where $$y_0 = 0$$ and $$y_0 < y_1 < \cdots$$ and so on. We can define $$F : [y_0,y_1) \rightarrow [0,1)$$ by $$F = f$$ on this interval. Define $$F : [y_n, y_{n+1}) \rightarrow [n, n+1]$$ by $$F|_{[y_n,y_{n+1})} = f + n$$. This then defines $$F$$ continuous on $$[0,1)$$, and gives us an obvious way of extending it to the real line: that is, define $$F : [1,2) \rightarrow \mathbb{R}$$ via $$F|_{[1,2)} = F|_{[0,1)} + |A|$$ (add the cardinality of $$A$$). We can continue in this fashion, defining $$F|_{[n,n+1)} = F|_{[0,1)} + n |A|$$. This gives us a continuous function $$F : [0,\infty) \rightarrow \mathbb{R}$$ which satisfies our quotienting properties. We can then make this symmetric about $$0$$, which constructs our function on the real line.

Can a continuous function wrap around the circle a countable or even an uncountable number of times? This is an interesting question. If we do it a countable number of times, the construction above still works. I don't think we can do it an uncountable number of times (at least not without backtracking), but my intuition is from algebraic topology and I don't want to get into this.

Notice that in the above construction we implicitly assumed that $$f$$ was (essentially) increasing, meaning that $$f(0) = 0$$ and it (over the long run, maybe not locally) increased to $$1$$. It could be that $$f$$ is (essentially) decreasing, in which case we change all of our pluses to minuses and everything still works out. [Remark: The terms essentially are not rigorous here, I'm just trying to say that it's trending upwards over the long run.] It may also be that $$f$$ is increasing for a short time, then backtracking and decreasing. We change the pluses and minuses appropriately for this kind of case as well.

Regardless, this construction establishes the existence of our lift. We then need to establish uniqueness. Uniqueness follows since if $$G$$ is another lift, we have that $$p \circ G = f \circ p = p \circ F$$, and so $$F$$ and $$G$$ differ by an integer. Since the difference of continuous functions is continuous, we get a map $$F - G : \mathbb{R} \rightarrow \mathbb{Z}$$, which forces it to be constant. So we have uniqueness of lifts up to a constant (which is fine).

We now define the degree of $$F$$ to be $$F(x+1) - F(x)$$. We explicitly constructed a lift for which this quantity measures the number of times $$f$$ wraps around the circle. Since all lifts differ by a constant, we get that this notion still holds regardless of lift and regardless of the point $$x$$ chosen.

For free based on this discussion, we also get that if $$f$$ is a homeomorphism from the circle to itself, then the degree will be (in absolute value) $$1$$. It cannot be $$0$$, since this implies it doesn't wrap around the circle at all, and it cannot be greater than $$1$$ since it wraps around more than once, implying it is not injective. The degree being less than $$1$$ follows from the map reversing orientation (assuming we chose an orientation ahead of time).

I recently made the (somewhat silly) mistake of assuming that the degree measured the number of preimages. This sadly isn't true, but it sort of captures the same idea. The number of preimages must be at least the degree in absolute value, so there is some value to taking the approach of using this.

To extend this discussion beyond the circle requires a little more manifold theory or algebraic topology, both of which I don't want to get into quite yet. I think the picture painted here gives a good enough idea to prevent someone from making the same mistakes I did when it came to degrees of functions. Katok & Hasselblatt go a different approach for existence. Their approach is shorter, but also omits some important details and kind of misses the point of constructing it for the degree. Even though I also skimmed some important details, I think the overall idea is more intuitive.
