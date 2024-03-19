---
title: Blog Post 1 - General Relativity
---

Hey everyone! Thanks for tuning into this next blog post; it’s a pretty long background one, so buckle up!

In this first post after the introduction, I’m going to go through a lot of the background reading on general relativity I’ve been doing recently (much of it from the textbooks *Gravitation*, by Wheeler, Misner, and Thorne, and *Spacetime and Geometry*, by Sean Carroll). General relativity is going to be a key foundational aspect of my senior project (black holes are, after all figments of general relativity; they don’t appear in classical physics at all!), so it’s worth laying some groundwork and getting it right.

General relativity, if you’re unfamiliar, is the theory that Einstein came up with in order to explain the various issues and inexplicable errors that the Newtonian description of gravity was returning—most famously, one related to the precession of Mercury’s orbit over time. There were deeper, more philosophical issues with general relativity too—Newton himself remarked in his original description of gravity how odd and unsettling it was that gravity acted seemingly instantly, with no delay. Einstein’s description of gravity sought to fix this and many of the other issues plaguing Newtonian gravity.

How exactly does Einstein’s gravity differ from Newton’s? In a great number of ways, but in one most important regard: Newtonian gravity is an explanationless, “hand-wavy” law that provides an inverse-square law that simply works, without providing any mechanism or underlying structure. Einstein’s gravity, on the other hand, provides a deeper reason for gravity’s existence: a “fictitious” force emerging from the geometry of spacetime itself. We’ll explore further what it means for a force to be fictitious or not, but for now what’s important is that general relativity is almost purely a **geometric** theory, leaving very little arbitrariness in the final result.

# The Equations of General Relativity

How, specifically, does general relativity describe the motion of objects using nearly only geometry? Well, in the words of John Archibald Wheeler: **“Matter tells spacetime how to curve, and curved spacetime tells matter how to move.”** Not only is this a succinct explanation of general relativity (the distribution of matter and energy in the universe determines the geometry of spacetime, and in turn the geometry of spacetime determines how the matter distribution evolves!), but the two clauses of the quote perfectly identify and distinguish the two key equations of general relativity: the **field equation** and the **geodesic equation**.

