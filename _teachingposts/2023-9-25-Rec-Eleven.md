---
layout: post
title: Recitation Eleven
tag: [MA1172]
---

In this recitation, we covered improper integrals.

# Improper Integrals

Essentially, an improper integral occurs when we have a vertical asymptote (the function is unbounded on the interval) or when one of the bounds of integration is $$\pm \infty$$. To deal with this, we need to break up the problem into smaller chunks and take limits. Suppose we are looking at

$$ \int_a^b f(x)dx.$$

The rule of thumb is the following:
- If $$f(x)$$ is unbounded at $$x=c$$, where $$a \leq c \leq b$$, then we write

$$ \lim_{\alpha \rightarrow c^-} \int_a^\alpha f(x)dx + \lim_{\beta \rightarrow c^+} \int_\beta^b f(x)dx.$$

- If $$f(x)$$ is unbounded at $$x=a$$, then we write

$$ \int_a^b f(x)dx = \lim_{\alpha \rightarrow a^+} \int_\alpha^b f(x)dx.$$

If $$f(x)$$ is unbounded at $$x=b$$, then we write

$$ \int_a^b f(x)dx = \lim_{\alpha \rightarrow b^-} \int_a^\alpha f(x)dx.$$

This also applies for when $$a = -\infty$$ or $$b = + \infty$$ (in which case we don't need to write the $$\pm$$ superscript).

- We repeat this procedure until all of the integrals under the limits are proper (i.e. the function is bounded on the interval and the bounds do not include $$\pm \infty$$.) Notice that we sometimes have to choose an arbitrary number to ensure we don't have a double limit on the integral; this may happen if the function is unbounded at $$x=a$$ and $$x=b$$. As long as the function is bounded for all $$a < x < b$$, we can choose any $$c$$ in this interval and write

$$ \int_a^b f(x)dx = \lim_{\alpha \rightarrow a^+} \int_a^c f(x)dx + \lim_{\beta \rightarrow b^-} \int_c^b f(x)dx.$$

As long as the limits are well-defined (meaning they converge to some number), then the choice of $$c$$ doesn't matter by the fundamental theorem of calculus: if $$F'(x) = f(x)$$, then

$$ \int_a^b f(x)dx = F(c) - \lim_{\alpha \rightarrow a^+} F(\alpha)  + \lim_{\beta \rightarrow b^-} F(\beta) - F(c) = \lim_{\beta \rightarrow b^-} F(\beta) - \lim_{\alpha \rightarrow a^+} F(\alpha).$$

If the limits do not exist, then this also happens independent of the choice of $$c$$, so we're allowed to pick our favorite.

If one of the limits doesn't exist in the above procedure or is equal to $$\pm \infty$$, then we say that the limit **diverges**. Otherwise, the limit **converges**.

Note this can sometimes lead to weird answers, but these integrals are important for physics/probability. For example, improper integrals are important for calculating probabilities involving the Gaussian distribution.

Important things to remember from this section are:
- identifying whether or not an integral is improper,
- writing out the integral as a sum of limits, and
- evaluating the integrals/limits you get at the end.

**Example:** Let's look at

$$ \int_{1}^\infty \frac{dx}{x-1}.$$

The function on the inside of the integral has a vertical asymptote at $$x=1$$, so we need to break up the integral based on that. There's also an $$\infty$$ in the bound, so we need to write this as a limit. Finally, there are no vertical asymptotes after $$x=1$$, so we can pick our favorite number between $$1$$ and $$\infty$$ to break up the integral. Let's choose $$x=2$$ as our break up point. We get

$$\int_1^\infty \frac{dx}{x-1} = \lim_{a \rightarrow 1^+} \int_a^2 \frac{dx}{x-1} + \lim_{b \rightarrow \infty} \int_2^b \frac{dx}{x-1}.$$

Now we use the fundamental theorem of calculus to get

$$\int_1^\infty \frac{dx}{x-1} = \ln(1) - \lim_{a \rightarrow 1^+}\ln(a-1)  + \lim_{b \rightarrow \infty} \ln(b - 1) - \ln(1).$$

Simplifying:

$$\int_1^\infty \frac{dx}{x-1} = + \lim_{b \rightarrow \infty} \ln(b - 1) - \lim_{a \rightarrow 1^+}\ln(a-1).$$

Now we see that $$\lim_{a \rightarrow 1^+} \ln(a-1) = \lim_{a \rightarrow 0^+} \ln(a) = -\infty$$ and $$\lim_{b \rightarrow \infty} \ln(b-1) = \lim_{b \rightarrow \infty} \ln(b) = \infty.$$ Since the limits are not finite, the integral diverges.

**Remark:** We could have done just one of the limits and noticed that it doesn't converge to a number and stopped.

**Example:** Let's look at

$$ \int_{-\infty}^\infty \sin(x)dx.$$

It's tempting to say that this integral is $$0$$ because for any $$a > 0$$ we have

$$ \int_{-a}^a \sin(x)dx = 0.$$

However, according to the definition of improper integrals, **we have to do the limits separately**. Following the definition, we choose our favorite value on the real line and break the integral up into two integrals. My favorite number is $$x=0$$, so

$$ \int_{-\infty}^\infty \sin(x)dx = \lim_{a \rightarrow -\infty} \int_a^0 \sin(x)dx + \lim_{b \rightarrow \infty} \int_0^b \sin(x)dx.$$

Now unlike last time, let's just evaluate one of the integrals. Notice that

$$ \lim_{a \rightarrow -\infty} \int_a^0 \sin(x)dx = \lim_{a \rightarrow -\infty}( -\cos(0) + \cos(a)) = \lim_{a \rightarrow -\infty} (\cos(a) - 1).$$

Does this converge? Let's take two different paths to $$-\infty$$ and see what happens. Notice that $$\lim_{n \rightarrow \infty} -2\pi n = -\infty$$ (here $$n \geq 1$$ a whole number), and so if this limit converged we would have

$$ \lim_{a \rightarrow -\infty} \cos(a) = \lim_{n \rightarrow \infty} \cos(-2\pi n) = 1.$$

On the other hand, we also have $$\lim_{n \rightarrow \infty} -(n \pi + \pi/2) = -\infty,$$ and $$\cos(- (n\pi + \pi/2)) = 0$$ for each $$n \geq 1$$ a whole number. So if this limit converged, we would have

$$ \lim_{a \rightarrow -\infty} \cos(a) = \lim_{n \rightarrow \infty} \cos(-(n\pi + \pi/2)) = 0.$$

Uh oh! If the limit did converge, I would have $$1 = 0$$. We see the limit doesn't converge (note this is also easy to see from a graph of cosine and you don't have to do as much work). Since one of the limits doesn't converge, we have that the integral diverges.


