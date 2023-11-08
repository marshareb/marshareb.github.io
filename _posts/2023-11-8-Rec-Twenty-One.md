---
layout: post
title: Recitation Twenty One
tag: [MA1172]
---

In this recitation, we covered lines and curves in space as well as calculus with these functions.

# Vector Valued Functions

We're now going to generalize our work in calculus from one dimension to many. To start, we'll consider vector-valued functions as opposed to real-valued functions. A **vector-valued function** is a map

$$\vec{f} : \mathbb{R} \rightarrow \mathbb{R}^n.$$

Notice this takes a real number and outputs a vector. We can always express a vector valued function as follows:

$$\vec{f}(t) := \langle f_1(t), f_2(t), \ldots, f_n(t) \rangle,$$

where $$f_i : \mathbb{R} \rightarrow \mathbb{R}$$ is a real-valued function. Vector-valued functions are useful for modeling things in higher dimensions. For example, we know that it is impossible to find a real-valued function $$f : \mathbb{R} \rightarrow \mathbb{R}$$ whose graph is a circle, because a circle fails the vertical line test. However, we can "cheat" and find a vector valued function $$f : \mathbb{R} \rightarrow \mathbb{R}^2$$ whose graph will be a circle. To get a circle of radius $$r$$, we just look at the function

$$\vec{f}(\theta) := \langle r \cos(\theta), r \sin(\theta) \rangle.$$