$$
\begin{align}
\color{#ed5a40} \Large \displaystyle R_{\mu \nu} + \frac 12 Rg_{\mu \nu} - \Lambda g_{\mu \nu} = \frac{8 \pi G}{c^4} T_{\mu \nu} \, \, \, \, \, &\rbrace  \, \, \, \, \ \text{Field Equation} \\
\color{#4287f5} \Large \displaystyle \frac{d^2 x^{\mu}}{ds^2} + \Gamma ^{\mu}_{\alpha \beta} \frac{dx^{\alpha}}{ds} \frac{dx^{\beta}}{ds} = 0 \, \, \, \, \, &\rbrace  \, \, \, \, \ \text{Geodesic Equation}
\end{align}
$$

Don’t be too intimidated by these equations yet! We’ll explain them in great depth soon enough.

# Tensors

You might notice the above equations involve a lot of funny-looking quantities with 1 to 3 different indices that are on the top, bottom, or both, like $R_{\mu \nu}$, $g_{\mu \nu}$, $T_{\mu \nu}$, $\Gamma ^{\mu}_{\; \; \alpha \beta}$, $x^{\alpha}$, and so on. These objects are **tensors**. Tensors are very useful mathematical structures that are central to general relativity. In some sense, tensors are a generalization of vectors: vectors are an array of values, while tensors can be a multidimensional array of values—while vectors have only one index, tensors can have arbitrarily many. But much like vectors, at least in physics, are a deeper concept than merely a list of values, tensors are also somewhat more complicated.

**Above all, a tensor is an object that transforms like a tensor.**

Okay, perhaps not all that helpful. Let’s try that again.

Consider a scalar field: what this means is that every point in space (and time) is associated with a single scalar (a number). Note that this representation does not depend on the coordinate system we use. If we shift our coordinate system, even if the numbers we use to describe certain points are different, we expect the same “physical point” to correspond to the same scalar value. Thus, scalars are invariant under a change in coordinate system. This coordinate invariance is a really important and very desirable quality for a mathematical object to have, since there is no “natural” or “correct” coordinate system—particularly in general relativity, where the coordinate system itself may be continuously changing as the fabric of spacetime adjusts to the current matter distribution. Thus, when physicists say “tensors are objects that transform like tensors,” it isn’t circular reasoning; what they mean is that tensors are multidimensional arrays that obey the following transformation law (which guarantees this “coordinate invariance”):

$$
\Large \displaystyle T^{\alpha ,...}_{\quad \; \; \beta ,...} = \sum_{\alpha' ,..., \beta' ,...} T^{\alpha' ,...}_{\quad \; \; \; \beta' ,...} \frac{\partial x^{\alpha}}{\partial x^{\alpha'}} ... \frac{\partial x^{\beta'}}{\partial x^{\beta}} ...
$$

If the equation above confuses you, essentially: when you transform a tensor from some coordinate system $(x^{\alpha'}, x^{\beta'}$ to some system $(x^{\alpha}, x^{\beta}$, its value remains unchanged. Another confusion you might have: what’s going on with the superscripts and the subscripts? The answer is that tensors can have **contravariant** (superscripted) indices or **covariant** (subscripted) indices. We won’t go into the geometric nuances characterizing the difference between the two, but the basic premise is that covariant indices transform in the same way that the basis coordinates transform, while contravariant indices transform in the opposite manner. The important property that contravariant and covariant indices have is that they **contract**: when summing over a tensor with a contravariant index times one with the same covariant index, the two indices contract and are no longer a free index, as shown below:


$$
\Large \displaystyle \sum_a T^{a}_{\; \; b} K_a = T'_b
$$

Here, the index $a$ was summed over and subsequently contracted.

The last important note about tensors is something called the **Einstein convention**. When tensors are contracted with one another, it is very common to sum over certain “repeated indices,” such as those shown in the above two equations. This is often a great hassle, and so Albert Einstein popularized the convention of simply ommitting the summation symbol, and leaving it implicit than any repeated index is to be summed over. (Einstein facetiously referred to this convention as his “greatest contribution to physics”—it certainly saves a lot of writing!)

# The Field Equation

$$
\Large \displaystyle R_{\mu \nu} + \frac 12 Rg_{\mu \nu} - \Lambda g_{\mu \nu} = \frac{8 \pi G}{c^4} T_{\mu \nu}
$$

The first clause of Wheeler’s quote explains the field equation: **“Matter tells spacetime how to curve.”** Einstein’s field equation describes the relationship between the matter/energy distribution of a region of spacetime, and the curvature of that region. (An important note: although the field equation looks quite beautiful and compact—and it is beautiful!—its compactness is somewhat misleading; with two “dummy” indices, $\mu$ and $\nu$, the single field equation actually contains 16 different equations, one for each value of $\mu$ and $\nu$, which can each take on a value from 0 to 3. It’s also worth noting that of these 16 equations there are only 10 unique ones, due to symmetry conditions on the relevant tensors). In particular, the right hand side of the equation describes the matter distribution; the tensor $T_{\mu \nu}$, or the **stress-energy tensor**, encodes all the necessary information about the matter distribution of the region. The left hand side, however, is all about geometry. The most important quantity to note, by far, is the **metric tensor** $g_{\mu \nu}$. We’ll dive further into the metric tensor in future posts, since it’s central to the geodesic equation, which is the equation that’s more important for our project, but for the moment what’s important to know is that somehow this tensor $g_{\mu \nu}$ encodes the geometry of space.

What about the rest of the left hand side then? Are $R_{\mu \nu}$, $R$, and $\Lambda$ separate quantifiers of geometry? Well, $\Lambda$ is the cosmological constant, and it essentially quantifies the strength of dark energy. Dark energy is a sort of “hack” in general relativity to replicate the negative pressure density required to produce the sort of accelerating expansion of the universe that we’ve observed, but since in this project we’ll be dealing with relatively small physical setups (black holes), rather than with large-scale cosmology, we’re going to ignore $\Lambda$ and set $\Lambda = 0$. The remaining two quantities, it turns out, depend directly on $g_{\mu \nu}$—both are measures of “curvature”, and $g_{\mu \nu}$ completely describes the shape of spacetime, so all relevant information about curvature can be extracted. Specifically, the tensor that completely quantifies curvature, the Riemann tensor $R_{\mu \nu \sigma}^{\quad \; \, \rho}$, can be derived solely from the metric tensor to be:

$$
\large \displaystyle R_{\mu \nu \sigma}^{\quad \; \, \rho} = \frac 12 g^{\zeta \rho} \left(\frac{\partial}{\partial x^{\nu}} \frac{\partial}{\partial x^{\sigma}} g_{\mu \zeta}
+ \frac{\partial}{\partial x^{\mu}} \frac{\partial}{\partial x^{\zeta}} g_{\nu \sigma} - \frac{\partial}{\partial x^{\nu}} \frac{\partial}{\partial x^{\zeta}} g_{\mu \sigma}
- \frac{\partial}{\partial x^{\mu}} \frac{\partial}{\partial x^{\sigma}} g_{\nu \zeta} \right)
$$

Note the use of the Einstein convention here: the repeated index $\zeta$ is being implicitly summed over. Another interesting thing note to make is that the Riemann tensor consists solely of second partial derivatives of the metric tensor: this makes intuitive sense; as you may remember from your single-variable calculus class, curvature is entirely a feature of the second derivative of a function. From the Riemann tensor, which contains all information about curvature, $R_{\mu \nu}$ (the Ricci tensor) and $R$ (the Ricci scalar) can be computed, according to the following relations:

$$
\Large \displaystyle R_{\mu \nu} = R_{\mu \sigma \nu}^{\quad \; \, \sigma}
$$

$$
\Large \displaystyle R = g^{\mu \nu} R_{\mu \nu}
$$

(Once again, note the use of the Einstein convention.)

What we’ve shown here is that the entire left hand side of Einstein’s field equation depends only on the shape of spacetime (that is, on the metric tensor), while the right hand side depends only on the matter/energy distribution of spacetime (that is, on the stress-energy tensor). Therefore, the field equation relates the **curved spacetime** ($g^{\mu \nu}$) to the **matter** within it ($T^{\mu \nu}$), thus fulfilling Wheeler’s claim that **“matter tells spacetime how to curve.”**

I hope this has been a convincing and at least somewhat enlightening introduction to the mathematics of general relativity, and to Einstein’s field equation. We did a lot of handwave-y mathematical explanations here, and I haven’t even close to done justice to much of the mathematical rigor behind these concepts, but hopefully this has been an adequate introduction to the concept for our purposes. We will not be explicitly using the field equation in this project; rather, we will begin with a metric tensor $g_{\mu \nu}$ that was already derived from the field equation, from a given mass distribution, and then derive some interesting and potentially novel properties from it.

Stay tuned for that in the future! (And in the more immediate future, a blog post going into more depth on the geodesic equation as well.)

# Sources
- Misner, Thorne, and Wheeler. *Gravitation*. Princeton University Press. 1973.
- Carroll, Sean. *Spacetime and Geometry*. Cambridge University Press. 2003.