**Example:** Evaluate

$$ \int_{0}^{\pi/2} \tan(2x) \sec^4(2x)dx.$$

If we don't think about it, it looks like there's no vertical asymptotes because there is no denominator. However, remember that these trig functions are hiding something in the denominator. We have

$$ \tan(2x) = \frac{\sin(2x)}{\cos(2x)} \text{ and } \sec^4(2x) = \frac{1}{\cos^4(2x)}.$$

Now it's a little annoying to deal with this $$2x$$ on the inside, so let's get rid of that by doing a $$u$$-substitution. Let $$u = 2x$$, $$du = 2 dx$$. Then

$$ \int_{0}^{\pi/2} \tan(2x) \sec^4(2x)dx = \frac{1}{2}\int_0^{\pi} \tan(u) \sec^4(u)du = \frac{1}{2}\int_0^{\pi} \frac{\sin(u)}{\cos^5(u)}du.$$

Now on the interval $$[0,\pi],$$ we have that $$\cos(x) = 0$$ when $$x = \pi/2$$ (I recommend drawing a graph). So we need to break up our integral at this point. We write

$$ \int_0^{\pi/2} \tan(2x) \sec^4(2x)dx = \frac{1}{2} \left\{ \lim_{a \rightarrow (\pi/2)^-}\int_0^{a} \frac{\sin(u)}{\cos^5(u)}du + \lim_{b \rightarrow (\pi/2)^+}\int_b^{\pi} \frac{\sin(u)}{\cos^5(u)}du \right\}.$$

