---
layout: post
title: Recitation Eighteen
tag: [MA1172]
---

In this recitation, we covered vectors and the dot product.

# Vectors

A long time ago you (should have) learned that a **point** is a location in the Cartesian plane, or, another way to put it, an [ordered tuple](https://en.wikipedia.org/wiki/Tuple). We write things like $$(1,2)$$ or $$(2,3,4)$$ to indicate locations on an $$xy$$-plane or an $$xyz$$-plane; see [this](https://en.wikipedia.org/wiki/Cartesian_coordinate_system) for more details. A vector, on the other hand, contains more information than a point. Very vaguely speaking, it is something that has **magnitude** and **direction**. One way of thinking about a vector is that it is not only telling you a location, but telling you how you got to that location. As a result, a vector takes two bits of information:
- a **tail**, which is a point representing the starting location, and
- a **tip**, which represents the ending location.
The **difference** of these two points (coordinate wise) is called a **vector**. For example, if our tail is $$(1,1)$$ and our tip is $$(1,2)$$, then the vector representing this is given by

$$ \langle 1-1, 2-1 \rangle = \langle 0, 1 \rangle.$$

Notice that the notation for a vector does not tell you what the tail and tip is. The notation is a bit unfortunate, but for calculations we generally don't care what these two points are -- the useful information is contained in their difference. While I won't be doing this in these notes, I will be discussing in person how vectors can be visualized or understood geometrically. See [this](https://www.youtube.com/watch?v=2_21erD-nBg) video for some more details on this. The other thing to point out is that vectors are written different from points -- we use parentheses for points and angled brackets for vectors.

The **dimension** of a vector is the number of components (or entries) that it has. For example, $$\langle 1,2 \rangle$$ is a two dimensional vector. A better way to say this, though, is that this is a vector in $$\mathbb{R}^2$$, which we think of as the collection of all two dimensional vectors.

Vectors are objects which have associated algebraic rules to them. Notice they are not numbers, but rather something new entirely. As a result, we have to memorize these new rules and take them into account when we are combining them. The two key operations to consider here are the following.
- Addition: Given vectors $$\langle a_1, \ldots, a_n \rangle$$ and $$ \langle b_1, \ldots, b_n \rangle$$, we can add them together to get a new vector:

$$ \langle a_1, \ldots, a_n \rangle + \langle b_1, \ldots, b_n \rangle = \langle a_1 + b_1, \ldots, a_n + b_n \rangle.$$

**Remember that adding vectors gives us a vector**.

- Scaling: Given a vector $$\langle a_1, \ldots, a_n \rangle$$ and a real number $$c$$, we can scale the vector by $$c$$ to get a new vector:

$$ c \cdot \langle a_1, \ldots, a_n \rangle = \langle ca_1, \ldots, ca_n \rangle.$$

**Remember that scaling a vector gives us a vector**. Also, people are sloppy with writing scaling -- they sometimes omit the dot.

The **magnitude** of a vector is its length (which you can calculate using the Pythagorean theorem). Given a vector $$\vec{v} = \langle a_1, \ldots, a_n \rangle$$, the magnitude is

$$ \mid \vec{v} \mid = \sqrt{\sum_{i=1}^n a_i^2}.$$

For example, the magnitude of $$\langle 1,2 \rangle$$ is $$\sqrt{1^2 + 2^2} = \sqrt{5}$$. You should check on your own that the magnitude of a vector is always bigger than or equal to zero, and the magnitude is equal to zero only when we have the zero vector.

A vector is called a **unit vector** if it has magnitude one (sometimes I'll say length or norm -- these things are all the same).

From a non-zero vector $$\vec{v}$$ we can construct a new vector $$\hat{u}$$ which is the **unit vector pointing in the direction of $$v$$**. We simply take our vector and divide it by its magnitude:

$$ \hat{u} = \frac{1}{\mid \vec{v} \mid} \cdot \vec{v}.$$

You should check that this is a unit vector (it's not a hard calculation). Two vectors are **parallel** if their associated unit vectors $$\hat{u}$$ and $$\hat{v}$$ satisfy

$$\hat{u} = \pm \hat{v}.$$

Let's focus on the case of two dimensions for a moment. Notice that a unit vector lives on the unit circle, which means that a unit vector always takes the form

$$ \vec{v} = \langle \cos(\theta), \sin(\theta) \rangle.$$

The angle $$\theta$$ is the **angle with the x-axis**. Notice that given $$\theta$$ and a magnitude $$r$$, we can completely recover a vector. This is what it really means by a vector is something with magnitude and direction.

# The Dot Product

The dot product is a magical formula that lets us calculate angles between vectors in higher dimensions. It comes in two flavors. First, given vectors $$\langle a_1, \ldots, a_n \rangle$$ and $$\langle b_1, \ldots, b_n \rangle$$, we say that the **dot product** between them is

$$ \langle a_1, \ldots, a_n \rangle \cdot \langle b_1, \ldots, b_n \rangle = \sum_{i=1}^n a_i b_i.$$

For example, $$\langle 1,2 \rangle \cdot \langle 0,1 \rangle = 1 \cdot 0 + 2 \cdot 1 = 2.$$

**Remember that the dot product between two vectors gives a number**.

It can be shown (using the [law of cosines](https://en.wikipedia.org/wiki/Law_of_cosines)) that the dot product also satisfies the following:

$$ \vec{v} \cdot \vec{w} = \mid \vec{v} \mid \cdot \mid \vec{w} \mid \cdot \cos(\theta),$$

where $$\theta$$ is the angle between them. The first formula is useful for actual calculation, but the second formula is useful for interpretation -- this allows us to find the angle between two vectors without having to really do any geometry. Also notice that with either interpretation, we see that the magnitude can be calculated using the dot product:

$$ \mid \vec{v} \mid = \sqrt{\vec{v} \cdot \vec{v}}.$$

Two vectors are said to be **orthogonal** if their dot product is zero.

Dot products are also useful because they let us calculate projections. Notice that a vector defines a line by scaling. The projection can be thought of as the "shadow" on this line. Alternatively, it is the amount you have to move along this line before you're "underneath" the vector. We've secretly used projections our whole lives -- projecting a vector onto the $$x$$-axis, or onto the vector $$\langle 1, 0 \rangle$$, is the same thing as just looking at the first coordinate. In a formula, the **orthogonal projection** of $$\vec{v}$$ onto a vector $$\vec{w}$$ is given by

$$\text{proj}_{\vec{w}}(\vec{v}) = \left( \frac{\vec{v} \cdot \vec{w}}{\vec{w} \cdot \vec{w}} \right) \vec{w}.$$

**Remember that the projection of a vector is a vector**.

The **scalar component** of a vector $$\vec{v}$$ is given by

$$ \text{scal}_{\vec{w}}(\vec{v}) = \frac{\vec{v} \cdot \vec{w}}{\mid \vec{w} \mid}.$$

Finally, the **orthogonal decomposition** of a vector $$\vec{v}$$ is given by

$$ \vec{v} = \text{proj}_{\vec{w}}(\vec{v}) + (\vec{v} - \text{proj}_{\vec{w}}(\vec{v})).$$
