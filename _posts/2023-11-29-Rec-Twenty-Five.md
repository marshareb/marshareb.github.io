---
layout: post
title: Recitation Twenty Five
tag: [MA1172]
---

In this recitation, we covered partial derivatives and the gradient.

# Partial Derivatives and Gradient

Given a function of several variables $$F : \mathbb{R}^n \rightarrow \mathbb{R}$$, we can define its **partial derivative** with respect to a variable as the derivative assuming the other variables are fixed. So if we had a function $$F(x,y)$$, we can find its partial derivative with respect to $$x$$ as

$$ \frac{\partial F}{\partial x}(x,y) = \lim_{h \rightarrow 0} \frac{F(x+h, y) - F(x,y)}{h}.$$

For example, consider the function $$F(x,y) = 2x^2y + x.$$ If we wished to take its partial derivative, we would get

$$ \frac{\partial F}{\partial x}(x,y) = 4xy + 1,$$

since we just treat $$y$$ like a constant and take the derivative with respect to $$x$$. Now all of calculus as you know it applies!

The **gradient vector** is the vector of partial derivatives: if $$F : \mathbb{R}^n \rightarrow \mathbb{R}$$ is of the form $$F(x_1, \ldots, x_n)$$, then

$$ \nabla F := \langle \frac{\partial F}{\partial x_1}, \ldots, \frac{\partial F}{\partial x_n} \rangle.$$

The only really "hard" part of this section of the course is problems involving contour plots. A **contour plot** is a plot of different level curves for a function of several variables (remember that the level curves are where the function is constant). Using the contour plot and some additional information, one can figure out estimates for the partial derivatives. The advice for this part is to try imagining the plot in higher dimensions and try to picture what is happening with the $$z$$-axis as you move in the direction of the partial derivative. 