Let's look at just one of these limits. To evaluate the integral, we can do a $$u$$-substitution. Sadly I already used $$u$$, but let's use $$w$$ instead. Let $$w = \cos(u)$$, so $$dw = -\sin(w)dw$$. Then

$$ \int_0^a \frac{\sin(u)}{\cos^5(u)}du = \int_1^{\cos(a)} w^{-5}dw = -\frac{1}{4} w^{-4} \Big|_{w=1}^{\cos(a)}.$$

Notice it's okay to let the bounds depend on $$a$$ since this is fixed until the end. Plugging things in:

$$ \int_0^a \frac{\sin(u)}{\cos^5(u)}du = -\frac{1}{4} \cos(a)^{-4} + \frac{1}{4}.$$

Now we take a limit as $$a \rightarrow (\pi/2)^-$$. But cosine is in the denominator, and as $$a \rightarrow (\pi/2)^-$$ we see that this is blowing up to $$\infty$$. Since one of the limits blows up, the integral must be divergent, and we can stop.

**Example:** We've done a lot of divergent improper integrals, is there any chance that these integrals converge? Let's explore a family of examples. Let $$p > 0$$ (not necessarily a whole number) and look at

$$ \int_1^\infty \frac{dx}{x^p}.$$

This only problem can happen at $$x=0$$, which we are excluding from our domain of integration. It makes sense to write

$$ \int_1^\infty \frac{dx}{x^p} = \lim_{a \rightarrow \infty} \int_1^a \frac{dx}{x^p}.$$

Now we can use fundamental theorem of calculus to get two different answers depending on $$p$$: If $$p \neq 1$$, then we can use the power rule for integration to get

$$\int_1^\infty \frac{dx}{x^p} = \lim_{a \rightarrow \infty} \left[ \frac{x^{1-p}}{1-p} \Big|_{x=1}^a \right] = \lim_{a \rightarrow \infty} \frac{a^{1-p}}{1-p} - \frac{1}{1-p}.$$

If $$p = 1$$, then we have the one exception to the power rule for integration

$$\int_1^\infty \frac{dx}{x} = \lim_{a \rightarrow \infty} \left[ \ln(x) \Big|_{x=1}^a \right] = \lim_{a \rightarrow \infty} \ln(a) - \ln(1).$$

Notice we can already rule out $$p =1$$ as a possibility, since this limit is $$\infty$$. Thus, as long as $$p \neq 1$$, the integral is convergent if

$$ \lim_{a \rightarrow \infty} \frac{a^{1-p}}{1-p}$$

exists and is finite. We have two cases to think about. First, if $$p < 1$$, then $$1-p > 0$$, so there is some power of $$a$$ in the numerator. Taking the limit will have this converge to $$\infty$$, so we have to ignore $$0 < p < 1$$. Next, if $$p > 1$$, then $$1-p < 0$$, so $$\lim_{a \rightarrow \infty} a^{1-p} = 0$$. This tells us that the integral is convergent if and only if $$p > 1$$, and furthermore the answer is

$$\int_1^\infty \frac{dx}{x^p} = - \frac{1}{1-p} = \frac{1}{p-1}.$$

For example, if $$p =2$$ then we get that the integral is $$1$$ (and we finally have an example of a convergent improper integral).

**Example:** In the opposite direction, let's look at $$p > 0$$ a real number and the integral

$$ \int_0^1 \frac{dx}{x^p}.$$

