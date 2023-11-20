---
layout: post
title: Recitation Twenty Three
tag: [MA1172]
---

In this recitation, we covered functions of several variables and planes.

# Special Unit Vectors

Let $$\vec{f}(t)$$ be a vector valued function. Recall that the **unit tangent vector** for $$\hat{f}(t)$$ is the function

$$\vec{\tau}(t) := \frac{\vec{f}'(t)}{\mid \vec{f}(t) \mid}.$$

Since $$\mid \vec{\tau}(t) \mid = 1$$, we know from earlier that its derivative will be orthogonal to it. The **principal unit normal vector** is defined by

$$ \vec{n}(t) := \frac{\vec{\tau}'(t)}{\mid \vec{\tau}'(t) \mid}.$$

This is a vector which is orthogonal to the tangent vector and is unit.

**Remark:** Normal, perpendicular, and orthogonal all mean the same thing when it comes to vectors.


# Functions of Several Variables

We've gone from scalar valued functions, i.e. functions of the form $$f : \mathbb{R} \rightarrow \mathbb{R}$$, to vector valued functions, i.e. functions of the form $$f : \mathbb{R} \rightarrow \mathbb{R}^n$$. The next step is to think about functions of the form $$f : \mathbb{R}^n \rightarrow \mathbb{R}$$; we call these **functions of several variables**. These are functions which take ordered tuples of real numbers $$(x_1, \ldots, x_n)$$ and output a real number. You can also think of these as functions that take vectors and output real numbers by using the correspondence between points in space and vectors.

Let $$f : \mathbb{R}^n \rightarrow \mathbb{R}$$ be a function of several variables (although technically the upcoming definition works for any kind of function). The **preimage** of a point $$t \in \mathbb{R}$$ is the collection of all points $$(x_1, \ldots, x_n)$$ so that $$f(x_1, \ldots, x_n) = t$$. We write this as

$$f^{-1}(t) = \{ (x_1, \ldots, x_n) \in \mathbb{R}^n \ | \ f(x_1, \ldots, x_n) = t\}.$$

This is also sometimes referred to as the **level set** (especially in the context of functions of several variables).

**Warning:** The $$-1$$ is misleading -- this is **not** an inverse. This works for functions that are not even invertible.

**Example:** Consider the function $$f(x) = x^2$$. Then $$f^{-1}(1) = \{-1, 1\}$$.

**Observation:** Recall that a function $$f$$ is one-to-one if $$f(x) = f(y)$$ implies $$x=y$$. If a function is one-to-one, then the preimage of any point is at most one point. So $$f(x) = x^2$$ is not one-to-one, since the preimage of $$1$$ has two points.

Going back to functions of several variables, let's consider the function

$$ F : \mathbb{R}^2 \rightarrow \mathbb{R}, \ \ F(x,y) := x^2 + y^2.$$

Notice that for $$r > 0$$ we have that the level set $$F^{-1}(r^2)$$ is a circle of radius $$r$$.

If the domain of a function of several variables is a subset of $$\mathbb{R}^2$$, then we can visualize it by plotting it in three dimensions, with the third dimension being the output of the function. More precisely, we can look at the **graph** of the function of several variables by looking at

$$\{(x,y, F(x,y)) \in \mathbb{R}^3 \ | \ (x,y) \text{ are in the domain of } F\}.$$

# Planes

We now have the ingredients to describe a plane in $$\mathbb{R}^3$$. Given a vector $$\vec{v}$$, we can define the function

$$F_{\vec{v}}(x,y,z) := \langle x,y,z \rangle \cdot \vec{v}.$$

This is a function of several variables, and the level set $$F_{\vec{v}}^{-1}(0)$$ is the collection of all vectors orthogonal to $$\vec{v}$$. Notice that this level set is free in two variables (meaning that once we know two variables, the other one is determined), so this determines a plane in $$\mathbb{R}^3$$ which goes through the origin. Suppose we know that the point $$p = (p_1, p_2, p_3)$$ lies on the plane. We wish to treat this like the origin $$(0,0,0)$$. We can consider the function $$\tau_p : \mathbb{R}^3 \rightarrow \mathbb{R}^3$$ given by

$$\tau(x,y,z) := (x-p_1, y-p_2, z-p_3).$$

This shifts everything so that $$p$$ is now the origin. We can compose our functions now to get

$$F_{\vec{v}, p}(x,y,z) := F_{\vec{v}} \circ \tau_p(x,y,z).$$

By the description above, we see that $$F_{\vec{v}, p}^{-1}(0)$$ determines a plane which goes through the point $$p$$. We call $$\vec{v}$$ the **normal vector** to the plane.

Given two vectors $$\vec{w}_1, \vec{w}_2$$ such that $$F_{\vec{v}, p}(\vec{w}_1) = F_{\vec{v}, p}(\vec{w}_2) = 0$$ and $$\vec{w}_1 \times \vec{w}_2 \neq \vec{0}$$ (or, even simpler -- $$\vec{w}_1$$ and $$\vec{w}_2$$ are not parallel), we can give a **parameterization** for the plane by

$$L(s,t) := \vec{p} + s \vec{w}_1 + t \vec{w}_2.$$
