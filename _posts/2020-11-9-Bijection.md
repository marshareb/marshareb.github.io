---
layout: post
title: Bijection Between Open Interval and Half Open Interval
tag: set-theory
categories: ["Set Theory"]
---

In this post, we discuss a basic set theory problem.

## Bijection between half open interval and closed interval

One day I'll get back to writing blog posts about my research, however another fun set theory problem was brought to my attention. I have never actually seen the solution to this before, although I think I've implicitly used it without thinking about it. The questions asks whether there is a bijection between $$[0,1]$$ and $$[0,1)$$ and asks how to construct it.

The idea that I came up with (that seems to agree with others, see for example [here](https://math.stackexchange.com/questions/28568/bijection-between-an-open-and-a-closed-interval)) is to start by just picking some point. So let $$f : [0,1) \rightarrow [0,1]$$ be the bijection, and let's set $$f(1/2) = 1$$. The issue now is we need a point which maps to $$1/2$$, so we set $$f(1/4) = 1/2$$. The issue continues like this, so set $$f(1/2^{n+1}) = 1/2^n$$. Since this is an infinite sequence which stays entirely in $$[0,1)$$, we have that this gives us a bijection on the level of these points. Finally, for all other points we just set $$f(x) = x$$. This gives us the desired bijection.

Notice how this trick works in general. If you want to make a bijection between $$f : (0,1) \rightarrow [0,1]$$, just take two sequences which don't overlap and repeat the same trick. Notice as well that in the construction of this bijection we've basically preserved no interesting properties about either $$(0,1)$$ or $$[0,1]$$. For example, on the level of topology this bijection is for sure not a homeomorphism (proof why: if we remove any point from $$(0,1)$$ it is no longer a connected set, but we can remove $$0$$ from $$[0,1]$$ and it is still a connected set).
