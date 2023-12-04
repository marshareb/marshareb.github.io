---
layout: post
title: Recitation Twenty Six
tag: [MA1172]
---

In this recitation, we covered tangent planes, chain rules and directional derivatives, and the gradient.

# Differentiability

Throughout, let $$F : \mathbb{R}^n \rightarrow \mathbb{R}$$ be a function of several variables. Although we have a notion of partial derivatives, we don't really have a notion of "derivatives" for the function yet. The closest is the gradient, but it still doesn't line up with the calculus version of a derivative. Let's take a step back and try to remember why we were taking a derivative in the first place. We wanted the best "linear approximation" of our function $$f : \mathbb{R} \rightarrow \mathbb{R}$$. You might then guess that if we had $$F : \mathbb{R}^n \rightarrow \mathbb{R}$$, then we'd want the best "planar approximation" of our function.

Recall that a **plane** in $$\mathbb{R}^n$$ can be seen through a function $$L : \mathbb{R}^n \rightarrow \mathbb{R}$$ of the form

$$ L(x_1, \ldots, x_n) = a_1 x_1 + \cdots + a_n x_n + D, \text{ where } a_i \in \mathbb{R} \text{ and } D \in \mathbb{R}.$$

A function $$F : \mathbb{R}^n \rightarrow \mathbb{R}$$ is **differentiable** at $$x=a$$ if there is a plane $$L_a : \mathbb{R}^n \rightarrow \mathbb{R}$$ so that

$$ \lim_{x \rightarrow a} \frac{F(x) - L_a(x)}{\mid x - a \mid} = 0.$$

Recall that this limit is not a one-dimensional limit, and so we need to take care when evaluating it. Notice that in one-dimension (i.e. $$n =1$$), this is saying that a function is differentiable if there exists numbers $$M, D \in \mathbb{R}$$ so that

$$ \lim_{x \rightarrow a} \frac{f(x) - (Mx + D)}{x-a} = 0.$$

