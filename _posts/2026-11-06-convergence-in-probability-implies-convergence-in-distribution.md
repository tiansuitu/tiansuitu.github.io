---
layout: stat5010
title: "Convergence in Probability Implies Convergence in Distribution: CDF Sandwiching"
date: 2026-11-06
permalink: /stat5010-study/convergence-in-probability-implies-convergence-in-distribution/
read_time: false
share: false
related: false
tags:
  - stat5010-study
excerpt: "A proof built from event inclusions, probability bounds, and continuity of the limiting CDF, including two ways to obtain the lower bound."
---

*STAT5010 — working notes on modes of stochastic convergence.*

## The intuition

A distribution function is induced by a random variable and the underlying probability measure. Thus, if $X_n$ is close to $X$ with high probability, I expect the distributions of $X_n$ and $X$ to be close as well.

One important refinement: **the underlying probability measure $\mathbb P$ is not changing**. Rather, $X_n$ induces a probability law $\mu_n=\mathbb P\circ X_n^{-1}$, whose CDF is

$$
F_n(t)=\mathbb P(X_n\le t)
     =\mu_n((-\infty,t]).
$$

The obstacle is the threshold $t$. Even when $X_n$ is very close to $X$, one variable can be on one side of $t$ and the other on the opposite side. The key is to introduce a small margin $\varepsilon$ around $t$.

## Claim and definitions

Let $X_n,X$ be real-valued random variables on the same probability space $(\Omega,\mathcal F,\mathbb P)$. Suppose that $X_n\xrightarrow{\mathbb P}X$, meaning

$$
\forall\,\varepsilon>0,\qquad
p_{n,\varepsilon}:=\mathbb P(\lvert X_n-X\rvert>\varepsilon)
\longrightarrow 0
\quad(n\to\infty).
$$

We want to show $X_n\xrightarrow{d}X$: for each continuity point $t$ of $F_X$,

$$
F_n(t)=\mathbb P(X_n\le t)
\longrightarrow
F_X(t)=\mathbb P(X\le t).
$$

Fix such a $t$ and fix $\varepsilon>0$. Define the events

$$
\begin{aligned}
A_n &:= \{X_n\le t\},\\
B_{n,\varepsilon} &:= \{\lvert X_n-X\rvert>\varepsilon\},\\
C^-_\varepsilon &:= \{X\le t-\varepsilon\},\\
C^+_\varepsilon &:= \{X\le t+\varepsilon\}.
\end{aligned}
$$

The event $B_{n,\varepsilon}$ is the error event: its probability tends to zero. On its complement, the two random variables differ by at most $\varepsilon$.

## 1. The upper bound

The motivation is to split the event we care about into a **good part**, where $X_n$ and $X$ are close, and a **bad part**, whose probability vanishes:

$$
\begin{aligned}
\mathbb P(X_n\le t)
&=\mathbb P(A_n\cap B_{n,\varepsilon}^c)
 +\mathbb P(A_n\cap B_{n,\varepsilon})\\
&\le \mathbb P(A_n\cap B_{n,\varepsilon}^c)
 +\mathbb P(B_{n,\varepsilon}).
\end{aligned}
$$

If $X_n\le t$ and $\lvert X_n-X\rvert\le\varepsilon$, then

$$
X\le X_n+\varepsilon\le t+\varepsilon.
$$

Therefore we have the **event inclusion**

$$
A_n\cap B_{n,\varepsilon}^c
\subseteq C^+_\varepsilon,
$$

and hence

$$
\boxed{
F_n(t)\le F_X(t+\varepsilon)+p_{n,\varepsilon}.
}
$$

This is an inclusion, **not an equality of events**: the condition $X\le X_n+\varepsilon$ alone does not imply $\lvert X_n-X\rvert\le\varepsilon$.

## 2. The lower bound: work backwards from $X$

For a lower bound on $F_n(t)$, it is helpful to start with a slightly smaller event involving $X$:

$$
C^-_\varepsilon=\{X\le t-\varepsilon\}.
$$

Whenever $X\le t-\varepsilon$ and $\lvert X_n-X\rvert\le\varepsilon$,

$$
X_n\le X+\varepsilon\le t.
$$

Thus

$$
C^-_\varepsilon\cap B_{n,\varepsilon}^c
\subseteq A_n.
$$

Partitioning $C^-_\varepsilon$ into its good and bad parts gives

$$
\begin{aligned}
F_X(t-\varepsilon)
&=\mathbb P(C^-_\varepsilon\cap B_{n,\varepsilon}^c)
  +\mathbb P(C^-_\varepsilon\cap B_{n,\varepsilon})\\
&\le \mathbb P(A_n)+\mathbb P(B_{n,\varepsilon}).
\end{aligned}
$$

