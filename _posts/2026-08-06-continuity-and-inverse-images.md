---
layout: durrett
title: "Some kind of Continuity vs. Openness/Closedness of Inverse Images of a Function"
date: 2026-08-06
permalink: /durrett-waffling/continuity-and-inverse-images/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "Informal notes on lower semicontinuity, motivated by Exercise 1.3.5."
---

Motivated by **Exercise 1.3.5.**

So review: suppose $x_0\in f^{-1}(O)$, then to show $f^{-1}(O)$ open, we need to find some $\delta_{x_0}>0$ such that

$$
B_{\delta_{x_0}}(x_0)\subseteq f^{-1}(O).
$$

I want the definition to be defined from a more intuitive engineering perspective. We know $f$ is continuous if $f(x_n)$ goes to $f(x)$ as $x_n$ goes to $x$, so a first intuitive try to come up with the definition by staring at the question is sequential, assuming we do not know the epsilon-delta kind of language of the definition of l.s.c.

We guess

$$
\liminf_{y\to x} f(y) \geq f(x) \iff
\sup_{n\in \mathbb N}\inf_{m\geq n} f(y_m)\geq f(x)
$$

for all

$$
y_m\to x
$$

as $m\to \infty$.

So, guessing the idea is just that for usual continuity,

$$
x_n\approx x \implies f(x_n)\approx f(x).
$$

Now it is directional signed, with allowable large difference in output: as we get close enough in the domain to some $x$ target, the function output is not less than...

$$
x_n \approx x \implies f(x_n) \gtrapprox f(x).
$$

Once $y$ is sufficiently close to $x$, $f(y)$ cannot remain $\epsilon$ **or more** below $f(x)$. So basically, it cannot be too much lower than $f(x)$:

$$
\forall \epsilon>0, \exists \delta>0: |y-x|<\delta \implies f(y) > f(x) -\epsilon.
$$

So you see it is not

$$
f(y) > f(x) + \epsilon \implies f(y) > f(x),
$$

because that requires too much, as if $f(y)$ must be above $f(x)$, as if **there must be upward jumps**. We only require the looser $f(y) > f(x) -\epsilon$, which allows

$$
f(y)<f(x).
$$
