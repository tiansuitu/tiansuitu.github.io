---
layout: durrett
title: "Converges a.e. — Two Proofs of the Infinitely Often Characterisation"
date: 2026-11-27
permalink: /durrett-waffling/almost-everywhere-convergence-two-proofs/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "Two proofs from STAT5010 and STAT5005, the countability issue, and the difference between convergence a.e. and convergence in probability."
---

I want to discuss two proofs of

$$
X_n\to X\quad\text{a.e.}
\iff
\forall\epsilon>0,\quad
P(\lvert X_n-X\rvert>\epsilon\text{ i.o.})=0.
$$

The first proof is from STAT5010 involving more elementary operations, is the first intuitive route I can think of. Second proof is from STAT5005, although a bit involved but quite interesting because it utilised the definition of limsup and importantly, for a nonnegative sequence, lim is zero iff limsup is zero. As liminf is nonnegative and smaller or equal to limsup, if latter zero former zero and then limit well-defined and also zero.

Throughout we work on a probability space $(\Omega,\mathcal F,P)$. Here a.e. and a.s. mean the same thing.

WLOG assume $X=0$ and suppose $X_n\geq0$. Or simply redefine $X_n$ to be the previous $\lvert X_n-X\rvert$.

The intuition is ofc simple: if $X_n$ converges almost surely then, the event (about the whole sequence infinite chain) that it deviates away from target limit (so distance greater than $\epsilon$) infinitely often (basically just the negation of real analysis 101 convergence defn, for some positive $\epsilon$) should NOT happen, in the sense that it has zero chance.

## First proof: STAT5010

For fixed $\omega\in\Omega$, by the definition of convergence,

$$
\begin{aligned}
\{\omega:\lim_{n\to\infty}X_n(\omega)=0\}
&=\bigcap_{\epsilon>0}\bigcup_{N\in\mathbb N}
\bigcap_{m\geq N}\{X_m\leq\epsilon\}.
\end{aligned}
$$

(Above use $\leq\epsilon$ not strict inequality just convenience, later negation can turn to $>\epsilon$ as we will see.)

Now negate convergence defn (taking complement of the set):

$$
\begin{aligned}
\{\omega:X_n(\omega)\not\to0\}
&=\bigcup_{\epsilon>0}\bigcap_{N\in\mathbb N}
\bigcup_{m\geq N}\{X_m>\epsilon\}.
\end{aligned}
$$

Before taking probabilities, there is a technical issue: the union over $\epsilon>0$ is uncountable. We first check that it is really a countable union in disguise.

Write

$$
A_\epsilon:=\bigcap_{N\in\mathbb N}
\bigcup_{m\geq N}\{X_m>\epsilon\}
=\limsup_{n\to\infty}\{X_n>\epsilon\}.
$$

Note that

$$
\bigcup_{k\in\mathbb N}A_{1/k}
\supseteq
\bigcup_{\epsilon>0}A_\epsilon.
$$

Above set inequality is true because for any $\epsilon>0$ can choose $k\in\mathbb N$ by Archimedean property so that $1/k<\epsilon$. Then for all $m\in\mathbb N$, $X_m>\epsilon$ implies $X_m>1/k$ and hence

$$
\limsup_{n\to\infty}\{X_n>\epsilon\}
\subseteq
\limsup_{n\to\infty}\{X_n>1/k\}.
$$

Actually above is set equality not just $\supseteq$. The other direction follows simply because each $1/k$ is itself a positive real number, so every set on the left is already one of the sets in the union on the right. Therefore

$$
\bigcup_{\epsilon>0}A_\epsilon
=\bigcup_{k=1}^{\infty}A_{1/k}\in\mathcal F.
$$

Now we can safely take probabilities:

$$
\begin{aligned}
P(\lim_n X_n=0)=1
&\iff P\left(\bigcap_{\epsilon>0}
\bigcup_{N\in\mathbb N}
\bigcap_{m\geq N}\{X_m\leq\epsilon\}\right)=1\\
&\iff P\left(\bigcup_{\epsilon>0}
\bigcap_{N\in\mathbb N}
\bigcup_{m\geq N}\{X_m>\epsilon\}\right)=0.
\end{aligned}
$$

Now crucial technical step: above is equiv to

$$
\forall\epsilon>0,\quad
P\left(\bigcap_{N\in\mathbb N}
\bigcup_{m\geq N}\{X_m>\epsilon\}\right)=0.
$$

Proof of the two directions:

**Forward direction.** So fix arbitrary $\epsilon>0$, then

