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

Although Lemma 2.2.13 is expressed as an integral, it also applies to nonnegative discrete random variables. For example, suppose $Y\sim\operatorname{Poisson}(\lambda)$. For every $y\in\mathbb R$,

$$
\begin{aligned}
\mathbb P(Y>y)
  &= \sum_{x=\max\{0,\lfloor y\rfloor+1\}}^\infty
       \frac{e^{-\lambda}\lambda^x}{x!},\\[6pt]
\mathbb P(Y\ge y)
  &= \sum_{x=\max\{0,\lceil y\rceil\}}^\infty
       \frac{e^{-\lambda}\lambda^x}{x!}.
\end{aligned}
$$

In particular, for $p>0$,

$$
\begin{aligned}
\mathbb E[Y^p]
  &= \int_0^\infty p y^{p-1}\,\mathbb P(Y>y)\,\mathrm{d}y\\
  &= \int_0^\infty p y^{p-1}
     \left(\sum_{x=\lfloor y\rfloor+1}^\infty
       \frac{e^{-\lambda}\lambda^x}{x!}\right)\,\mathrm{d}y.
\end{aligned}
$$

Alternatively, writing the integrand with $\mathbb P(Y\ge y)$ gives the same integral, since the two tails differ only at integer values of $y$:

$$
\begin{aligned}
\mathbb E[Y^p]
  &= \int_0^\infty p y^{p-1}\,\mathbb P(Y\ge y)\,\mathrm{d}y\\
  &= \int_0^\infty p y^{p-1}
     \left(\sum_{x=\lceil y\rceil}^\infty
       \frac{e^{-\lambda}\lambda^x}{x!}\right)\,\mathrm{d}y.
\end{aligned}
$$

Here $\mathrm{d}y$ denotes integration with respect to Lebesgue measure. **WIP.**

*Notation: the summation bounds must be integers, namely $\lfloor y\rfloor+1$ and $\lceil y\rceil$. In the two tail-probability formulas, $\max\{0,\cdot\}$ also accounts for $y<0$.*

## Truncation and the weak law

This is the step from the triangular-array WLLN to a weak law without a moment assumption, under the tail condition $x\,\mathbb P(|X_1|>x)\to0$ as $x\to\infty$.

Filling in the details (starting from p. 55), let

$$
A_n=\{|X_1|\le n\},
\qquad
\bar X_{n,1}=X_1\mathbf 1_{A_n}.
$$

Lemma 2.2.13 applies to the nonnegative random variable $|\bar X_{n,1}|$ with $p=2$. Since $|\bar X_{n,1}|\le n$, the tail integrand vanishes for $y\ge n$, giving

$$
\begin{aligned}
\mathbb E[\bar X_{n,1}^{\,2}]
  &= \mathbb E[|\bar X_{n,1}|^2]\\
  &= \int_0^\infty
       2y\,\mathbb P(|\bar X_{n,1}|>y)\,\mathrm{d}y\\
  &= \int_0^n
       2y\,\mathbb P(|X_1|\mathbf 1_{A_n}>y)\,\mathrm{d}y.
\end{aligned}
$$

For $0<y<n$, partitioning the event according to $A_n$ and $A_n^c$ yields

$$
\begin{aligned}
&\mathbb P(|X_1|\mathbf 1_{A_n}>y)\\
&\quad= \mathbb P(\{|X_1|\mathbf 1_{A_n}>y\}\cap A_n)
       +\mathbb P(\{|X_1|\mathbf 1_{A_n}>y\}\cap A_n^c)\\
&\quad= \mathbb P(y<|X_1|\le n)
       +\mathbb P(0>y,\ |X_1|>n)\\
&\quad= \mathbb P(|X_1|>y)-\mathbb P(|X_1|>n).
\end{aligned}
$$

Consequently,

$$
\begin{aligned}
\mathbb E[\bar X_{n,1}^{\,2}]
  &= \int_0^n 2y\,
     \bigl[\mathbb P(|X_1|>y)-\mathbb P(|X_1|>n)\bigr]\,\mathrm{d}y\\
  &\le \int_0^n 2y\,\mathbb P(|X_1|>y)\,\mathrm{d}y.
\end{aligned}
$$

## Continuous Cesàro means

The claim is that the tail condition

$$
y\,\mathbb P(|X_1|>y)\longrightarrow0
\qquad (y\to\infty)
$$

implies

$$
\frac1n\int_0^n 2y\,\mathbb P(|X_1|>y)\,\mathrm{d}y
\longrightarrow0.
$$

Durrett's intuition is to put $g(y):=2y\,\mathbb P(|X_1|>y)$, so that $g(y)\to0$ as $y\to\infty$, and regard $n^{-1}\int_0^n g(y)\,\mathrm{d}y$ as an average over $[0,n]$.

What was not immediately clear to me is why averaging a function over an expanding interval forces the result to zero: the integral still includes the initial finite interval, on which $g$ need not vanish.

| Discrete Cesàro mean | Continuous Cesàro mean |
|---|---|
| $a_n\to0$ | $g(y)\to0$ as $y\to\infty$ |
| $\displaystyle\frac1n\sum_{k=1}^n a_k\to0$ | $\displaystyle\frac1n\int_0^n g(y)\,\mathrm{d}y\to0$ |

Both rely on the same idea: the finite initial part becomes negligible after normalization, while the remaining terms are uniformly small.

**TO BE COMPLETED**
