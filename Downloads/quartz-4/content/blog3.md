---
title: Blog Post 3 - An Exercise in Geodesics
---

Welcome to my next blog post! I've been promising for a few weeks now to get into the details of the geodesic equation, which governs how objects move through curved spacetime, so let's handle that today. In particular, I'm going to present a step-by-step derivation to come to the geodesic equation, which, as I was reading, helped me understand why the geodesic equation takes the form it does. It's not quite a *proof*, as it isn't fully formalized, but I would think of it more as a convincing argument. This will be a more technical, in-depth blog post, but I think it's worth going over given how important understanding the motion of geodesics will be to our project.

# Formalizing Geodesics

As a brief recap of what we covered last week, a geodesic is an "unaccelerated" path that a particle might take—that is, the free-fall trajectory of a particle. (When we say "unaccelerated," we are ignoring all forces **except** gravity, since Einstein argues that gravity does not act on particles as an external force but rather is a feature of the geometry of spacetime.) Thinking back to classical physics, we might naively write that the equation of motion of a geodesic is $\vec a = 0$, or
$$
\Large \displaystyle \frac{d \vec v}{dt} = 0
$$

This is all the geodesic equation really is! And in Newtonian mechanics, it's usually enough to stop there—given the position function $\vec x(t) = (x(t), y(t), z(t))$ of a particle, we can solve for its entire trajectory (noting that $\vec v = \frac{d \vec x}{dt}$), and in this simple case we would find that it would travel in a straight line at constant velocity (as Newton's First Law would imply). But as we try to generalize this to arbitrary, non-flat spacetimes, what changes?

Well, the first change we must make to generate our geodesic equation has less to do with geometry and more to do with relativity; in relativity, time is no longer an independent, global entity that ticks at a constant rate for all observers, but rather a feature of the frame of reference an observer is in; that is, time becomes a dimension on the same footing as space, and in fact is a part of the coordinate system. As our geometry of spacetime warps, not only will our spatial coordinates warp, so too will our time coordinate. This has two implications: firstly, time $t$ is no longer a useful quantity by which we can parameterize our trajectory, since the rate at which time changes (you can think of this as "the rate at which a clock ticks") might vary from point to point along the trajectory. Secondly, because of this fact, we must now include time as a coordinate when describing our trajectory $\vec x$.

Instead of parameterizing via $t$, we will use as our parameter the proper time $\tau$. The proper time is merely the time experienced by an observer in its own frame (i.e, the frame in which it is stationary). This proper time must necessarily tick at the same rate throughout for the observer in question, since it appears at rest with respect to itself. (There is an edge case that will become important later in our project—photons do not experience time, so proper time is meaningless! We'll examine this more closely when we get to it, but the short answer is that we'll be using a different paramter $\sigma$ instead of proper time $\tau$). Making these modifications, our trajectory can be expressed as $\vec x(\tau) = (t(\tau), x(\tau), y(\tau), z(\tau))$. One last notational change: it is often convention, so that one can sum over numerical indices, to give each of these 4 dimensions of spacetime numerical identifiers, so we can instead express our trajectory as $\vec x(\tau) = (x^0(\tau),x^1(\tau),x^2(\tau),x^3(\tau))$. (We start with time and label it $0$ so that, by convention, the nonzero indices can represent spatial indices.)

# Deriving an Equation of Motion
So why is it enough to stop at the above equation in Newtonian mechanics, and why do we have to be more careful when involving curved spacetimes? This has to do with a rather subtle point about the nature of the **basic vectors** in which we define our coordinate system.

