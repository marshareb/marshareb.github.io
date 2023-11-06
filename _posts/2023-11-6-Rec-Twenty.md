---
layout: post
title: Recitation Twenty
tag: [MA1172]
---

In this recitation, we covered a little on matrices and the cross-product.

# Matrices

Credit to Wikipedia and Ximera for the images.

There is a lot to say about matrices which we will not do right now. For us, a **matrix** is an ordered tuple of vectors. So for example, if we have the vectors $$\vec{v} = \langle 2,1 \rangle$$ and $$\vec{w} = \langle 1,1 \rangle$$, then we can form a matrix $$M = (\vec{v}_1, \vec{v}_2)$$. You can think of the columns of a matrix as vectors. We generally write it out in rows and columns, so the above matrix would be written as

$$ M = \begin{pmatrix} 2 & 1 \\ 1 & 1 \end{pmatrix}.$$

There's no reason I stopped at writing a $$2 \times 2$$ matrix (or a tuple of two vectors in $$\mathbb{R}^2$$) except that it is convenient for writing. You can do this for all kinds of vectors, and the representation is the same.

We are interested in studying the **determinant** of a matrix. Abstractly, the determinant is the signed "volume" of the "parallelepipied spanned by the vectors." In higher dimensions, this falls apart without more definitions and language, but this at least makes sense in dimensions two and three. Taking two vectors, the parallelogram spanned by them is easy enough to draw.

![](https://ximera.osu.edu/mooculus/calculus2TextbookBySection/crossProductsSection/crossProducts/digInCrossProducts-figure0.svg)

Suppose the vectors corresponding to this parallelogram are given by $$\vec{v} = \langle a,b \rangle$$ and $$\vec{w} = \langle c,d \rangle$$. The trick for finding the area is to find the area of the rectangle containing the parallelogram, and then subtract off the corresponding smaller areas. Here is a nice visualization of what I mean.

![](https://ximera.osu.edu/mooculus/calculus2TextbookBySection/crossProductsSection/crossProducts/digInCrossProducts-figure1.svg)

In this case, the total area is $$(a+c)(b+d) = ab + ad + cb + cd$$. There are two purple regions, each with area $$ \frac{ab}{2},$ two orange regions, each with area $$cb$$, and two green regions, each with area $$\frac{cd}{2}$$. Combining it, we can find that the area of the parallelogram spanned by $$\vec{v}$$ and $$\vec{w}$$ is given by

$$ ab + ad + cb + cd - 2\left( \frac{ab}{2} + cb + \frac{cd}{2}\right) = ad - bc.$$

So the determinant of the matrix $$M = (\vec{v}, \vec{w})$$ will be $$ad - bc$$.

For higher dimensions, the trick is harder but doable. I'll spoil it for three dimensions and just tell you the formula:

$$ \text{Det} \begin{pmatrix} a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \\ c_1 & c_2 & c_3 \end{pmatrix} = a_1 (b_2c_3 - b_3c_2) - a_2(b_1c_3 - b_3c_1) + a_3(b_1c_2 - b_2c_1).$$

This is the (signed) volume of the parallelepipied spanned by these three vectors. See [this](https://math.libretexts.org/Bookshelves/Linear_Algebra/A_First_Course_in_Linear_Algebra_(Kuttler)/03%3A_Determinants/3.02%3A_Properties_of_Determinants) and [this](https://math.libretexts.org/Bookshelves/Linear_Algebra/A_First_Course_in_Linear_Algebra_(Kuttler)/03%3A_Determinants) for more details on the determinant.

# Cross Product

Using the determinant, we're going to define the cross product. This is a way of multiplying $$3 \times 3$$ vectors. This operation takes two vectors and gives out a vector. The abstract first definition is that the cross product is

$$ \langle a_1, a_2, a_3 \rangle \times \langle b_1, b_2, b_3 \rangle = \text{Det} \begin{pmatrix} \vec{i} & \vec{j} & \vec{k} \\ a_1 & a_2 & a_3 \\ b_1 & b_2 & b_3 \end{pmatrix}.$$

Here, we're using determinant as a shorthand for the abstract formula described above. Technically speaking, we're being a little sloppy by mixing vectors in with numbers for a matrix, but what we're really trying to say is

$$ \langle a_1, a_2, a_3 \rangle \times \langle b_1, b_2, b_3 \rangle = \langle a_2 b_3 - a_3 b_2, b_1 a_3 - a_3 b_1, a_1 b_2 - a_2 b_1 \rangle.$$

For example,

$$ \langle 1,2,3 \rangle \times \langle 1,1,1 \rangle = \langle (2)(1) - (3)(1), -( (1)(1) - (3)(1)), (1)(1) - (2)(1) \rangle = \langle -1, 2, -1 \rangle.$$

Notice that

$$\langle 1,2,3 \rangle \cdot \langle -1, 2, -1 \rangle = 0 \text{ and } \langle 1,1, 1 \rangle \cdot \langle -1, 2, -1 \rangle = 0.$$

This is the important property of the cross product -- **it gives a vector which is orthogonal to both of the original vectors**! Let's check this in general. Notice that

$$\langle a_2 b_3 - a_3 b_2, b_1 a_3 - a_3 b_1, a_1 b_2 - a_2 b_1 \rangle \cdot \langle a_1, a_2, a_3 \rangle = a_1a_2b_3 - a_1a_3b_2 + a_2b_1a_3 - a_3a_2b_1 + a_3a_1b_1 - a_3a_2b_1 = 0.$$

The same thing works for the other vector!

Notice that given two vectors, they span either a line or a plane. If they span a plane, then there are two options for a (unit) vector which is orthogonal to them; if you stand above this plane, this vector either points towards you or away from you. The difference between these vectors is a minus sign, and so is not too significant in the long run of mathematics, but we need to make a cohesive choice. The choice that mathematicians made a long time ago is the **right hand rule**, namely that if you make your pointer finger on your right hand $$\vec{v}$$ and your middle finger on your right hand $$\vec{w}$$, then $$\vec{v} \times \vec{w}$$ (which will be orthogonal to both) must point in the direction of your thumb. This gives us an easy and uniform way of deciding the direction of $$\vec{v} \times \vec{w}$$ without having to make calculations.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/d/d2/Right_hand_rule_cross_product.svg/330px-Right_hand_rule_cross_product.svg.png)

Finally, the last thing we need to know about the cross product is that it satisfies a geometric formula which is similar to the dot product. We have

$$\mid \vec{v} \times \vec{w} \mid = \mid \vec{v} \mid \cdot \mid \vec{w} \mid \cdot \sin(\theta),$$

where $$\theta$$ is the angle between $$\vec{v}$$ and $$\vec{w}$$.
