---
layout: post
title: Metrization and Flows
tag: functional-analysis dynamics
categories: ["Weekly Update", "Dynamics"]
---

This week was mostly focused on getting back into the flow of things (pun intended). I'll break this post up into a dynamical part and a functional analysis part.

## Dynamics

The past few weeks I've read some of Katok's "Modern Dynamics," book casually, but this week was centered on applying things that I've learned. Of particular interest
was the special flow, suspension flow, and linear flows.

To review briefly, a dynamical system consists of three components: 

(1) Some space with whatever structure is of interest (in most of my exercises, this was a smooth manifold). We denote the space
by $$X$$.

(2) Some function $$f : X \rightarrow X$$ preserving the structure of the space (smooth map, in the case of a smooth manifold). 
Thinking phyiscally, this function maybe represents movement.

(3) A time variable, which is either going to be discrete or continuous. 

In the case of discrete dynamical systems, we measure time through iterations of our function; i.e., time 0 correpsonds to $$ f^{(0)} = \text{Id}$$,
time 1 corresponds to $$ f^{(1)} = f$$, time 2 corresponds to $$f^{(2)} = f \circ f$$, and so on and so forth. If our function is invertible, we can represent
"negative" time with iterates of the inverse. 

In the case of continuous dynamical systems, we introduce the notion of a flow. A flow is a map $$ F : X \times \mathbb{R} \rightarrow X$$ which measures the location of the object $$x \in X$$ at time
$$t \in \mathbb{R}$$ along the flow $$F$$. The one requirement we put on flows is that they satisfy a group composition law. This just means that $$F(F(x,t),s) = F(x,t+s)$$, or in other words if I measure
where the object is at time t, then follow the flow until time s, its the same as just following the flow for time t + s. 

One might wonder if there is a way to relate discrete time dynamical systems with continuous time dynamical systems. In particular, for every discrete time dynamical system, can I find a 
unique continuous time dynamical system which represents it? I am unsure of the answer to this question (though surely I'll come back to it). However, I did explore some methodologies for
assigning discrete time dynamical systems to continuous time dynamical systems.

Given a flow $$F$$, the natural trick to associating a discrete time dynamical system to this continuous time dynamical system is to just 
choose a time $$t_0$$ and iterate that point. So we assign the map $$ f(x) = F(x,t_0)$$, and we see that we get the discrete time dynamical system
$$ f^{(n)}(x) = F(x,nt_0)$$. If this is not clear, just take one iterate and then use induction to get the formula; $$ f^{(2)}(x) = f \circ f (x) = F(F(x,t_0),t_0) = F(x,2t_0)$$ by the group composition law.

The issue is that this method doesn't capture everything of interest to us. A point is periodic if there exists some integer $$k$$ so that $$f^{(k)}(x) = x$$, $$k > 1$$ (for $$k=1$$, we call this a fixed point instead).
Say $$x$$ is a point of period $$k$$, and examine the orbit of the map at the point $$x$$, $$\mathcal{O}_f = \{f^{(k)}(x) : k \in \mathbb{Z}\}$$. By construction, $$1 < |\mathcal{O}_f(x)| < \infty$$ (the orbit is finite but not fixed).
Notice that the group composition law says 

$$f^{(k)} \circ F(x,t) = F(F(x,t),kt_0) = F(x, t + kt_0) = F(F(x,kt_0),t) = F(f^{(k)}(x),t) = F(x,t).$$ 

So every point $$ x \in \mathcal{O}_f(x)$$ is also a periodic point. Thus, if our dynamical system
$$ f: X \rightarrow X$$ has an isolated periodic point, we cannot construct it from a flow in this fashion.

So we see that this global method has local issues. To get around this, we can use a local method to construct discrete time dynamical systems (however, these systems only act locally as a result). This method is 
by Poincare first return maps. It is a little techical, but in essence what we do is take a transverse manifold to a point
$$x$$ on our manifold, and then construct (locally) a discrete dynamical system by sending points on this local neighborhood to where the flow intersects this transverse manifold. Taking a small enough neighborhood $$U$$, we have
a map $$F_N : U \rightarrow U$$. 

The question of going the other way is given by suspension and special flows. Consider the manifold $$X$$ ad some discrete time dynamical system $$ f$$ on this manifold (let it be a diffeomorphism for this case). 
We construct a suspension manifold by taking the product $$X \times [0,1]$$ and quotienting it by $$(x,1) \sim (f(x),0)$$. This gives us a manifold $$X_f$$ called the suspension manifold. On this suspension manifold, we can construct
a suspension flow $$\sigma_f^t$$, which is just the linear flow determined by $$ \frac{\partial}{\partial t}$$ on $$X_f$$.

The special flow follows a similar definition, except we introduce a cutoff map $$h : X \rightarrow \mathbb{R}_{\geq 0}$$. Instead of the product, we construct the manifold

$$X_h = \{(x,t) : x \in X, t \in \mathbb{R}, 0 \leq t \leq h(x)\}.$$

We then take the quotient $$(x,h(x)) \sim (f(x), 0)$$ to get the manifold $$X_{f,h}$$. The special flow is then determined by the vertical vector field on this manifold. Notice that the suspension flow is a special case of the special flow with cutoff function given by 
$$h(x) = 1$$.

The remark is that the suspension flow for the circle rotation $$R_\alpha : S^1 \rightarrow S^1$$ determined by $$R_\alpha(x) := x + \alpha \pmod{1}$$ is smoothly conjugate to the linear flow on $$\mathbb{T}^2 = S^1 \times S^1,$$ which can be seen by just noting that the suspension manifold is 
diffeomorphic to the torus and the flows are conjugate via affinely translating everything back into place before the rotation.

## Functional Analysis

This has mostly been reading chapter 1 of Rudin's, "Functional Analysis." Essentially a review of basic topological concepts as well as some linear algebra.
The more interesting thing has been the metrization theorem, which can be concisely stated as follows: "A topological vector space $$X$$ admits a countable local base iff it is metrizable," where metrizable
means that there is some metric which generates the topology on the vector space. The backwards direction is clear (just take balls centered at 0 with radius $$1/n$$) but the forward direction takes a great deal of effort. I'll post Rudin's proof of this later.