Plotting this on your favorite calculator for $$r=1$$ gives us the [unit circle](https://www.wolframalpha.com/input?i=plot+%28cos%28t%29%2C+sin%28t%29%29).

# Functions in $$\mathbb{R}^n$$

At this point, there's a slight issue with what your book writes, and it never really discusses it. The output of a vector valued function $$\vec{f}$$ is a vector. This is fine, but in reality we sometimes don't want vectors, we want *points*. A point-valued function $$f : \mathbb{R} \rightarrow \mathbb{R}^n$$ can be written also as

$$ f(t) := (f_1(t), f_2(t), \ldots, f_n(t)),$$

where $$f_i : \mathbb{R} \rightarrow \mathbb{R}$$ is a real-valued function. Functionally, these objects are the same, or at least they look the same, but there's one important difference between the two. We are allowed to do algebra with vectors, while points are just objects in space with no algebraic rules associated to them. To emphasize, **all functions $$\vec{f} : \mathbb{R} \rightarrow \mathbb{R}^n$$ will be vector valued** for us, but sometimes we'll interpret them as points (especially when drawing pictures).

# Lines in $$\mathbb{R}^n$$

Just like in calculus, the building block of everything we want to work with is the line. Given two points $$p = (x_1, \ldots, x_n)$$ and $$q = (y_1, \ldots, y_n)$$ in $$\mathbb{R}^n$$, the **line** connecting these two points is given by

$$\vec{f}(t) = t p + (1-t) q = \langle y_1 + t(x_1 - y_1), y_2 + t(x_2 - y_2), \ldots, y_n + t(x_n - y_n) \rangle.$$

It's clear that this is a line (since it has degree one), and furthermore notice that $$\vec{f}(0) = q$$ and $$\vec{f}(1) = p$$.

In essence, what we're doing is looking at the vector $$\vec{v}$$ whose tail is $$q$$ and whose endpoint is $$p$$. With that in mind, we can rewrite this as

$$\vec{f}(t) = q + t \vec{v}.$$

Of course, this doesn't make sense as is. I told you earlier that you are not allowed to add or subtract points (especially with vectors). To get around this issue, let $$\vec{q}$$ be the vector whose tail is $$(0, \ldots, 0)$$ and whose endpoint is $$q$$. Then the real way to write this is

$$ \vec{f}(t) = \vec{q} + t \vec{v}.$$

We'll start to adopt this notation to make our lives easier -- if $$p$$ is a point in $$\mathbb{R}^n$$, then $$\vec{p}$$ is the vector whose tail is $$(0, \ldots, 0)$$ and whose endpoint is $$p$$.

# Parameterizations

Let's go back to our circle example. If I wanted to plot the unit circle in $$\mathbb{R}^2$$, I would look at the curve

$$\vec{f}(\theta) = \langle \cos(\theta), \sin(\theta) \rangle.$$

However, this is not the only way you could do this. Notice that if I write

$$\vec{g}(\theta) = \langle \cos(2\pi \theta), \sin(2\pi \theta) \rangle,$$

then plotting $$\vec{f}$$ and $$\vec{g}$$ gives me the same picture. In fact, I could put any constant next to $$\theta$$ and get the same picture. If two functions have the same graph, then we say that they **parameterize** the same curve. In fact, given any vector valued function $$\vec{f}(t)$$, if we look at the function $$\vec{f}(C t)$$ for a non-zero constant $$C$$, then we get a new parameterization of the same curve. The way to interpret this is that it's changing the "speed" that we draw the picture (pretending that the $$t$$ variable represents time). While parameterizations give us the same graph at the end of the day, they are different functions.

# Distance Between Points and Line

Given two vectors $$\vec{v}$$ and $$\vec{w}$$, the distance between their endpoints is given by $$\mid \vec{v} - \vec{w} \mid$$. If we want to find the distance between a vector and a point, we apply the procedure described above to turn a point into a vector, and then calculate the distance between the vectors. The next step in this analysis is to look at the distance between a point and a line. Let $$p$$ be some point in $$\mathbb{R}^n$$, and let $$\vec{f}(t) = \vec{q} + t \vec{v}$$ be a line. We would like to know at point $$t$$ is $$\vec{f}(t)$$ closest to $$p$$. Notice that the distance between the point $$p$$ and $$\vec{f}(t)$$ at a given time $$t$$ is

$$ \mid \vec{f}(t) - \vec{p} \mid.$$

Now you could use calculus to figure out the time $$t$$ that minimizes the distance between the vector $$\vec{f}(t)$$ and $$\vec{p}$$. Call this time $$t_0$$. The value $$\mid \vec{f}(t_0) - \vec{p} \mid$$ is called the **distance between the line and the point**. Let's follow through on this analysis. Write

$$\vec{f}(t) = \langle q_1 + t v_1, \ldots, q_n + t v_n \rangle, \ \ \vec{p} = \langle p_1, \ldots, p_n \rangle.$$

Define

$$D(t) = \mid \vec{f}(t) - \vec{p} \mid^2 = ((q_1 - p_1) + tv_1)^2 + \cdots +  ((q_n - p_n) + tv_n)^2.$$

If we take the derivative of this, we have

$$D'(t) = 2v_1 ((q_1 - p_1) + tv_1) + \cdots + 2v_n ((q_n - p_n) + tv_n).$$

Now we can solve for $$D'(t) = 0$$. This amounts to solving

$$ (q_1 - p_1)v_1 + tv_1^2 + \cdots + (q_n - p_n)v_n + tv_n^2 = 0.$$

Rearranging:

$$ t(v_1^2 + \cdots + v_n^2) = (p_1 - q_1)v_1 + \cdots + (p_n - q_n)v_n.$$

Finally, we get

$$ t = \frac{(p_1 - q_1)v_1 + \cdots + (p_n - q_n)v_n}{v_1^2 + \cdots + v_n^2}.$$

Let $$\vec{w}$$ be the vector whose tip is $$p$$ and whose tail is $$q$$. Then the time $$t_0$$ that minimizes the distance between $$\vec{f}(t)$$ and $$p$$ is given by

$$t_0 = \frac{\vec{w} \cdot \vec{v}}{\vec{v} \cdot \vec{v}}.$$

This looks familiar. Notice that

$$ \vec{f}(t_0) = \vec{q} + t_0 \vec{v} = \vec{q} + \text{Proj}_{\vec{v}}(\vec{w}),$$

and since $$\vec{q} - \vec{p} = \vec{w}$$, we get

$$ \vec{f}(t_0) - \vec{p} = \text{Proj}_{\vec{v}}(\vec{w}) - \vec{w}.$$

This is the part of $$\vec{w}$$ which is orthogonal to $$\vec{w}$$. So the distance between the line $$\vec{f}(t)$$ and $$p$$ is the magnitude of this vector.

If one draws a picture of what this looks like, we get something like this:

![](https://ximera.osu.edu/mooculus/calculus2TextbookBySection/linesAndCurvesInSpaceSection/linesAndCurvesInSpace/digInLinesAndCurvesInSpace-figure4.svg)

If $$\theta$$ is the angle between the vectors, then we can also calculate this distance by doing

$$ \mid \vec{w} \mid \sin(\theta).$$

If we are in $$\mathbb{R}^3$$, we can use the cross product. Remember the geometric interpretation of the cross product is

$$ \mid \vec{v} \times \vec{w} \mid = \mid \vec{v} \mid \cdot \mid \vec{w} \mid \cdot \sin(\theta).$$

So rearranging, we have that the distance between the line and the point in $$\mathbb{R}^3$$ can also be calculated by

$$ \frac{\mid \vec{v} \times \vec{w} \mid}{\mid \vec{v} \mid}.$$

# Line on an Embedded Surface

Let $$g : \mathbb{R}^3 \rightarrow \mathbb{R}$$ be a function which takes three variables and outputs a real number. For example, we could think of

$$g(x,y,z) = x^2 + y^2 + z^2.$$

For simplicity, let's assume that $$g(x,y,z)$$ is a "nice" functions. I don't want to be too specific here, but one example of a nice function is one where it is a polynomial in each variable. In $$\mathbb{R}^3$$, an **embedded surface** is the collection of all points $$(x,y,z)$$ which satisfy a relation given by $$g(x,y,z) = 0$$, where $$g$$ is a "nice" function. Notice that some embedded surfaces are given in a misleading way. For example, consider the plane given by

$$-2x + 3y + 4z = 6.$$

Ahead of time, it doesn't seem to fit the bill. You might guess that the function is $$g(x,y,z) = -2x + 3y + 4z,$$ but the surface is characterized by $$g(x,y,z) = 6$$, not $$0$$. The way to get around this is with a little "cheat" -- you can move the $$6$$ to the other side. So if $$(x,y,z)$$ lies on the plane given by the above equation, then it also lies on the plane given by the equation

$$-2x + 3y + 4z - 6 = 0.$$

Now you can think about the function $$g(x,y,z) = -2x + 3y + 4z - 6,$$ and the curve is given by $$g(x,y,z) = 0$$.

Given our favorite line $$\vec{f}(t)$$ (or even more generally, any vector valued function), we say that the line **lies on the embedded surface** characterized by $$g(x,y,z) = 0$$ if

$$ g(\vec{f}(t)) = 0.$$

Recall that the function can be written as $$\vec{f}(t) = \langle f_1(t), f_2(t), f_3(t) \rangle,$$ so we can say that the line given by $$\vec{f}(t)$$ lies on the surface if for every $$t$$ we have

$$g(f_1(t), f_2(t), f_3(t)) = 0.$$