$$
0\leq P(A_\epsilon)
\leq P\left(\bigcup_{\delta>0}A_\delta\right)=0.
$$

**Reverse direction.** Here need to worry about uncountable union over $\epsilon$, which cannot directly apply continuity of prob measures.

So first since given condition true for any real $\epsilon>0$, choose $\epsilon_k=1/k$ then have

$$
\forall k\in\mathbb N,\quad
P\left(\bigcap_{N\in\mathbb N}
\bigcup_{m\geq N}\{X_m>1/k\}\right)=0.
$$

Now since

$$
A_{1/k}
=\limsup_{n\to\infty}\{X_n>1/k\}
$$

is increasing sequence of sets in $k$, then by continuity from below of measure $P$, we have

$$
\begin{aligned}
P\left(\bigcup_{k=1}^{\infty}
\limsup_n\{X_n>1/k\}\right)
&=\lim_{k\to\infty}P(A_{1/k})\\
&=0.
\end{aligned}
$$

Then use the countable-union identity we established above to get

$$
P\left(\bigcup_{\epsilon>0}A_\epsilon\right)=0.
$$

For the probability inequality in this direction we only need the countable union to contain the uncountable union, but the equality also takes care of measurability.

Now going back to

$$
\begin{aligned}
X_n\to0\text{ a.e.}
&\iff \forall\epsilon>0,\quad
P\left(\bigcap_{N=1}^{\infty}
\bigcup_{m\geq N}\{X_m>\epsilon\}\right)=0\\
&\iff \forall\epsilon>0,\quad
P(\limsup_n\{X_n>\epsilon\})=0\\
&\iff \forall\epsilon>0,\quad
P(X_n>\epsilon\text{ i.o.})=0.
\end{aligned}
$$

We are done.

## Similarity with convergence in probability

Before jumping towards S5005 proof, notice this similarity with convergence in probability definition! They actually **just differ by a UNION inside $P(\cdot)$!** From superficial observation, at least.

Converge a.e.:

$$
\forall\epsilon>0,\quad
P\left(\bigcap_{n=1}^{\infty}
\bigcup_{m\geq n}\{X_m>\epsilon\}\right)=0.
$$

Or equivalently, by continuity from above of measures on decreasing sets, as the tail unions decrease as $n\to\infty$,

$$
\boxed{
\forall\epsilon>0,\quad
\lim_{n\to\infty}P\left(
\bigcup_{m\geq n}\{X_m>\epsilon\}\right)=0.
}
$$

Converge in prob:

$$
\boxed{
\forall\epsilon>0,\quad
\lim_{n\to\infty}P(\{X_n>\epsilon\})=0.
}
$$

Above difference in union is maybe a good memorising device.

Note that ofc we cannot translate the last limit back to probability of an intersection of the original events, since $\{X_n>\epsilon\}$ need not be monotone in $n$. It is the tail unions in the a.e. case that are decreasing.

Also, as

$$
\{X_n>\epsilon\}
\subseteq\bigcup_{m\geq n}\{X_m>\epsilon\},
$$

we see directly that convergence a.e. implies convergence in probability.

## Second proof: STAT5005

Ok now to 5005 which gets a bit more interesting as it first needs some understanding of numerical limsup and set limsup difference.

As a side remark, for convergence in probability,

$$
\lim_{n\to\infty}P(X_n>\epsilon)=0
\iff
\limsup_{n\to\infty}P(X_n>\epsilon)=0,
$$

because

$$
0\leq\liminf_n P(X_n>\epsilon)
\leq\limsup_n P(X_n>\epsilon).
$$

But for convergence a.e. the overarching starting idea is instead that the numerical limit of a nonnegative sequence is zero iff its numerical limsup is zero.

Now, the chain of subsets involving numerical limsup and set event limsup:

$$
\boxed{
\{\limsup_n X_n>\epsilon\}
\subseteq\limsup_n\{X_n>\epsilon\}
\subseteq\{\limsup_n X_n\geq\epsilon\}.
}
$$

For the proof, fix $\omega$ and suppress it from notation. For the first inclusion,

$$
\inf_n\sup_{m\geq n}X_m>\epsilon
$$

implies

$$
\forall n,\quad\sup_{m\geq n}X_m>\epsilon,
$$

which implies (in fact is equivalent to)

$$
\forall n,\ \exists m\geq n:\ X_m>\epsilon.
$$

Notice this logic chain last step not work if $\geq$ not $>$ as sup may not be attained (say sup equals $\epsilon$).

Then to the rightmost, start from before:

$$
\forall n,\ \exists m\geq n:\ X_m>\epsilon
$$

