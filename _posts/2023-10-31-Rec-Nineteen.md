---
layout: post
title: Recitation Nineteen
tag: [MA1172]
---

In this recitation, we covered more on the dot product.

# Dot Product

Recall from the previous notes that if we are given $$\vec{v} = \langle v_1, \ldots, v_n \rangle$$ and $$\vec{w} = \langle w_1, \ldots, w_n \rangle$$, then

$$ v \cdot w = \sum_{i=1}^n v_i w_i = \mid \vec{v} \mid \cdot \mid \vec{w} \mid \cdot \cos(\theta),$$

where $$\theta$$ is the angle between the vectors. The idea behind the "proof" of this fact is the [law of cosines](https://en.wikipedia.org/wiki/Law_of_cosines) and using the fact that

$$ \vec{v} \cdot \vec{v} = \sum_{i=1}^n v_i^2 = \mid \vec{v} \mid^2.$$

Here is the "proof": We can form a triangle with sides $$\vec{v}, \vec{w}$$ and $$\vec{v} - \vec{w}$$. The law of cosines then tells us

$$ \mid \vec{v} - \vec{w} \mid^2 = \mid \vec{v} \mid^2 + \mid \vec{w} \mid^2 - 2 \mid \vec{v} \mid \cdot \mid \vec{w} \mid \cdot \cos(\theta).$$

On the other hand, we know that

$$ \mid \vec{v} - \vec{w} \mid^2 = (\vec{v} - \vec{w}) \cdot (\vec{v} - \vec{w}) = \mid \vec{v} \mid^2 - 2 \vec{v} \cdot \vec{w} + \mid \vec{w} \mid^2.$$

Combining these two facts, we get

$$ \vec{v} \cdot \vec{w} = \mid \vec{v} \mid \cdot \mid \vec{w} \mid \cdot \cos(\theta),$$

as desired.

Using the above relation, we can come up with the [Cauchy-Schwarz inequality](https://en.wikipedia.org/wiki/Cauchy%E2%80%93Schwarz_inequality). Notice that

$$ \mid \vec{v} \cdot \vec{w} \mid = \mid \vec{v} \mid \cdot \mid \vec{w} \mid \cdot \mid \cos(\theta) \mid \leq \mid \vec{v} \mid \cdot \mid \vec{w} \mid.$$

We also only have equality when $$\cos(\theta) = \pm 1$$.

Recall that two vectors are **orthogonal** if the angle between them is $$\pi/2$$ and it is **parallel** if the angle is $$0$$ or $$\pi$$. Since $$\cos(\pi/2) = 0$$, being orthogonal is the same thing as saying

$$ \vec{v} \cdot \vec{w} = 0.$$

Next, let's notice that given two vectors $$\vec{w}$$ and $$\vec{v}$$, we can create a new vector (called the **orthogonal projection**) by considering

$$ \text{proj}_{\vec{w}}(\vec{v}) := \frac{\vec{v} \cdot \vec{w}}{\vec{w} \cdot \vec{w}} \vec{w}.$$

By construction, this vector is parallel to $$\vec{w}$$ as long as $$\vec{v} \cdot \vec{w}$$ is not zero. Notice we can rewrite this as

$$ \text{proj}_{\vec{w}}(\vec{v}) := \frac{\vec{v} \cdot \vec{w}}{\vec{w} \cdot \vec{w}} \vec{w} = \left(\frac{\vec{v} \cdot \vec{w}}{ \mid \vec{w} \mid } \right) \left( \frac{\vec{w}}{\mid \vec{w} \mid} \right).$$

In other words, we're scaling the unit vector $$ \vec{w}/ \mid \vec{w} \mid$$ by $$\frac{\vec{v} \cdot \vec{w}}{ \mid \vec{w} \mid }$$. We define the **scalar projection** of $$\vec{v}$$ onto $$\vec{w}$$ as this amount that we are scaling the unit vector by:

$$ \text{scal}_{\vec{w}}(\vec{v}) = \frac{\vec{v} \cdot \vec{w}}{ \mid \vec{w} \mid }.$$

# Examples

**Example:** Let $$\vec{v} = \langle 3, -6 \rangle$$ and $$\vec{w} = \langle 3, 5 \rangle$$. We have

$$ \vec{v} \cdot \vec{w} = 9 - 30 = -21.$$

Notice that

$$ \mid \vec{v} \mid = \sqrt{45} \text{ and } \mid \vec{w} \mid = \sqrt{34},$$

so

$$ -21 = \vec{v} \cdot \vec{w} = \sqrt{45} \cdot \sqrt{34} \cdot \cos(\theta).$$

To find the angle between them, we simply have

$$ \theta = \text{arccos} \left( - \frac{21}{\sqrt{45} \cdot \sqrt{34}}\right).$$

**Example:** Let $$\vec{v} = \langle 1,2,1 \rangle$$ and $$\vec{w} = \langle 0, 1, 2 \rangle$$. We see that

$$ \vec{v} \cdot \vec{w} = 0 + 2 + 2 = 4.$$

We also have

$$ \mid \vec{w} \mid = \sqrt{5},$$

so

$$ \text{scal}_{\vec{w}}(\vec{v}) = \frac{4}{\sqrt{5}},$$

and

$$ \text{proj}_{\vec{w}}(\vec{v}) = \frac{4}{\sqrt{5}} \langle 0, \frac{1}{\sqrt{5}}, \frac{2}{\sqrt{5}} \rangle.$$

**Example:** Suppose we know that $$\text{scal}_{\vec{v}}(\vec{u}) = 0$$, and $$\vec{v}$$ and $$\vec{u}$$ are non-zero. This means that

$$ \vec{v} \cdot \vec{u} = 0,$$

which implies that the vectors are orthogonal.