Remember that, using [Taylor series results](https://en.wikipedia.org/wiki/Taylor%27s_theorem), a function is differentiable at a point $$x=a$$ if there is a function $$h_a(x)$$ which satisfies the property that $$\lim_{x \rightarrow a} h_a(x) = 0$$ and

$$ f(x) = f(a) + f'(a) (x-a) + h_a(x) (x-a).$$

So if we let $$M = f'(a)$$ and $$D = f(a)$$, we have

$$ \lim_{x \rightarrow a} \frac{f(x) - (Mx + D)}{x-a} = \lim_{x \rightarrow a} \frac{h_a(x)(x-a)}{x-a} = 0.$$

So it works in one dimension! We just never really thought about things like this.

Going back to the above, if the function $$F$$ is differentiable at a point $$x=a$$, then we call the plane $$L_a$$ the **tangent plane** at the point $$x=a$$. Without knowing a lot of information about the function already, it is generally pretty hard to figure out what the tangent plane at a point is. Luckily, we have a couple tools to help determine "sufficient" conditions for differentiability.

**Theorem:** If $$F : \mathbb{R}^n \rightarrow \mathbb{R}$$ is a function defined on an open set containing $$a$$ and all partial derivatives of order one are defined and continuous on an open set containing $$a$$, then $$F$$ is differentiable at $$x=a$$.

Note that (apriori) this is not a "necessary" condition, meaning that it tells us when a function is differentiable, but a function may be differentiable without more information. Here is an example of a "necessary" condition.

**Theorem:** If $$F$$ is differentiable at $$x=a$$, then all partial derivatives of order one exist at $$x=a$$.

What this means is that if one partial derivative of order one does not exist at $$x=a$$, then the function cannot be differentiable at $$x=a$$. Finally, we have the following result (which is a throwback to the one variable case).

**Theorem:** If $$F$$ is defined on an open set containing $$x=a$$ and is differentiable at $$x=a$$, then it is continuous at $$x=a$$.

# Tangent Planes

Given Taylor's results, we were able to figure out what the tangent line at a point is supposed to be. How do we do this in higher dimensions? It turns out that the trick is mostly the same. Restricting to the case of two dimensions (although you can do higher), the tangent plane to a function at a point $$(x,y) = (a,b)$$ will just be given by

$$ L_{(a,b)}(x,y) := F(a,b) + \frac{\partial F}{\partial x}(a,b) (x-a) + \frac{\partial F}{\partial y}(a,b) (y-b).$$

This explains a little bit of the necessary conditions from earlier -- clearly for this plane to make sense, we need that the partial derivatives must exist.

Now, recall that the gradient is the vector of partial derivatives. Notice if we write $$\vec{a} = \langle a,b\rangle$$ and $$\vec{x} = \langle x,y \rangle$$, then we can rewrite the above as

$$ L_{\vec{a}}(\vec{x}) = F(\vec{a}) + \nabla F(\vec{a}) \cdot (\vec{x} - \vec{a}),$$

where $$\cdot$$ is the dot product and $$\nabla F$$ is the gradient from last lecture. This works in all dimensions (generalizing the components accordingly) and it is much easier to write!

# Chain Rule

Let $$F : \mathbb{R}^n \rightarrow \mathbb{R}$$ be a function of several variables, and let $$\vec{r} : \mathbb{R} \rightarrow \mathbb{R}^n$$ be a vector-valued function. Suppose we wanted to calculate $$\frac{d}{dt} F(\vec{r}(t)).$$ If we could make sense of "$$F'$$", then we could say it is

$$ \frac{d}{dt} F(\vec{r}(t)) = F'(\vec{r}(t)) \vec{r}'(t).$$

Two things are nonsense in the above. First, $$F'$$ is not well-defined (is it a vector, scalar, or something else?) and second, $$\vec{r}'$$ is a vector, so what is the operation between these things? One natural guess for what $$F'$$ should be is the gradient -- after all, in our above notes it played the role of the derivative. A gradient is a vector, so we should be doing some operation between vectors. Notice that $$F(\vec{r}(t))$$ is a scalar valued function, so whatever our output is better be a real number. We know that the dot product gives us a real number, so maybe we'll try using that. We make an educated guess that

$$ \frac{d}{dt} F(\vec{r}(t)) = \nabla F(\vec{r}(t)) \cdot \vec{r}'(t).$$

It turns out this is the correct interpretation of the chain rule!

Now let's see how this works in two dimension. Let $$z = F(x,y)$$ be a function, and suppose that $$x$$ and $$y$$ are functions of $$x$$. This is confusing to think about without more notation, so let's define

$$ \vec{r}(x) = \langle x, y(x) \rangle.$$

This is a little silly, but notice that $$\vec{r} : \mathbb{R} \rightarrow \mathbb{R}^2$$ is a vector-valued function now. We can think of

$$z(x) = F(\vec{r}(x)).$$

So if we take the derivative of this, we can use the chain rule to get

$$ \frac{dz}{dx} = \nabla F(x,y) \cdot \langle 1, \frac{dy}{dx} \rangle = \frac{\partial z}{\partial x} + \frac{\partial z}{\partial y} \frac{dy}{dx}.$$

Let's think of an example. Consider the implicit function

$$x^2y - xy^3 = 3.$$

We can't write out explicitly what $$y$$ is, but given an $$x$$ we are able to solve for a $$y$$. So we'll write $$y(x)$$ to indicate what this $$y$$ should be. Notice this is poorly defined (maybe there's more than one value of $$y$$), but we'll ignore these issues for the moment. Now, to solve for $$\frac{dy}{dx}$$, we could use implicit differentiation to solve for this, but we could also use the chain rule. Let

$$z = x^2y - xy^3.$$

Now we're trying to solve for $$\frac{dy}{dx}$$ along the level curve $$z=3$$. Since we're along a level curve, we know that $$z$$ is constant, so $$\frac{dz}{dx} = 0.$$ On the other hand, our formula gives us

$$ 0 = \frac{dz}{dx} = \frac{\partial z}{\partial x} + \frac{\partial z}{\partial y} \frac{dy}{dx}.$$

Solving, we get

$$ \frac{dy}{dx} = - \frac{\frac{\partial z}{\partial x} }{\frac{\partial z}{\partial y}}.$$

Notice

$$ \frac{\partial z}{\partial x} = 2xy - y^3, \ \ \frac{\partial z}{\partial y} = x^2 - 3xy^2,$$

so

$$ \frac{dy}{dx} = \frac{y^3 - 2xy}{x^2 - 3xy^2}.$$

This matches what we'd get with implicit differentiation!

# Directional Derivatives

Given a function of several variables $$F$$, remember that $$\frac{\partial F}{\partial x}$$ is asking for the instantaneous rate of change of $$F$$ in the direction of $$x$$. Let's think about the case $$n=2$$. The vector $$\langle 1,0 \rangle$$ is the unique unit vector pointing in the direction of $$x$$, and so one might interpret the partial derivative as the derivative in the direction of $$\langle 1,0 \rangle$$. The partial derivative in the direction of $$y$$ would then be the derivative in the direction of $$\langle 0,1 \rangle$$. We can then make sense of scaling, since derivatives behave nicely with constants. Asking for the derivative in the direction of $$\langle 2,0 \rangle$$ can be seen as the derivative if we move at $$2$$ times the speed in the $$x$$-direction, or

$$ D_{\langle 2, 0 \rangle} F(x,y) = \frac{\partial}{\partial x}(F(2x, y)) =  2 \frac{\partial F}{\partial x}(x,y).$$

Once we know how to take the derivative in the direction of unit vectors, the above intuition tells us that we know how to take the derivative in the direction of all vectors by using the chain rule. So we just need to figure out how unit vectors should work.

Taking a step back, if I asked you to take the derivative of $$F$$ in the direction of a unit vector $$\vec{v}$$ using the limit definition, you might guess that

$$ D_{\vec{v}} F(\vec{x}) = \lim_{h \rightarrow 0} \frac{F(\vec{x} + h \vec{v}) - F(\vec{x})}{h}.$$

It turns out that by playing with the limit definition carefully, one can show that this will be equal to

$$ D_{\vec{v}} F (\vec{x}) = \nabla F (\vec{x}) \cdot \vec{v}.$$

Explicitly, if we write $$\vec{v} = \langle v_1, v_2 \rangle$$, then this is just saying that

$$ D_{\vec{v}} F(x,y) = v_1 \frac{\partial F}{\partial x}(x,y) + v_2 \frac{\partial F}{\partial y}(x,y).$$

So it turns out that the partial derivatives tell us all the information we need to figure out the instantaneous rate of change of $$F$$ in any direction!

If we write the geometric definition for the dot product, we have (for a unit vector $$\vec{v}$$) that

$$ D_{\vec{v}} F (\vec{x}) = \mid \nabla F(\vec{x}) \mid \cdot \mid \vec{v} \mid \cdot \cos(\theta),$$

where $$\theta$$ is the angle between the gradient at $$\vec{x}$$ and the vector $$\vec{v}$$. Since $$\vec{v}$$ is a unit vector, this is equal to

$$ D_{\vec{v}} F (\vec{x}) = \mid \nabla F(\vec{x}) \mid \cdot \cos(\theta).$$

Now, $$\cos(\theta)$$ is bounded between $$-1$$ and $$1$$, and is only equal to $$1$$ on the interval $$[0, \pi]$$ if $$\theta = 0$$, it is equal to $$0$$ if $$\theta = \pi/2$$, and it is equal to $$-1$$ if $$\theta = \pi$$. Since the derivative measures the rate of change, this says that the function changes the fastest in the direction of the gradient, it decreases the fastest in opposite direction of the gradient, and there is no change if the direction is orthogonal to the gradient (all interpreted appropriately). This tells us what the gradient is good for -- it is the direction of fastest change!