further implies

$$
\forall n,\ \exists m\geq n:\ X_m\geq\epsilon,
$$

which implies

$$
\forall n,\quad\sup_{m\geq n}X_m\geq\epsilon,
$$

and hence

$$
\inf_n\sup_{m\geq n}X_m\geq\epsilon.
$$

Notice here need weak inequality as if $>$ this time inf won't work (last time sup not work). More precisely, $\sup_{m\geq n}X_m>\epsilon$ for all $n$ does not imply that their infimum is strictly greater than $\epsilon$.

Then, notice

$$
\begin{aligned}
X_n\to0\text{ a.e.}
&\iff P(\lim_n X_n=0)=1\\
&\iff P(\limsup_n X_n=0)=1.
\end{aligned}
$$

As for fixed $\omega\in\Omega$, $\lim_n X_n(\omega)=0$ iff $\limsup_n X_n(\omega)=0$, since

$$
0\leq\liminf_n X_n(\omega)
\leq\limsup_n X_n(\omega).
$$

Write $Z:=\limsup_n X_n$. Recall that we redefined $X_n$ to be nonnegative, so $Z\geq0$ as well (possibly infinite). The numerical limsup is an extended real-valued measurable function.

Thus, we first show

$$
P(Z=0)=1
\implies
\forall\epsilon>0,\quad
P(\limsup_n\{X_n>\epsilon\})=0.
$$

Proof:

$$
\{Z>0\}
=\bigcup_{k=1}^{\infty}\{Z\geq1/k\}.
$$

Also for all $\epsilon>0$,

$$
\limsup_n\{X_n>\epsilon\}
\subseteq\{Z\geq\epsilon\}
\subseteq\{Z>0\}.
$$

So

$$
\forall\epsilon>0,\quad
P(\limsup_n\{X_n>\epsilon\})
\leq P(Z>0)=0.
$$

Now show that

$$
P(Z=0)=1
\impliedby
\forall\epsilon>0,\quad
P(\limsup_n\{X_n>\epsilon\})=0.
$$

Use

$$
P(Z>\epsilon)
\leq P(\limsup_n\{X_n>\epsilon\})=0
\quad\forall\epsilon>0.
$$

So that implies

$$
\forall k\in\mathbb N,\quad P(Z>1/k)=0,
$$

which implies by continuity from below, since these events increase in $k$,

$$
\begin{aligned}
P(Z>0)
&=P\left(\bigcup_{k=1}^{\infty}\{Z>1/k\}\right)\\
&=\lim_{k\to\infty}P(Z>1/k)=0.
\end{aligned}
$$

Hence $P(Z=0)=1$ and we are done.

### Why the lecture notes say "may not be the same epsilon"

In the STAT5005 notes, Chapter 2, Section 2.2, pp. 8–9, the first step is to switch from the set limsup condition to the numerical limsup condition

$$
\forall\epsilon>0,\quad P(Z\leq\epsilon)=1.
$$

The reason for the qualification about epsilon is that for the same fixed $\epsilon$, the events need not be equal. But we have

$$
P(Z>\epsilon)
\leq P(A_\epsilon)
\leq P(Z>\epsilon/2).
$$

As our statements are for ALL positive epsilon, we are allowed to use a different epsilon in the two directions. Then the notes take the limit as $\epsilon$ decreases to zero, by continuity from above. Explicitly,

$$
\begin{aligned}
P(Z=0)
&=P\left(\bigcap_{k=1}^{\infty}
\{Z\leq1/k\}\right)\\
&=\lim_{k\to\infty}P(Z\leq1/k)=1.
\end{aligned}
$$

This is another way of doing the last step in the proof above, using complements.

Above note that all in all we used generally for a nonnegative r.v. $Y$ (also allowed to be extended real-valued),

$$
\boxed{
\bigcup_{k=1}^{\infty}\{Y>1/k\}
=\bigcup_{k=1}^{\infty}\{Y\geq1/k\}
=\{Y>0\}
=\{Y\neq0\}.
}
$$

This countability issue and the distinction between the two limsups are the main things I want to remember from these two proofs.

See also [What Does an Event Occurring Infinitely Often Actually Mean?](/durrett-waffling/what-does-infinitely-often-mean/) and [Three ways to place limsup: random variables, events and probabilities](/durrett-waffling/#three-limsup-comparisons).

*References: STAT5010 (elementary set operations approach, as recalled in my notes); STAT5005, Xiao Fang, Chapter 2, Section 2.2, pp. 8–9; Durrett, Probability: Theory and Examples, 5th ed., Section 2.3.*
