---
layout: durrett
title: "Centring Indicator Functions: One-Sided Chebyshev and L2 Projection"
date: 2026-11-25
permalink: /durrett-waffling/centering-indicators-and-one-sided-chebyshev/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "How centring an indicator sharpens Cauchy–Schwarz, extends to nonzero means, and connects to the L2 projection interpretation of conditional expectation."
---

*Created by ChatGPT, based on a discussion during STAT5005 revision.*

## Why centre an indicator?

Work on a probability space $(\Omega,\mathcal F,\mathbb P)$. Let $Y\in L^2(\mathbb P)$ satisfy $\mathbb E[Y]=0$ and $\mathbb E[Y^2]=\sigma^2$. For $a>0$, set

$$
A=\{Y\geq a\},\qquad p=\mathbb P(A).
$$

Since $Y\mathbf 1_A\geq a\mathbf 1_A$, ordinary Cauchy–Schwarz gives

$$
ap\leq\mathbb E[Y\mathbf 1_A]
\leq \sqrt{\mathbb E[Y^2]\mathbb E[\mathbf 1_A^2]}
=\sigma\sqrt p.
$$

For $p>0$, this gives only $p\leq\sigma^2/a^2$. We have not yet exploited the zero-mean assumption.

The key observation is that subtracting any deterministic constant $c$ from the indicator leaves the expected product unchanged:

$$
\mathbb E[Y(\mathbf 1_A-c)]
=\mathbb E[Y\mathbf 1_A]-c\mathbb E[Y]
=\mathbb E[Y\mathbf 1_A].
$$

In particular, choose $c=p=\mathbb E[\mathbf 1_A]$. Then

$$
\mathbb E[(\mathbf 1_A-p)^2]
=\operatorname{Var}(\mathbf 1_A)=p(1-p).
$$

Applying Cauchy–Schwarz again, now to the centred indicator,

$$
ap\leq\mathbb E[Y(\mathbf 1_A-p)]
\leq\sigma\sqrt{p(1-p)}.
$$

Squaring and dividing by $p>0$ yields $a^2p\leq\sigma^2(1-p)$. The case $p=0$ is trivial. Thus

$$
\boxed{
\mathbb P(Y\geq a)\leq\frac{\sigma^2}{a^2+\sigma^2}.
}
$$

This is the one-sided Chebyshev (Cantelli) inequality. The improvement comes from replacing the second moment $p$ by the smaller variance $p(1-p)$, while preserving the expected product.

## What if the mean is not zero?

Let $Y\in L^2(\mathbb P)$ have mean $\mu=\mathbb E[Y]$ and variance $\sigma^2$. For any event $A\in\mathcal F$, with $p=\mathbb P(A)$,

$$
\begin{aligned}
\mathbb E[Y(\mathbf 1_A-p)]
&=\mathbb E[Y\mathbf 1_A]-\mu p\\
&=\mathbb E[(Y-\mu)\mathbf 1_A]\\
&=\mathbb E[(Y-\mu)(\mathbf 1_A-p)].
\end{aligned}
$$

So centring the indicator alone no longer preserves the original expected product, but it does isolate the covariance. Cauchy–Schwarz gives the general bound

$$
\left|\mathbb E[Y\mathbf 1_A]-\mu p\right|
\leq \sigma\sqrt{p(1-p)}.
$$

Now take $A=\{Y\geq\mu+a\}$ for $a>0$. On $A$, we have $Y-\mu\geq a$, so

$$
ap\leq\mathbb E[(Y-\mu)\mathbf 1_A]
\leq\sigma\sqrt{p(1-p)}.
$$

The same rearrangement proves

$$
\boxed{
\mathbb P(Y-\mu\geq a)\leq
\frac{\operatorname{Var}(Y)}
{a^2+\operatorname{Var}(Y)}.
}
$$

Equivalently, for a threshold $t>\mu$, the denominator is $(t-\mu)^2+\operatorname{Var}(Y)$.

## Why is the mean the optimal constant? An L2 projection

For any $V\in L^2(\mathbb P)$ and any deterministic constant $c\in\mathbb R$, expanding the square gives

$$
\begin{aligned}
\mathbb E[(V-c)^2]
&=\mathbb E[(V-\mathbb E[V])^2]
 +(\mathbb E[V]-c)^2\\
&=\operatorname{Var}(V)+(\mathbb E[V]-c)^2.
\end{aligned}
$$

The cross term vanishes because $\mathbb E[V-\mathbb E[V]]=0$. Consequently,

$$
\boxed{
\underset{c\in\mathbb R}{\arg\min}\;
\mathbb E[(V-c)^2]=\mathbb E[V].
}
$$

This is precisely the orthogonal projection of $V$ onto the closed subspace of constant random variables in the Hilbert space $L^2(\mathbb P)$, with inner product $\langle U,V\rangle=\mathbb E[UV]$. The residual $V-\mathbb E[V]$ is orthogonal to every constant.

The connection to Chapter 4 is that, for the trivial sigma-field $\mathcal G=\{\varnothing,\Omega\}$,

$$
\mathbb E[V\mid\mathcal G]=\mathbb E[V]
\qquad\text{a.s.}
$$

More generally, conditional expectation is the orthogonal projection onto $L^2(\Omega,\mathcal G,\mathbb P)$, and minimises $\mathbb E[(V-Z)^2]$ over square-integrable $\mathcal G$-measurable $Z$, uniquely up to almost sure equality.

In our example, take $V=\mathbf 1_A$. Its best constant approximation is $p$, and its residual has squared norm $p(1-p)$. If $\mathbb E[Y]=0$, the quantity $\mathbb E[Y(V-c)]$ is independent of $c$. Hence choosing $c=\mathbb E[V]$ minimises the Cauchy–Schwarz upper bound among all deterministic shifts of $V$.

**Takeaway.** Centring is not just an algebraic trick. It removes the component in the direction of the constants, which contributes nothing to an inner product with a mean-zero random variable. This makes the Cauchy–Schwarz bound as small as possible within this family of constant shifts.

*References: Durrett, Probability: Theory and Examples (5th ed.), Exercise 1.6.4(ii) and Chapter 4 (conditional expectation). The Cauchy–Schwarz argument here is an alternative to the shift-and-optimise approach suggested in the exercise.*
