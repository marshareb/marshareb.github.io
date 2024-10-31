---
layout: post
title: Recitation Three
tag: [MA1172]
---

In this recitation, we covered all of the problems from the "Area Between Curves" worksheet, along with Ximera problems 13 from "Area between curves" and 24 from "A review of integration."


# Weierstrass Substitution

I'll briefly go over the Weiestrass substitution (named after [Karl Weiestrass](https://en.wikipedia.org/wiki/Karl_Weierstrass)). The idea is that we wish to integrate

$$ \int_0^{\pi/2} \frac{dx}{3 + \cos(x)}.$$

Notice that a $$u$$-sub is not helpful here, and we can't do it directly, so we'll need to do something else. One trick is to try letting $$t = \tan(x/2)$$. Notice that if we draw a right triangle with angle $$x/2$$, opposite side $$t$$, and adjacent side $$1$$, we can find that the hypotenuse has length $$\sqrt{t^2 + 1}$$ (using the Pythagorean theorem) and we have

$$ \sin(x/2) = \frac{t}{\sqrt{t^2 + 1}}, \ \ \cos(x/2) = \frac{1}{\sqrt{t^2 + 1}}.$$

Next, we wish to figure out what $$\cos(x)$$ and $$\sin(x)$$ are (this is important because the integral has a $$\cos(x)$$ term). To do so, we'll use the [half-angle identity](https://trigidentities.info/trig-half-angle-identities/). Admittedly, this is one I don't have memorized and have to look up, but it is surprisingly useful (I figure it out on the fly using [Euler's formula](https://en.wikipedia.org/wiki/Euler%27s_formula), but there's a less technical way of doing it). The identity says

$$ \sin(x) = 2 \cos(x/2) \sin(x/2).$$

Substituting this in, we get

$$ \sin(x) = \frac{2t}{t^2 + 1}.$$

Next, using the Pythagorean theorem again, we get

$$ \sin^2(x) + \cos^2(x) = 1,$$

so

$$ \cos^2(x) = 1 - \frac{4t^2}{(t^2 + 1)^2} = \frac{t^4 + 2t^2 + 1 - 4t^2}{(t^2 + 1)^2} = \frac{(t^2 - 1)^2}{(t^2 + 1)^2}.$$

Taking the square root of both sides,

$$ \cos(x) = \frac{t^2 - 1}{t^2 + 1} = \frac{\sqrt{(t^2-1)^2}}{t^2 + 1}.$$

You might be wondering why I didn't take the square root of the top. The problem is that in the interval $$0 \leq t \leq 1$$ we have $$t^2 - 1 \leq 0$$. I'm leaving the square root until we know the sign.

If I'm going to use the substitution $$t = \tan(x/2)$$, I'm going to need to figure out what $$dt$$ is in terms of $$dx$$. Taking the derivative of both sides of my substitution, I have

$$dt = \frac{\sec^2(x/2)}{2} dx = \frac{dx}{2\cos^2(x/2)}.$$

Using my earlier identity, I get

$$ \frac{2 dt}{t^2 + 1} = dx.$$

Finally, I need to change the bounds in my integration. If $$x = 0$$, then $$t = \tan(0/2) = 0$$, and if $$x= \pi/2$$, then $\tan(\pi/4) = 1$$. So:

$$  \int_0^{\pi/2} \frac{dx}{3 + \cos(x)} = \int_0^1 \frac{2 dt}{(t^2 + 1)\left(3 -  \frac{t^2-1}{t^2 + 1}\right)}.$$

Notice the minus that pops up since $$0 \leq t \leq 1$$. Let's simplify a bit:

$$ \int_0^1 \frac{2dt}{3t^2 + 3 - t^2 + 1} = \int_0^1 \frac{2dt}{2t^2 + 4} = \int_0^1 \frac{dt}{t^2 + 2} = \frac{1}{2} \int_0^1 \frac{dt}{(t/\sqrt{2})^2 + 1}.$$

Let $$u = t/\sqrt{2}$$, so $$dt = \sqrt{2} du$$. If $$t = 0$$, then $$u=0$$, and if $$t = 1$$ then $$u = 1/\sqrt{2}$$. We get

$$ \frac{1}{\sqrt{2}} \int_0^{1/\sqrt{2}} \frac{du}{u^2 + 1} = \frac{1}{\sqrt{2}} \arctan(u) \bigg|_{u=0}^{1/\sqrt{2}} = \frac{\arctan(1/\sqrt{2})}{\sqrt{2}}.$$

Substitutions like this will come up when we get into the "trig substitution" section.

# Area Between Curves

If a function $$f(x)$$ is positive on an interval $$[a,b]$$, that is, $$f(x) \geq 0$$ for $$a \leq x \leq b$$, then recall that the definite integral is the area under the curve. However, if $$f(x)$$ is negative, then the definite integral will be the negative of the area under the curve. To find the unsigned area under a curve, we have to break up when a function is positive and negative and evaluate the definite integral on those intervals.

**Problem:** Find the total area between the curve $$y = x^2-1$$ and the $$x$$-axis on the interval $$[-2,2]$$.

**Solution:** Let's figure out when the function $$f(x) = x^2-1$$ is zero. Notice

$$ 0 = x^2 - 1 \iff x^2 = 1 \iff x = \pm 1.$$

Notice that $$f(x)$$ is a polynomial, so in particular it is continuous. Recall that the [intermediate value theorem](https://en.wikipedia.org/wiki/Intermediate_value_theorem) tells us that the only way a *continuous* function can go from positive to negative (or vice versa) is if it is zero inbetween. If we want to figure out when $$f(x)$$ is positive and negative on the interval $$[-2,2]$$, we just need to choose test points in the intervals $$[-2, -1)$$, $$(-1,1)$$, $$(1,2].$$ Remember a *test point* is just any point in that interval -- they will all tell us the same answer.

Let's choose the test points $$x = -3/2 = -1.5$$, $$x = 0$$, and $$x = 1.5$$. We see that

$$f(-1.5) = (-1.5)^2 - 1 > 0,$$

$$ f(0) = 0^2 - 1 = -1 < 0,$$

$$f(1.5) = (1.5)^2 - 1 > 0.$$

Remember I'm not interested in the actual value of the function at these points, I'm just interested in whether or not it is positive or negative.

The above tells us that $$f(x)$$ is positive on the intervals $$[-2, -1) \cup (1, 2]$$ and negative on the interval $$(-1,1)$$. To find the total area between the curve and the $$x$$-axis, we evaluate

$$ \int_{-2}^{-1} f(x)dx - \int_{-1}^1 f(x)dx + \int_1^2 f(x)dx.$$

Now let's use the fundamental theorem of calculus. We calculate

$$ \int (x^2-1)dx = \frac{x^3}{3} - x + C.$$

So one antiderivative of $$f(x)$$ is $$F(x) = \frac{x^3}{3} - x.$$ The fundamental theorem of calculus then tells us

$$ \int_{-2}^{-1} f(x)dx - \int_{-1}^1 f(x)dx + \int_1^2 f(x)dx = F(-1) - F(-2) - F(1) + F(-1) + F(2) - F(1)$$

which simplifies to

$$ \text{Area} = 2 F(-1) + F(2) - 2F(1) - F(-2).$$

Going to our favorite calculator, we find

$$ \text{Area} = 2 \left(\frac{2}{3} \right) + \frac{2}{3} - 2 \left(- \frac{2}{3} \right) - \left(- \frac{2}{3} \right) = 4.$$

Notice that we've just found the area between a curve $$y=f(x)$$ and $$y=0$$ by evaluating

$$ \int_{a}^b \mid f(x) - 0 \mid dx.$$

This is, in fact, how we do it in general. Given two curves $$y= f(x)$$ and $$y= g(x)$$, we find the area between them on the interval $$[a,b]$$ by evaluating

$$ \int_a^b \mid f(x) - g(x) \mid dx.$$

In general, this will involve us breaking up integrals into smaller integrals, evaluating them, and then adding the answers up.

**Problem:** Consider the region given by

<p align="center">
  <img src="https://ximera.osu.edu/mooculus/areasBetweenCurves/exercises/exerciseList/areasBetweenCurves/exercises/setUpAreaBothWays2-figure0.svg" />
</p>

Set up the integral for the area of the region with respect to $$x$$.

**Solution:** This picture is misleading, as I pointed out in recitation. It looks like there's only two functions, given by the blue curve and the red curve. However, there's actually three functions. Remember that the relationship

$$x^2 + y^2 = 1$$

does not define a function (it fails the vertical line test). However, if we consider the pair of functions

$$ y = \sqrt{1 - x^2} \text{ and } y = - \sqrt{1-x^2},$$

then we get the same region. The semicircle above the $$x$$-axis is given by $$y = \sqrt{1-x^2}$$ and the semicircle below the $$x$$-axis is given by $$y = -\sqrt{1-x^2}$$. So if we set up the integral for the area with respect to $$x$$, we have to integrate from $$x=-1$$ to the point where $$y=x$$ and $$y = - \sqrt{1-x^2}$$ intersect. To figure out what the $$x$$-value is, we set them equal to eachother:

$$ - \sqrt{1-x^2} = x \implies 1 - x^2 = x^2 \implies 1 = 2x^2 \implies x = \pm \frac{1}{\sqrt{2}}.$$

Using the graph, we know that this intersection happens when $$x < 0$$, so we must have that they intersect at $$x = - \frac{1}{\sqrt{2}}.$$ Our bounds so far are from $$x=-1$$ to $$x = -1/\sqrt{2}$$, but we see we have one final bound we need to figure out. This happens when $$\sqrt{1- x^2} = x$$, which happens at $$x= 1/\sqrt{2}$$. So the integral will be

$$ \int_{-1}^{-1/\sqrt{2}} [(\sqrt{1-x^2}) - (- \sqrt{1-x^2})] dx + \int_{-1/\sqrt{2}}^{1/\sqrt{2}} [(\sqrt{1-x^2}) - x]dx.$$
