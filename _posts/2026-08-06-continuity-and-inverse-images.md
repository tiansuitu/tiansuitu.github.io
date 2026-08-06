---
title: "Continuity and Inverse Images"
date: 2026-08-06
permalink: /durrett-waffling/continuity-and-inverse-images/
tags:
  - durrett-waffling
excerpt: "Informal working notes on lower semicontinuity, motivated by Exercise 1.3.5."
---

*These are informal working notes, questions, and thoughts as I read Durrett.*

## Some kind of continuity versus openness/closedness of inverse images of a function

Motivated by **Exercise 1.3.5**.

So, review: suppose $x_0\in f^{-1}(O)$. To show that $f^{-1}(O)$ is open, we need to find some $\delta_{x_0}>0$ such that

$$
B_{\delta_{x_0}}(x_0)\subseteq f^{-1}(O).
$$

I want the definition to be defined from a more intuitive, engineering perspective. We know that $f$ is continuous if $f(x_n)$ goes to $f(x)$ as $x_n$ goes to $x$, so a first intuitive try at coming up with the definition—assuming we do not already know the epsilon-delta language of lower semicontinuity—is sequential.

We guess

$$
\liminf_{y\to x} f(y) \geq f(x)
\iff
\sup_{n\in\mathbb N}\inf_{m\geq n} f(y_m)\geq f(x)
$$

for all

$$
y_m\to x
$$

as $m\to\infty$.

I am guessing the idea is that, for usual continuity,

$$
x_n\approx x \implies f(x_n)\approx f(x).
$$

Now it is directional or signed, with an allowable large difference in the output: as we get close enough in the domain to some target $x$, the function output is not too much less than $f(x)$:

$$
x_n\approx x \implies f(x_n)\gtrapprox f(x).
$$

Once $y$ is sufficiently close to $x$, $f(y)$ cannot remain $\epsilon$ or more below $f(x)$. Basically, it cannot be too much lower than $f(x)$:

$$
\forall\epsilon>0,\ \exists\delta>0:
|y-x|<\delta \implies f(y)>f(x)-\epsilon.
$$

It is not

$$
f(y)>f(x)+\epsilon \implies f(y)>f(x),
$$

because that requires too much—as if $f(y)$ must be above $f(x)$, or as if there must be upward jumps. We only require the looser condition

$$
f(y)>f(x)-\epsilon,
$$

which allows

$$
f(y)<f(x).
$$

## Working notes and questions

I think $f(y)>f(x)-\epsilon$ is easier to interpret in human terms than $f(y)+\epsilon>f(x)$, although they express a similar idea.

Another way to understand it—although this is **not equivalent**—is to compare:

1. The usual non-directional condition:

   $$
   |f(y)-f(x)|<\epsilon.
   $$

2. A directional condition: $f(y)$ can still be below $f(x)$, just not too far below it:

   $$
   f(y)<f(x).
   $$

Combining these two conditions gives

$$
f(y)-f(x)<0
\implies
f(x)-f(y)<\epsilon
\iff
f(y)>f(x)-\epsilon.
$$

Of course, this only helps with intuition; it is not an if-and-only-if relationship:

$$
\bigl[|f(y)-f(x)|<\epsilon\bigr]
\land
\bigl[f(y)<f(x)\bigr]
\not\Longleftarrow
f(y)>f(x)-\epsilon.
$$

Questions I still have:

- Why not just use $\lim_{n\to\infty}f(y_n)\geq f(x)$? What is the purpose of all the infimum and supremum machinery?
- Unlike ordinary continuity, this only prevents nearby values from falling substantially below $f(x)$; arbitrarily large upward jumps are permitted. What does this really mean? How should I understand the similar statement on Wikipedia?
- Why does the definition use

  $$
  \liminf_{y\to x}f(y)\geq f(x)
  $$

  rather than the strict inequality

  $$
  \liminf_{y\to x}f(y)>f(x)?
  $$