Let's back up a little. Convince yourself first that we can write our velocity vector $\vec v$ as
$$
\Large \displaystyle \vec v = v^{\alpha} \vec e_{\alpha}
$$
First of all, note the use of the Einstein convention (the Einstein convention, which I introduced in Blog Post 1, is super important! A lot of the equations I write from now on will be quite confusing if you don't understand it.): here, the term on the right is a sum of $v^{\alpha} \vec e_{\alpha}$ from $\alpha = 0$ to $3$. Also note that I've used a Greek letter $\alpha$ as my index, instead of Latin letter; you may recall that by convention, the use of Greek letters means that time *is* included as an index, and so we sum from 0 instead of 1.

What this equation is saying, then, is that given some representation $\vec x(\tau) = (x^0(\tau),x^1(\tau),x^2(\tau),x^3(\tau))$, this corresponds to a vector in physical space by multiplying each component of this vector with a corresponding vector that we call a **basis vector**, and we have one basis vector for each dimension ($\vec e_0$ being the basis vector for time, $\vec e_1$ being the basis vector for the first spatial direction, etc.). An important technical side note, if you're curious: it's crucial that the set of basis vectors are **linearly independent**—this means that no linear combination of basis vectors can return another basis vector. This in turn implies that any vector that can be represented using these basis vectors has a **unique representation**, and so the mapping of sets of numbers $(x^0(\tau),x^1(\tau),x^2(\tau),x^3(\tau))$ to points in physical space is a 1-to-1 mapping.

Now, in classical mechanics, we would simply find from our above geodesic equation $\vec a = 0$ that
$$
\Large \displaystyle \frac{d \vec v}{dt} = \frac{d}{dt} \left(v^i \vec e_i\right) = 0
$$
(Note that I've used $i$ since this is a classical equation.) But because the basis vectors are not functions of time, we can factor them out of the derivative and get that $\vec e_i \frac{d}{dt} v^i = 0$. Now, since our basis vectors are linearly independent, for this sum to be zero, the coefficients of every basis vector must be 0; therefore, for each value of $i$ it is true that
$$
\Large \displaystyle \frac d{dt} v^i = 0
$$
That is, the geodesic equation in classical mechanics is that objects have constant velocity, which is exactly what we expected. So what changes in general relativity? Simply put, **the basis vectors are not constant along the geodesic**. Because space can be arbitrarily warped, the coordinates that we considered basis vectors continuously deform along our curved surface. Expressing $\vec v$ as $v^{\alpha} \vec e_{\alpha}$ now to denote a relativistic geodesic, we get the following:
$$
\Large \displaystyle \frac{d \vec v}{d \tau} = \frac d{d\tau} \left(v^{\alpha} \vec e_{\alpha}\right) = v^{\alpha} \frac {d \vec e_{\alpha}}{d\tau} + \frac {d v^{\alpha}}{d\tau} \vec e_{\alpha} = 0
$$
Having expanded our time derivative using the product rule, we can express it as shown above in terms of both how components of velocity change over the trajectory, *as well as* how the basis vectors themselves (that is, the geometry of spacetime) changes throughout the trajectory. This second term is fairly straightforward; it can be computed as long as we know the rate of change of a component of velocity. The first term, however, might seem more foreign. How can we conceptualize the rate of change of the coordinate system itself?

# The Christoffel Symbol

The answer is something called a Christoffel symbol. First of all, it may help to apply to expand that term and pick out some familiar features:
$$
\Large \displaystyle \frac {d \vec e_{\alpha}}{d x^{\beta}} \frac {d x^{\beta}}{d \tau} = v^{\beta} \frac {d \vec e_{\alpha}}{d x^{\beta}}
$$
Using the multivariable chain rule to express the rate of change of the basis vectors as a sum, we can see that it depends on how the basis vectors change with the trajectory's coordinates, and how those coordinates change with the proper time of the trajectory (which is just the velocity components!) The nice thing about expressing the rate of change of basis vectors with respect to a coordinate is that this depends only on the geometry of spacetime, and *not* on a particular trajectory, and so we can very generally compute these values, which are known as the **Christoffel symbols**, denoted by $\Gamma$. In particular, a particular Christoffel symbol is defined as
$$
\Large \displaystyle \frac {d \vec e_{\alpha}}{d x^{\beta}} = \Gamma^{\mu}_{\; \; \alpha \beta} \vec e_{\mu}
$$
In other words, **the Christoffel symbol $\Gamma^{\mu}_{\; \; \alpha \beta}$ denotes the rate of change of $\vec e_{\alpha}$ with respect to $x^{\nu}$ in the direction of $\vec e^{\mu}$**.

If we rewrite our above equation in terms of Christoffel symbols, and use the fact that $v^{\alpha} = \frac d{dt} x^{\alpha}$, we arrive at the most common form of the geodesic equation
$$
\Large \displaystyle \frac {d^2 x^{\mu}}{d\tau^2} +  \Gamma^{\mu}_{\; \; \alpha \beta} \frac{d x^{\alpha}}{d \tau} \frac{d x^{\beta}}{d \tau} = 0
$$
which is true for each $\mu$.

All that's left is computing the Christoffel symbols themselves. This blog post has already grown a little bloated, so we won't go into figuring this out from scratch, but hopefully it should make sense that the Christoffel symbols, which have to do with how the basis vectors defining a coordinate system change as you move around a spacetime, are entirely determined by the **metric tensor** we discussed in the last blog post, since the metric tensor fully characterizes the geometry of a space. Specifically, the Christoffel symbols come out to be
$$
\Large \displaystyle \Gamma^{\mu}_{\; \; \alpha \beta} = \frac 12 g^{\mu \sigma} \left( \frac{\partial}{\partial x_{\beta}} g_{\sigma \alpha} + \frac{\partial}{\partial x_{\alpha}} g_{\sigma \beta} - \frac{\partial}{\partial x_{\sigma}} g_{\alpha \beta} \right)
$$
What's important to note is that they depend not directly on the metric tensor itself, but rather its derivatives, which makes sense (it quantifies how the metric tensor changes in particular directions). The Christoffel symbols are crucial to general relativity, and help conceptualize how a space changes along a trajectory.

If you didn't understand all the math above, that's alright! This was certainly a denser blog than usual. The key takeaway is that there exists an equation which, when given *only* a **metric** that describes the geometry of a spacetime, allows one to compute what **geodesic trajectories** through that spacetime look like (i.e, what curved paths objects will appear to follow). Next week, we'll begin getting into the actual meat of the project, where we'll be attempting to compute these geodesics (for photons, specifically) around a given metric (that of a black hole with certain properties).

Tune into the next post as we'll finally begin talking about how black hole imaging connects with all of this!

# Sources
- Misner, Thorne, and Wheeler. *Gravitation*. Princeton University Press. 1973.
- Carroll, Sean. *Spacetime and Geometry*. Cambridge University Press. 2003.