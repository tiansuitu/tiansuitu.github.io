---
layout: durrett
title: "Lemma 2.2.13: Poisson Tails, Truncation, and Cesàro Means (WIP)"
date: 2026-11-05
permalink: /durrett-waffling/lemma-2-2-13-poisson-truncation-cesaro/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "Working notes on applying Durrett's tail-integral lemma to discrete distributions, filling in the truncation calculation on p. 55, and understanding the continuous Cesàro mean argument."
---

## Lemma 2.2.13

Note that Lemma 2.2.13, although using integration, it holds true for discrete (non-negative) random variables $Y$: Suppose $Y$ is $Po(\lambda)$, then

- $\forall y\in \mathbb R, P(Y>y)=\displaystyle\sum_{x=\max\{0,\lfloor y \rfloor+1\}}^\infty\frac{e^{-\lambda}\lambda^x}{x!}$
- $\forall y\in \mathbb R, P(Y\geq y)=\displaystyle\sum_{x=\max\{0,\lceil y \rceil\}}^\infty\frac{e^{-\lambda}\lambda^x}{x!}$

$$
\int_0^\infty py^{p-1}
\sum_{x=\lfloor y\rfloor +1}^\infty\frac{e^{-\lambda}\lambda^x}{x!}
dy
$$

---

$$
\int_0^\infty py^{p-1} P(Y>y)dy
=
\int_0^\infty py^{p-1}
\sum_{x=\lfloor y\rfloor+1}^\infty\frac{e^{-\lambda}\lambda^x}{x!}
dy
$$

$$
\int_0^\infty py^{p-1} P(Y\geq y)dy
=
\int_0^\infty py^{p-1}
\sum_{x=\lceil y\rceil}^\infty\frac{e^{-\lambda}\lambda^x}{x!}
dy
$$

(Lesbesgue) integration (with Lesbesgue measure so $dy$)... WIP

*Notation correction only: the sums in these two integrals need integer lower bounds, $\lfloor y\rfloor+1$ and $\lceil y\rceil$, rather than $y+1$ and $y$. In the bullet points, the $\max\{0,\cdot\}$ keeps the Poisson support correct also when $y<0$.*

This is going from WLLN triangular arrays to NO moment assumptions but with $xP(\lvert X_i\rvert>x)\to 0$

Filling in the details, starting from p.55, note that Lemma 2.2.13 only applies for nonnegative random variables like $\lvert\bar X_{n,1}\rvert$, and in this case $p=2$:

$$
E[\bar X_{n,1}^2]=E[\lvert\bar X_{n,1}\rvert^2]
=\int_0^\infty 2y P(\lvert X_{1} \mathbf{1}\{\lvert X_{1}\rvert\leq n\}\rvert> y) dy
$$

$$
=\int_0^n 2y P(\lvert X_{1}\rvert \mathbf{1}\{\lvert X_{1}\rvert\leq n\}> y)dy
+
\int_n^{+\infty} 2y P(\lvert X_{1}\rvert \mathbf{1}\{\lvert X_{1}\rvert\leq n\}> y)dy
$$

$$
=
\int_0^n 2y P(\{\lvert X_{1}\rvert \mathbf{1}\{\lvert X_{1}\rvert\leq n\}> y\}\cap\{\lvert X_{1}\rvert\leq n\})dy
+
\int_0^n 2y P(\{\lvert X_{1}\rvert \mathbf{1}\{\lvert X_{1}\rvert\leq n\}> y\}\cap\{\lvert X_{1}\rvert> n\})dy
$$

$$
=
\int_0^n 2y P(\{\lvert X_{1}\rvert> y\}\cap\{\lvert X_{1}\rvert\leq n\})dy
+
\int_0^n 2y P(\{0> y\}\cap\{\lvert X_{1}\rvert> n\})dy
$$

$$
=
\int_0^n 2y P(y< \lvert X_{1}\rvert\leq n)dy
+
0
$$

$$
=
\int_0^n 2y[P(\lvert X_{1}\rvert> y)-P(\lvert X_1\rvert>n)]dy
$$

$$
\leq
\int_0^n 2yP(\lvert X_{1}\rvert> y)dy
$$

It is claimed that

$$
y\to \infty\implies yP(\lvert X_1\rvert>y) \to 0
$$

implies

$$
\frac{1}{n}\int_0^n 2yP(\lvert X_1\rvert>y)dy \to 0
$$

so the intuition in the book is that as $y\to\infty$,

$$
g(y):= 2yP(\lvert X_1\rvert>y)\to 0
$$

so then $1/n$ at front is like averaging the $g(y)$ over $[0,n]$. But to me this does not clearly explains why INTEGRATING something going to zero as $n\to +\infty$ (so domain for which integrates is enlarging) will lead to zero, as the area itself for finite $y$ is non zero and included when integrating from $0$ to $n\to \infty$.

| Discrete Cesàro mean | Continuous Cesàro mean |
|---|---|
| $a_n\to0$ | $g(y)\to0$ as $y\to\infty$ |
| $\displaystyle \frac1n\sum_{k=1}^n a_k\to0$ | $\displaystyle\frac1n\int_0^n g(y)\,dy\to0$ |

Both rely on the same idea: the finite initial part becomes negligible after normalization, while the remaining terms are uniformly small.

**TO BE COMPLETED**