Again, because of the power rule we have that the case $$p=1$$ is special, and so we should look at it separately. For $$p=1$$ we get

$$ \int_0^1 \frac{dx}{x} = \lim_{a \rightarrow 0^+} \int_a^1 \frac{dx}{x} = \lim_{a \rightarrow 0^+} \ln(1) - \ln(a) = \lim_{a \rightarrow 0^+} - \ln(a) = \infty.$$

So it is divergent. If $$p \neq 1$$, then the power rule tells us

$$ \int_0^1 \frac{dx}{x} = \lim_{a \rightarrow 0^+} \int_a^1 \frac{dx}{x} = \lim_{a \rightarrow 0^+} \left(\frac{1}{1-p} - \frac{a^{1-p}}{1-p} \right).$$

Now if $$p < 1$$, then $$1-p > 0$$, so $$\lim_{a \rightarrow 0^+} a^{1-p} = 0$$. We conclude that if $$p < 1$$, then the integral converges to $$1/(1-p)$$. If $$p > 1$$, then $$1-p < 0$$, and we get $$\lim_{a \rightarrow 0^+} a^{1-p} = + \infty$$, so the integral diverges. This gives us another family of convergent improper integrals.

**Remark:** These kinds of integrals are important for something called the [$$p$$-series test](https://en.wikipedia.org/wiki/Convergence_tests#p-series_test), which we will come back to later. We're starting to get into deep math!

**Warning:** There is something called [Cauchy's principal value](https://en.wikipedia.org/wiki/Cauchy_principal_value) which is a way of assigning values to certain divergent improper integrals (the idea is to bring the limit outside and use the same variable in both integrals). We are **not** learning this in class, however, integration calculators sometimes like to use this value when calculating improper integrals. For example, according to our definition of an improper integral, we have that

$$\int_{-1}^1 \frac{dx}{x}$$

diverges, since we can write this as

$$ \int_{-1}^0 \frac{dx}{x} + \int_0^1 \frac{dx}{x},$$

and we know from our prior example that the integral on the right diverges (so everything diverges). However, the Cauchy principal value of this integral is $$0$$ (in fact, the Cauchy principal value of an odd function over a symmetric interval is always zero). Calculators like Desmos will tell you this integral is $$0$$ because it is using this alternative definition (for some reason). You can see [here](https://www.wolframalpha.com/input?i=integral+from+-1+to+1+of+1%2Fx) that Wolfram Alpha avoids this issue. Interestingly, Desmos seems inconsistent about this. If you plug in

$$ \int_{-\infty}^\infty \frac{2x}{x^2+1}dx,$$

it tells you (correctly) that the integral is undefined, but the Cauchy principal value of this integral is $$0$$.

Looking at some [threads](https://www.reddit.com/r/desmos/comments/sdpdi0/bug_why_does_desmos_say_this_converges_its/), I've found some other bugs when it comes to Desmos. If you ask

$$ \int_3^\infty \frac{(2 + \cos(x))}{x}dx,$$

then Desmos will tell you this is zero. Notice this doesn't make any sense. Notice that $$-1 \leq \cos(x) \leq 1$$, so $$1 \leq 2 + \cos(x) \leq 3.$$ Hence for any $$a > 3$$, we have

$$ \int_3^a \frac{dx}{x} \leq \int_3^a \frac{2 + \cos(x)}{x} \leq \int_3^a \frac{3}{x}dx = 3 \int_3^a \frac{dx}{x}.$$

Notice that

$$ \int_3^a \frac{dx}{x} = \ln(a) - \ln(3).$$

If we take $$a \rightarrow \infty$$, this converges to $$+\infty$$, so by the squeeze theorem we should have

$$ \lim_{a \rightarrow \infty} \int_3^a \frac{2 + \cos(x)}{x} dx = \infty,$$

or, in other words, the integral doesn't converge. The moral of the story is that Desmos lies and we should not trust it for improper integrals.