Equivalently,

$$
\boxed{
F_n(t)\ge F_X(t-\varepsilon)-p_{n,\varepsilon}.
}
$$

This has the same structure as the upper-bound argument: compare two threshold events on the good event, and pay an error of at most $p_{n,\varepsilon}$.

## 3. An alternative lower bound: use complements

There was another route I found natural. Since upper bounds follow readily from subadditivity, rewrite the desired lower bound as

$$
F_n(t)=1-\mathbb P(X_n>t),
$$

and **upper-bound** $\mathbb P(X_n>t)$.

Split according to the same good and bad events:

$$
\begin{aligned}
\mathbb P(X_n>t)
&=\mathbb P(\{X_n>t\}\cap B_{n,\varepsilon})
 +\mathbb P(\{X_n>t\}\cap B_{n,\varepsilon}^c)\\
&\le p_{n,\varepsilon}
 +\mathbb P(\{X_n>t\}\cap B_{n,\varepsilon}^c).
\end{aligned}
$$

On $\{X_n>t\}\cap B_{n,\varepsilon}^c$, we have

$$
X\ge X_n-\varepsilon>t-\varepsilon.
$$

It follows that

$$
\begin{aligned}
\mathbb P(X_n>t)
&\le p_{n,\varepsilon}
 +\mathbb P(X>t-\varepsilon)\\
&=p_{n,\varepsilon}+1-F_X(t-\varepsilon).
\end{aligned}
$$

Taking complements again,

$$
F_n(t)\ge F_X(t-\varepsilon)-p_{n,\varepsilon},
$$

exactly as in the direct argument.

## 4. The CDF sandwich and the order of limits

The two bounds together yield, for **each fixed** $\varepsilon>0$ and every $n$,

$$
\boxed{
F_X(t-\varepsilon)-p_{n,\varepsilon}
\le F_n(t)
\le F_X(t+\varepsilon)+p_{n,\varepsilon}.
}
$$

First let $n\to\infty$ **with $\varepsilon$ held fixed**. Since $p_{n,\varepsilon}\to0$,

$$
F_X(t-\varepsilon)
\le\liminf_{n\to\infty}F_n(t)
\le\limsup_{n\to\infty}F_n(t)
\le F_X(t+\varepsilon).
$$

Only now let $\varepsilon\downarrow0$. A CDF is always right-continuous, so

$$
F_X(t+\varepsilon)\longrightarrow F_X(t).
$$

For the lower endpoint, we need continuity **at the chosen $t$**:

$$
F_X(t-\varepsilon)\longrightarrow F_X(t).
$$

Consequently,

$$
F_X(t)
\le\liminf_{n\to\infty}F_n(t)
\le\limsup_{n\to\infty}F_n(t)
\le F_X(t),
$$

so $\lim_nF_n(t)=F_X(t)$. Since $t$ was an arbitrary continuity point of $F_X$, we have proved

$$
\boxed{X_n\xrightarrow{\mathbb P}X
\quad\Longrightarrow\quad
X_n\xrightarrow{d}X.}
$$

**A detail worth remembering:** it is not valid to replace $F_X(t+\varepsilon)$ by $F_X(t)$ immediately after taking $n\to\infty$. The margin $\varepsilon$ remains fixed at that stage. Nor is a lower bound involving $\limsup F_n(t)$ sufficient by itself: to establish convergence, the lower bound must control the **$\liminf$**.

## 5. Why continuity points are necessary

Consider the deterministic random variables

$$
X_n=\frac1n,\qquad X=0.
$$

We even have $X_n\to X$ almost surely. But at $t=0$,

$$
F_n(0)=\mathbb P(X_n\le0)=0,
\qquad
F_X(0)=\mathbb P(X\le0)=1.
$$

The CDFs do not converge at $0$, which is a discontinuity point of $F_X$. This explains why convergence in distribution is defined using continuity points of the limiting CDF.

## Takeaway: CDF sandwiching

The technique can be remembered as

$$
\begin{gathered}
\text{convergence in probability}\\
\Downarrow\\
\text{vanishing bad event } \{\lvert X_n-X\rvert>\varepsilon\}\\
\Downarrow\\
F_X(t-\varepsilon)-p_{n,\varepsilon}
\le F_n(t)
\le F_X(t+\varepsilon)+p_{n,\varepsilon}\\
\Downarrow\quad (n\to\infty,\ \varepsilon\downarrow0)\\
F_n(t)\to F_X(t)
\quad\text{at continuity points}.
\end{gathered}
$$

The central insight is **event comparison with a margin**, followed by the correct order of limits.

---

*Reference: Rick Durrett, Probability: Theory and Examples, 5th ed., Section 3.2 (weak convergence).*
