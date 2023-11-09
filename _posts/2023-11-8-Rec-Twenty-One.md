---
layout: post
title: Recitation Twenty One
tag: [MA1172]
---

In this recitation, we covered lines and curves in space as well as calculus with these functions.

# Lines and Curves

This is hopefully a review of the lecture.

## Vector Valued Functions

We're now going to generalize our work in calculus from one dimension to many. To start, we'll consider vector-valued functions as opposed to real-valued functions. A **vector-valued function** is a map

$$\vec{f} : \mathbb{R} \rightarrow \mathbb{R}^n.$$

Notice this takes a real number and outputs a vector. We can always express a vector valued function as follows:

$$\vec{f}(t) := \langle f_1(t), f_2(t), \ldots, f_n(t) \rangle,$$

where $$f_i : \mathbb{R} \rightarrow \mathbb{R}$$ is a real-valued function. Vector-valued functions are useful for modeling things in higher dimensions. For example, we know that it is impossible to find a real-valued function $$f : \mathbb{R} \rightarrow \mathbb{R}$$ whose graph is a circle, because a circle fails the vertical line test. However, we can "cheat" and find a vector valued function $$f : \mathbb{R} \rightarrow \mathbb{R}^2$$ whose graph will be a circle. To get a circle of radius $$r$$, we just look at the function

$$\vec{f}(\theta) := \langle r \cos(\theta), r \sin(\theta) \rangle.$$

