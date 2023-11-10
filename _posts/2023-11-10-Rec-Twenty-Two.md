---
layout: post
title: Recitation Twenty Two
tag: [MA1172]
---

In this recitation, we covered motion and paths in space as well as arclength.

# Motions and Paths

One key application of everything we've been talking about is analyzing motion in space. We did this kind of analysis in Calc 1 by thinking about $$s(t)$$ as a function which gives the position of a particle at time $$t$$. Remember that
- the velocity is given by $$v(t) := s'(t)$$,
- the acceleration is given by $$a(t) := v'(t)$$,
- the speed is given by $$S(t) := \mid v(t) \mid$$,
- and the displacement over the interval $$[a,b]$$ is given by

$$ \int_a^b s(t)dt.$$

It turns out that this is exactly the same for vector valued functions. Let's use this to study projectile motion. Suppose someone tosses a baseball. Let's assume that we're viewing the person in a two dimensional plane, and (with respect to some frame of reference) we know that the baseball has initial position $$\vec{s}(0) = \langle x(0), y(0) \rangle$$. Let's also assume that the baseball leaves the persons hand with initial velocity given by $$\vec{v}(0) = v_0 \langle \cos(\theta), \sin(\theta) \rangle$$, where $$\theta$$ is referred to as the **angle of elevation**. Once the baseball leaves the persons hand, the only force acting on it is gravity, which (in our picture) acts only on the $$y$$-coordinate. Translating this, the only thing we know is that $$\vec{a}(t) = \langle 0, -g \rangle$$ (here, $$g$$ is the gravitational constant). Let's use this to try to determine the velocity. We have

$$\vec{v}(t) = \int \vec{a}(t) dt = \int \langle 0, -g \rangle dt = \langle 0, -gt \rangle + \vec{C},$$

where $$\vec{C} = \langle C_1, C_2 \rangle$$ is a constant vector. We know that

$$\vec{v}(0) = \langle v_0 \cos(\theta), v_0 \sin(\theta) \rangle,$$

so we combine the two expressions:

$$\langle v_0 \cos(\theta), v_0 \sin(\theta) \rangle = \langle C_1, C_2 - g \cdot 0 \rangle = \langle C_1, C_2 \rangle.$$

We see that $$C_1 = v_0 \cos(\theta)$$ and $$C_2 = v_0 \sin(\theta)$$, so we have

$$\vec{v}(t) = \langle v_0 \cos(\theta), v_0 \sin(\theta) - gt \rangle.$$

Now let's find the position. Integrate again to get

$$ \vec{s}(t) = \int \vec{v}(t) dt = \langle t v_0 \cos(\theta), t v_0 \sin(\theta) - gt^2/2 \rangle + \vec{C},$$

where again $$\vec{C} = \langle C_1, C_2 \rangle$$ is some constant vector. Plug in $$t = 0$$ to get

$$ \langle x(0), y(0) \rangle = \langle C_1, C_2 \rangle,$$

so we put it all together and we get

$$ \vec{s}(t)  = \langle x(0) + t v_0 \cos(\theta), y(0) + tv_0 \sin(\theta) - gt^2/2 \rangle.$$

In other words, the $$x$$-position can be modeled by

$$x(t) = x(0) + t v_0 \cos(\theta),$$

and the $$y$$-position can be modeled by

$$y(t) = y(0) + tv_0 \sin(\theta) - gt^2/2.$$

We can also derive the equation for the speed at time $$t$$ and the displacement of the ball, but this is just an easy calculus exercise at this point.

# Arclength

Let's go back to geometry for a moment. [Remember](https://marshareb.github.io/Rec-Seven-Eight/) that we the length of a curve $$y = f(x)$$ on an interval $$[a,b]$$ is given by

$$ \int_a^b \sqrt{1 + f'(x)^2}dx.$$

The way we "derived" this was actually by pretending it was a parameterized curve already. If we consider the curve $$\vec{r}(t) = (x(t), y(t))$$, then our analysis showed us that the length of the curve on the interval $$[a,b]$$ should be something like

$$ \int_a^b \sqrt{x'(t)^2 + y'(t)^2}dt.$$

From our work prior, we know that we can write this as just

$$ \int_a^b \mid \vec{r}'(t) \mid dt.$$

In fact, this formula works in general. Going back to physical applications, if we know that the position of a particle can be modeled by the vector-valued function $$\vec{s}(t)$$, then the distance traveled over the interval $$[a,b]$$ is given by

$$ \int_a^b \mid \vec{s}'(t) \mid dt = \int_a^b \mid \vec{v}(t) \mid dt.$$

In other words, just integrate the speed from $$t=a$$ to $$t=b$$.