Plotting this on your favorite calculator for $$r=1$$ gives us the [unit circle](https://www.wolframalpha.com/input?i=plot+%28cos%28t%29%2C+sin%28t%29%29).

## Functions in $$\mathbb{R}^n$$

At this point, there's a slight issue with what your book writes, and it never really discusses it. The output of a vector valued function $$\vec{f}$$ is a vector. This is fine, but in reality we sometimes don't want vectors, we want *points*. A point-valued function $$f : \mathbb{R} \rightarrow \mathbb{R}^n$$ can be written also as

$$ f(t) := (f_1(t), f_2(t), \ldots, f_n(t)),$$

where $$f_i : \mathbb{R} \rightarrow \mathbb{R}$$ is a real-valued function. Functionally, these objects are the same, or at least they look the same, but there's one important difference between the two. We are allowed to do algebra with vectors, while points are just objects in space with no algebraic rules associated to them. To emphasize, **all functions $$\vec{f} : \mathbb{R} \rightarrow \mathbb{R}^n$$ will be vector valued** for us, but sometimes we'll interpret them as points (especially when drawing pictures).

## Lines in $$\mathbb{R}^n$$

Just like in calculus, the building block of everything we want to work with is the line. Given two points $$p = (x_1, \ldots, x_n)$$ and $$q = (y_1, \ldots, y_n)$$ in $$\mathbb{R}^n$$, the **line** connecting these two points is given by

$$\vec{f}(t) = t p + (1-t) q = \langle y_1 + t(x_1 - y_1), y_2 + t(x_2 - y_2), \ldots, y_n + t(x_n - y_n) \rangle.$$

It's clear that this is a line (since it has degree one), and furthermore notice that $$\vec{f}(0) = q$$ and $$\vec{f}(1) = p$$.

In essence, what we're doing is looking at the vector $$\vec{v}$$ whose tail is $$q$$ and whose endpoint is $$p$$. With that in mind, we can rewrite this as

$$\vec{f}(t) = q + t \vec{v}.$$

Of course, this doesn't make sense as is. I told you earlier that you are not allowed to add or subtract points (especially with vectors). To get around this issue, let $$\vec{q}$$ be the vector whose tail is $$(0, \ldots, 0)$$ and whose endpoint is $$q$$. Then the real way to write this is

$$ \vec{f}(t) = \vec{q} + t \vec{v}.$$

We'll start to adopt this notation to make our lives easier -- if $$p$$ is a point in $$\mathbb{R}^n$$, then $$\vec{p}$$ is the vector whose tail is $$(0, \ldots, 0)$$ and whose endpoint is $$p$$.

## Parameterizations

Let's go back to our circle example. If I wanted to plot the unit circle in $$\mathbb{R}^2$$, I would look at the curve

$$\vec{f}(\theta) = \langle \cos(\theta), \sin(\theta) \rangle.$$

However, this is not the only way you could do this. Notice that if I write

$$\vec{g}(\theta) = \langle \cos(2\pi \theta), \sin(2\pi \theta) \rangle,$$

then plotting $$\vec{f}$$ and $$\vec{g}$$ gives me the same picture. In fact, I could put any constant next to $$\theta$$ and get the same picture. If two functions have the same graph, then we say that they **parameterize** the same curve. In fact, given any vector valued function $$\vec{f}(t)$$, if we look at the function $$\vec{f}(C t)$$ for a non-zero constant $$C$$, then we get a new parameterization of the same curve. The way to interpret this is that it's changing the "speed" that we draw the picture (pretending that the $$t$$ variable represents time). While parameterizations give us the same graph at the end of the day, they are different functions.

## Distance Between Points and Line

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

## Line on an Embedded Surface

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

# Calculus of Vector Valued Functions

Supposedly this will not be covered in lecture. This is new material that we will talk about in recitation (and may take up all of recitation).

Using our above observation, every vector valued function $$\vec{f}(t)$$ can be written as

$$ \vec{f}(t) = \langle f_1(t), \ldots, f_n(t) \rangle,$$

where $$f_i(t) : \mathbb{R} \rightarrow \mathbb{R}$$ is a real-valued function for $$1 \leq i \leq n$$. Using this, we can define the **limit** of a vector-valued function to be the limit of each of its components:

$$ \lim_{t \rightarrow a} \vec{f}(t) = \langle \lim_{t \rightarrow a} f_1(t), \ldots, \lim_{t \rightarrow a} f_n(t) \rangle.$$

If you wish, you can define one-sided limits using this observation as well. Once we have limits, we can talk about continuity. Recall that a real-valued function $$f$$ is continuous at $$t=a$$ if

$$ \lim_{t \rightarrow a} f(t) = f(a).$$

Similarly, a vector-valued function is **continuous** at $$t=a$$ if

$$ \lim_{t \rightarrow a} \vec{f}(t) = \vec{f}(a).$$

In other words, a vector-valued function is continuous if and only if each of its components are continuous.

Once we have limits, we can also define derivatives using the definition (and using the fact that we can add/subtract/scale vectors). Recall that the derivative at $$t=a$$ of a real-valued function $$f(t)$$ is given by

$$f'(a) = \lim_{h \rightarrow 0} \frac{f(a+h) - f(a)}{h},$$

provided this limit exists. Similarly, the **derivative** of a vector-valued function is given by

$$ \vec{f}'(a) = \lim_{h \rightarrow 0} \frac{\vec{f}(a+h) - \vec{f}(a)}{h} = \langle \lim_{h \rightarrow 0} \frac{f_1(h+a) - f_1(a)}{h}, \ldots,  \lim_{h \rightarrow 0} \frac{f_n(h+a) - f_n(a)}{h} \rangle.$$

We see that a vector-valued function is differentiable if and only if each of its components (the $$f_i$$) are differentiable. We can jump the gun and just write

$$\vec{f}'(a) = \langle f_1'(a), \ldots, f_n'(a) \rangle.$$

Finally, once we have derivatives we can make sense of integrals. Recall that the indefinite integral of a real-valued function $$f$$ is given by

$$ \int f(x)dx = F(x) + C, \text{ where } F'(x) = f(x).$$

Similarly, we can say that the **indefinite integral** of a vector-valued function $$\vec{f}$$ is given by

$$ \int \vec{f}(t) dt = \vec{F}(t) + \vec{C}, \text{ where } \vec{F}'(t) = \vec{f}(t),$$

and $$\vec{C}$$ is a vector of (arbitrary) constants. Using the fundamental theorem of calculus, we can deduce that

$$ \int_a^b \vec{f}(t) dt = \vec{F}(b) - \vec{F}(a), \text{ where } \vec{F}'(t) = \vec{f}(t).$$

Notice that we technically need to check the conditions for the fundamental theorem of calculus before we do this, but I'll leave that to you to think about (open your favorite calculus book and look at the things that come before the conclusion of the fundamental theorem of calculus).

Before finishing this section, let's review a couple properties of the derivative. These mostly arise from the issue that we do *not* have a way to multiply vectors, so there's not really a way to multiply vector-valued functions. Still, we do have some operations that make sense, and these do interact somewhat nicely with the derivative. Throughout, $$\vec{f}, \vec{g} : \mathbb{R} \rightarrow \mathbb{R}^n$$ are vector-valued functions, and $$s : \mathbb{R} \rightarrow \mathbb{R}$$ is a scalar function (or in other words, a real-valued function).

- We have

$$ \frac{d}{dt} \left( \vec{f}(t) \pm \vec{g}(t)\right) = \vec{f}'(t) \pm \vec{g}'(t),$$

since

$$ \vec{f}(t) \pm \vec{g}(t) = \langle f_1(t) \pm g_1(t), \ldots, f_n(t) \pm g_n(t) \rangle,$$

and for each $$1 \leq i \leq n$$ we have (from the properties of derivatives)

$$ \frac{d}{dt}(f_i(t) \pm g_i(t)) = f_i'(t) \pm g_i'(t),$$

so

$$ \frac{d}{dt} \left( \vec{f}(t) \pm \vec{g}(t)\right) = \langle f_1'(t) \pm g_1'(t), \ldots, f_n'(t) \pm g_n'(t) \rangle = \vec{f}'(t) \pm \vec{g}'(t).$$

- Similar to above, for a scalar $$C$$ we have

$$ \frac{d}{dt} ( C \vec{f}(t)) = C \vec{f}'(t).$$

It's the exact same type of argument, so I'll skip it.

- We have

$$ \frac{d}{dt} (s(t) \vec{f}(t)) = s'(t) \vec{f}(t) + s(t) \vec{f}'(t).$$

To check this, notice that

$$ s(t) \vec{f}(t) = \langle s(t) f_1(t), \ldots, s(t) f_n(t) \rangle.$$

Taking the derivative of each component, we have

$$ \frac{d}{dt} (s(t) f_i(t)) = s'(t)f_i(t) + s(t) f_i'(t) \text{ for } 1 \leq i \leq n.$$

So

$$ \frac{d}{dt} (s(t) \vec{f}(t)) = \langle  s'(t)f_1(t) + s(t) f_1'(t), \ldots,  s'(t)f_n(t) + s(t) f_n'(t) \rangle.$$

Now we can split up the right side using properties of vectors:

$$ \langle  s'(t)f_1(t) + s(t) f_1'(t), \ldots,  s'(t)f_n(t) + s(t) f_n'(t) \rangle = \langle s'(t) f_1(t), \ldots, s'(t) f_n(t) \rangle + \langle s(t) f_1'(t), \ldots, s(t) f_n'(t) \rangle = s'(t) \vec{f}(t) + s(t) \vec{f}'(t).$$

The identity holds!

- We have

$$ \frac{d}{dt} (\vec{f}(t) \cdot \vec{g}(t)) = \vec{f}'(t) \cdot \vec{g}(t) + \vec{f}(t) \cdot \vec{g}'(t).$$

This is almost the same kind of argument as in the previous bullet point. Notice

$$\vec{f}(t) \cdot \vec{g}(t) = \sum_{i=1}^n f_i(t)g_i(t).$$

Using product rule and the fact that derivatives split up over sums, we have

$$ \frac{d}{dt} \left( \vec{f}(t) \cdot \vec{g}(t) \right) = \sum_{i=1}^n [f_i'(t) g_i(t) + f_i(t) g_i'(t) ].$$

Now we can split up the sum into two sums:

$$\sum_{i=1}^n [f_i'(t) g_i(t) + f_i(t) g_i'(t) ] = \sum_{i=1}^n f_i'(t) g_i(t) + \sum_{i=1}^n f_i(t) g_i'(t).$$

This just follows from noting that we can add in whatever order we wish. Finally, the first term is exactly the same thing as $$\vec{f}'(t) \cdot \vec{g}(t)$$ and the second one is $$\vec{f}(t) \cdot \vec{g}'(t).$$

- As long as $$n=3$$ (i.e. $$\vec{f}$$ and $$\vec{g}$$ map to three dimensional vectors), we have

$$ \frac{d}{dt} (\vec{f}(t) \times \vec{g}(t)) = \vec{f}'(t) \times \vec{g}(t) + \vec{f}(t) \times \vec{g}'(t).$$

This is just a long calculation in coordinates. Notice

$$ \vec{f}(t) \times \vec{g}(t) = \langle f_2(t) g_3(t) - f_3(t) g_2(t), f_3(t) g_1(t) - f_1(t) g_3(t), f_1(t) g_2(t) - f_2(t) g_1(t) \rangle.$$

Let's study each component individually. The derivative of the first component of the cross product is

$$ \frac{d}{dt} (f_2(t) g_3(t) - f_3(t) g_2(t)) = f_2'(t) g_3(t) + f_2(t) g_3'(t) - f_3'(t) g_2(t) - f_3(t) g_2'(t).$$

Let's group like terms together:

$$ \frac{d}{dt} (f_2(t) g_3(t) - f_3(t) g_2(t)) = (f_2'(t) g_3(t) - f_3'(t)g_2(t)) + (f_2(t) g_3'(t) - f_3(t) g_2'(t)).$$

But this is exactly the same thing as the first component of $$\vec{f}'(t) \times \vec{g}(t) + \vec{f}(t) \times \vec{g}'(t).$$ A similar calculation with the other two components does the trick for us.

- Last but not least, we have

$$ \frac{d}{dt} \vec{f}(s(t)) = \vec{f}'(s(t)) s'(t).$$

Notice

$$\vec{f}(s(t)) = \langle f_1(s(t)), \ldots, f_n(s(t)) \rangle.$$

Now taking the derivative of each component, we have

$$ \frac{d}{dt} f_i(s(t)) = f_i'(s(t)) s'(t), \text{ where } 1 \leq i \leq n.$$

So

$$ \frac{d}{dt} \vec{f}(s(t)) = \langle f_1'(s(t)) s'(t), \ldots, f_n'(s(t)) s'(t) \rangle.$$

Since $$s'(t)$$ is a scalar, we can pull it out to get

$$ \frac{d}{dt} \vec{f}(s(t)) = s'(t) \vec{f}'(s(t)).$$

One fun observation to make now is the following. Notice

$$ \mid \vec{f}(t) \mid = \sqrt{\vec{f}(t) \cdot \vec{f}(t)}.$$

Squaring both sides, we get

$$ \mid \vec{f}(t) \mid^2 = \vec{f}(t) \cdot \vec{f}(t).$$

Now taking the derivative of the left hand side, we have

$$ \frac{d}{dt} \left(\mid \vec{f}(t) \mid^2 \right) = 2 \mid \vec{f}(t) \mid \cdot \frac{d}{dt} (\mid \vec{f}(t) \mid ).$$

Notice I used chain rule here -- ahead of time, I have no idea how the derivative and magnitude work with each other, so I cannot bring the derivative inside. For the left hand side, we just saw

$$ \frac{d}{dt} (\vec{f}(t) \cdot \vec{f}(t)) = 2\vec{f}'(t) \cdot \vec{f}(t).$$

So if we rearrange things, we now get the following nice formula:

$$\frac{d}{dt} (\mid \vec{f}(t) \mid ) = \frac{\vec{f}'(t) \cdot \vec{f}(t)}{\mid \vec{f}(t) \mid}.$$

So we've found out how to take the derivative of the magnitude!


# Example Problems

This seems to be an especially hard section for people, so I will try to include a variety of problems.

## Parameterizations and Lines

**Problem:** Given the point $$(2,3,4)$$ and the vector $$\vec{v} = \langle 3, -1, 2 \rangle$$, find a parameterization of the line that is parallel to $$\vec{v}$$ and passing through $$P$$.

**Solution:** We use our good old fact, which is that such a line is given by

$$ \ell(t) = t\vec{v} + \vec{P} = \langle 3t, -t, 2t \rangle + \langle 2,3,4 \rangle = \langle 3t+2, 3-t, 2t + 4 \rangle.$$

**Problem:** Suppose we have the curve $$y = 2x + 3$$.
- Find a parameterization of the curve with $$x(t) = t$$.
- Find a parameterization of the curve with $$y(t) = t$$.

**Solution:** Our parameterization will be given by $$\vec{r}(t) = \langle x(t), y(t) \rangle.$$ If $$x(t) = t$$ and $$\vec{r}$$ must lie on the line, then we get that

$$y(t) = 2x(t) + 3 = 2t + 3.$$s

So the first parameterization is $$\vec{r}(t) = \langle t, 2t+3 \rangle$$. On the other hand, if $$y(t) = t$$, then

$$t = y(t) = 2x(t) + 3 \implies (t-3)/2 = x(t).$$

So the second parameterization is $$\vec{r}(t) = \langle (t-3)/2, t \rangle$$. While these are two different parameterizations, we note that they carve out the same curve.

**Problem:** Suppose you are given the line $$\ell(t) = \langle 5t + 4, 12, 3-2t \rangle$$. Find a vector parallel to the curve.

**Solution:** The line can be written in the form $$\ell(t) = t \vec{v} + \vec{P},$$ where $$P$$ is a point on the line and $$\vec{v}$$ is a vector parallel to the line. To find *a* vector parallel to the line, we just need to look at everything with a $$t$$. This gives us $$\vec{v} = \langle 5, 0, -2 \rangle$$.

**Problem:** Determine if the lines $$\ell_1(t) = \langle 3t + 1, t + 4, 6t + 7 \rangle$$ and $$\ell_2(t) = \langle 6t+4, 2t, 12t + 5 \rangle$$ are intersecting, parallel, or neither.

**Solution:** A vector parallel to the first line is given by $$\vec{v}_1 = \langle 3, 1, 6 \rangle$$, while a vector parallel to the second line is given by $$\vec{v}_2 = \langle 6, 2, 12 \rangle$$. Recall that these vectors are parallel if $$\vec{v}_1 = C \vec{v}_2$$ for some constant $$C$$. This equality is true for $$C = 1/2$$, so the lines are parallel.

**Problem:** Given the lines $$\ell_1(t) = \langle 5t + 1, t, 3t \rangle$$ and $$\ell_2(t) = \langle t + 15, t + 6, t + 10 \rangle$$, determine if they intersect, are parallel, or neither. If they intersect, determine where.

**Solution:** The vector parallel to the first line is $$\vec{v}_1 = \langle 5, 1, 3 \rangle$$, and the vector parallel to the second line is $$\vec{v}_2 \langle 1, 1, 1 \rangle$$. It's easy to see that these are not parallel. To see if the lines intersect, we need to solve

$$\ell_1(t) = \ell_2(s).$$

In other words, we have three equations we need to study:

$$ 5t + 1 = s + 15, \ \ t = s + 6, \ \ 3t = s + 10.$$

If we solve the first one for $$s$$, we have

$$ s = 5t - 14.$$

Plugging this into the second equation gives us

$$t = (5t - 14) + 6 = 5t - 8.$$

Rearranging this,

$$ 0 = 4t - 8 \text{ or } 8 = 4t \text{ or } t = 2.$$

So if the lines intersect, they must intersect when $$s = 5(2) - 14 = -4$$ and $$t = 2$$. We know that this means the first two coordinates agree, so we just have to check the third coordinate is the same. Pugging in $$t = 2$$ and $$s = -4$$, we see

$$ 6 = 3(2) = 3t = s + 10 = (-4) + 10 = 6.$$

So the lines intersect. To determine where they intersect, we can just calculate $$\ell_1(2)$$ or $$\ell_2(-4)$$ (whichever is easier). Solving the first, we have that they intersect at the point

$$ \ell_1(2) = (11, 2, 6).$$

**Problem:** Let $$\vec{v} = \langle 1,1, 0\rangle$$ and $$\vec{w} = \langle 2,0,4 \rangle$$. Find the equation of the line perpendicular to $$\vec{v}$$ and $$\vec{w}$$ passing through the point $$(5,1,0)$$.

**Solution:** Since we are in dimension three, any vector perpendicular to these two vectors will be parallel to the line. We calculate

$$ \vec{v} \times \vec{w} = \langle 4, -4, -2 \rangle.$$

Using our fact, the line passing through the point $$(5,1,0)$$ can be parameterized by

$$ \ell(t) = \langle 4t + 5, 1 - 4t, -2t \rangle.$$

**Problem:** Find the line passing through the point $$(0,0,1)$$ at $$t=0$$ and $$(2,3,5)$$ at $$t=1$$.

**Solution:** We need to find a vector parallel to our line. This will be the vector with tail $$(0,0,1)$$ and tip $$(2,3,5)$$, so $$\vec{v} = \langle 2-0, 3-0, 5-1 \rangle = \langle 2,3,4 \rangle.$$ So the equation will be

$$ \ell(t) = \langle 0,0,1 \rangle + t \langle 2,3,4 \rangle = \langle 2t, 3t, 4t + 1 \rangle.$$  

**Problem** Suppose a bug is walking along the curve $$y = x^3 + 4,$$ and does so with constant velocity in the $$x$$-direction given by $$x'(t) = 5$$. If the bug starts walking at time $$t=0$$ with $$x$$-position $$2$$, find a vector-valued function for the location of the bug at time $$t$$.

**Solution:** As a first step, let's write the function as

$$\vec{r}(t) = \langle x(t), y(t) \rangle.$$

Since it has to lie on the curve, we know that $$y(t) = x(t)^3 + 4,$$ so we can write

$$\vec{r}(t) = \langle x(t), x(t)^3 + 4 \rangle.$$

Next, let's figure out what $$x(t)$$ is. We know that $$x'(t) = 5$$ and $$x(0) = 2$$. Integrating $$x'(t)$$, we have by the fundamental theorem of calculus that

$$ \int_0^t x'(s) ds = x(t) - x(0) = x(t) - 2.$$

On the other hand,

$$ \int_0^t x'(s)ds = \int_0^t 5 ds = 5t.$$

So we get $$x(t) = 5t + 2$$. Plugging this in,

$$ \vec{r}(t) = \langle 5t +2, (5t+2)^3 + 4 \rangle.$$

**Problem:** Suppose the equation for an ellipse is given by $$25x^2 + 16y^2 = 121.$$ Find two parameterizations for the ellipse.

**Solution:** Recall that the equation for an ellipse with width $$2a$$ and height $$2b$$ is given by

$$\frac{x^2}{a^2} + \frac{y^2}{b^2} = 1.$$

We can see from this that the "standard" ellipse centered at the origin according to this formula is going to be

$$ \vec{r}(t) = \langle a \cos(t), b \sin(t) \rangle, \text{ where } 0 \leq t \leq 2\pi.$$

So let's try to rearrange our formula to get this. Notice that $$25 = 5^2, 16 = 4^2,$$ and $$121 = 11^2$$. Rewriting:

$$ \frac{x^2}{(11/5)^2} + \frac{y^2}{(11/4)^2} = 1.$$

So the standard ellipse is parameterized by

$$\vec{r}(t) = \langle (11/5) \cos(t), (11/4) \sin(t) \rangle, \text{ where } 0 \leq t \leq 2\pi.$$

For any constant $$C > 0$$, we could also reparamterize this by $$C$$ to get

$$\vec{r}_C(t) = \langle (11/5) \cos(Ct), (11/4) \sin(Ct) \rangle, \text{ where } 0 \leq t \leq (2\pi)/C.$$

For example, moving double speed around the ellipse would be $$C=2$$.

**Problem:** Consider the curve $$C$$ traced out by the function

$$ \vec{r}(t) = \langle t^2, 3t+4, t \rangle.$$

Consider the embedded surface

$$S(\alpha) = \{(x,y,z) \in \mathbb{R}^3 \ | \ 9x - 6y^2 + 4z = \alpha \},$$

where $$\alpha$$ is some constant.
- For what $$\alpha$$ does $$C$$ never intersect $$S$$?
- For which $$\alpha$$ does $$C$$ intersect once?
- For which $$\alpha$$ does $$C$$ intersect twice?
- For which $$\alpha$$ does $$C$$ intersect more than twice?

**Solution:** Remember that we can write

$$\vec{r}(t) = \langle x(t), y(t), z(t) \rangle.$$

The curve $$\vec{r}(t)$$ intersects the embedded surface when

$$9t^2 - 6(3t+4)^2 + 4t = \alpha.$$

Expanding the left hand side:

$$ -45t^2 - 140t - 96 = \alpha.$$

Finally, let's move $$\alpha$$ to the other side:

$$ -45t^2 - 140t - (96 + \alpha) = 0.$$

The discriminant of this quadratic is

$$ (-140)^2 - 4(-45)(-96 - \alpha) = 2320 - 180\alpha.$$

Notice that $$C$$
- does not intersect the surface if the discriminant is negative,
- intersects the surface once if the discriminant is zero, and
- intersects the surface twice if the discriminant is positive.

So the point when the behavior changes happens when $$2320 - 180 \alpha =0$$, or $$\alpha = 116/9.$$ So $$C$$
- does not intersect $$S$$ if $$\alpha > 116/9,$$
- intersects $$S$$ once if $$\alpha = 116/9$$, and
- intersects the surface twice if $$\alpha < 116/9.$$

We also see from this analysis that the most $$C$$ intersects $$S$$ is twice.

# Calculus

**Problem:** Suppose $$\vec{p}(0) = \langle 1,1 \rangle,$$ \vec{p}'(0) = \langle 1, 0 \rangle$$, $$\vec{q}(0) = \langle 3, 10 \rangle$$, and $$\vec{q}'(0) = \langle 0,2 \rangle$$. Calculate

$$ \frac{d}{dt} (\vec{p}(t) \cdot \vec{q}(t)) \text{ when } t =0.$$

**Solution:** Use our identity above:

$$\frac{d}{dt} (\vec{p}(t) \cdot \vec{q}(t)) = \vec{p}'(t) \cdot \vec{q}(t) + \vec{p}(t) \cdot \vec{q}'(t).$$

Plugging in $$t=0$$, we get

$$ \vec{p}'(0) \cdot \vec{q}(0) + \vec{p}(0) \cdot \vec{q}'(0) = \langle 1,0 \rangle \cdot \langle 3, 10 \rangle + \langle 1,1 \rangle \cdot \langle 0,2 \rangle = 3 + 2 = 5.$$

**Problem:** Let $$\vec{p}(t) = \langle t + 4, 2t^2 + 3t + 1, t + 4 \rangle.$$ Find a $$t$$ so that $$\vec{p}(t)$$ is orthogonal to $$\vec{p}'(t).$$

**Solution:** Remember two vectors are orthogonal if $$\vec{v} \cdot \vec{w} = 0.$$ We calculate

$$\vec{p}'(t) = \langle 1, 4t + 3, 1 \rangle,$$

so we need to solve for the $$t$$ so that

$$\vec{p}'(t) \cdot \vec{p}(t) = 0.$$

Notice

$$\vec{p}'(t) \cdot \vec{p}(t) = (t+4) + (4t+3)(2t^2+3t+1) + (t+4) = 8t^3 + 18t^2 + 15t + 11.$$

This has a very nasty solution that you can only find with a calculator, but it is approximately $$t \approx -1.6163.$$
