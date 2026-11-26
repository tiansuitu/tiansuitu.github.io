---
layout: durrett
title: "What Does an Event Occurring Infinitely Often Actually Mean?"
date: 2026-11-27
permalink: /durrett-waffling/what-does-infinitely-often-mean/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "A note on fixed sample points, indexed events, set-theoretic limits, and the distinction between convergence and hitting a shrinking neighbourhood."
---

While revising the Borel–Cantelli lemmas in Durrett, *Probability: Theory and Examples* (5th ed., §2.3), I found myself wondering what exactly we mean when we say that an event occurs infinitely often. The notation is familiar, but the wording can conceal a subtle distinction between a fixed event and a sequence of events.

The following is my attempt to straighten out this intuition, starting from the sample space itself.

## 1. The ambiguity in saying that an event occurs infinitely often

Let $(\Omega,\mathcal F,\mathbb P)$ be a probability space and let $(A_n)_{n\geq1}$ be a sequence of events in $\mathcal F$.

For a fixed index $n$, $A_n$ is a single event, namely a measurable subset of $\Omega$. Saying that $A_n$ occurs simply means that the realised sample point $\omega$ belongs to $A_n$.

By contrast, the notation $\{A_n\text{ i.o.}\}$ does not mean that one particular event, with $n$ fixed, happens repeatedly. It refers to the entire indexed sequence:

$$
\{A_n\text{ i.o.}\}
:=\left\{\omega\in\Omega:
\forall N\geq1,\ \exists n\geq N
\text{ such that }\omega\in A_n\right\}.
$$

Equivalently,

$$
\{A_n\text{ i.o.}\}
=\limsup_{n\to\infty}A_n
=\bigcap_{N=1}^{\infty}\bigcup_{n=N}^{\infty}A_n.
$$

This is itself a single event in $\mathcal F$, since a sigma-field is closed under countable unions and intersections. A more transparent verbal description is that **the same realised sample point belongs to $A_n$ for infinitely many indices $n$**. The index need not represent time.

The analogous definition of eventual membership is

$$
\liminf_{n\to\infty}A_n
=\bigcup_{N=1}^{\infty}\bigcap_{n=N}^{\infty}A_n
=\left\{\omega\in\Omega:
\exists N\geq1,\ \forall n\geq N,\ \omega\in A_n\right\}.
$$

The order of the quantifiers is essential: infinitely often means that every tail contains an occurrence, whereas eventually always means that there is a tail in which every index is an occurrence. In particular, $\liminf_n A_n\subseteq\limsup_n A_n$.

## 2. Infinite coin tossing: what is a single outcome?

Consider an infinite sequence of independent fair coin tosses. Use the canonical sample space

$$
\Omega=\{H,T\}^{\mathbb N},
\qquad
\mathcal F=\bigotimes_{n=1}^{\infty}2^{\{H,T\}},
\qquad
\mathbb P=\bigotimes_{n=1}^{\infty}
\left(\tfrac12\delta_H+\tfrac12\delta_T\right).
$$

A single sample point is an entire infinite history,

$$
\omega=(\omega_1,\omega_2,\omega_3,\ldots),
\qquad \omega_n\in\{H,T\}.
$$

One way I find helpful to think about this is to imagine a possible universe containing the entire history of the experiment, rather than just a snapshot at one time. The mathematical experiment has one outcome $\omega$, even though that outcome has infinitely many coordinates.

Define

$$
A_n:=\{\omega\in\Omega:\omega_n=H\}.
$$

For example, $A_7$ is the event that the seventh toss is a head. However, its elements are still *entire infinite sequences*, not merely outcomes of the seventh trial. The first, second, eighth and millionth coordinates are all unrestricted. Thus $A_7$ describes a property of the whole outcome while specifying only one of its coordinates.

We can now form two different events from precisely the same sequence $(A_n)$:

$$
C:=\bigcup_{n=1}^{\infty}A_n
=\{\omega:\exists n\geq1,\ \omega_n=H\},
$$

$$
B:=\limsup_{n\to\infty}A_n
=\{\omega:\forall N\geq1,\ \exists n\geq N,\ \omega_n=H\}.
$$

The former says that at least one head appears; the latter says that infinitely many heads appear. The sample point

$$
\omega=(H,T,T,T,\ldots)
$$

belongs to $C$ but not to $B$. Hence $B\subsetneq C$.

Nevertheless, $\mathbb P(B)=1$ by the second Borel–Cantelli lemma (Theorem 2.3.7), because the events are independent and $\sum_n\mathbb P(A_n)=\sum_n 1/2=\infty$. Since $B\subseteq C$, also $\mathbb P(C)=1$. This is a useful reminder that two events may have equal probability, and even equal indicators almost surely, without being the same set.

The phrase "heads occur infinitely often" is natural here because the index happens to correspond to a trial. But in abstract probability theory there need not be any time or repeated experiment at all.

## 3. Why the names limsup and liminf?

Durrett explains the terminology using indicator functions. Fix $\omega\in\Omega$. The numerical sequence $\mathbf 1_{A_n}(\omega)$ takes values only in $\{0,1\}$.

The supremum of these indicators is one exactly when at least one of the indicators is one, while their infimum is one exactly when every indicator is one. Thus, pointwise,

$$
\sup_{n\geq1}\mathbf 1_{A_n}
=\mathbf 1_{\bigcup_{n\geq1}A_n},
\qquad
\inf_{n\geq1}\mathbf 1_{A_n}
=\mathbf 1_{\bigcap_{n\geq1}A_n}.
$$

Using the numerical definitions of limsup and liminf,

$$
\begin{aligned}
\limsup_n\mathbf 1_{A_n}(\omega)
&=\inf_{N\geq1}\sup_{n\geq N}\mathbf 1_{A_n}(\omega)\\
&=\inf_{N\geq1}\mathbf 1_{\bigcup_{n\geq N}A_n}(\omega)\\
&=\mathbf 1_{\limsup_n A_n}(\omega),
\end{aligned}
$$

and similarly,

$$
\begin{aligned}
\liminf_n\mathbf 1_{A_n}(\omega)
&=\sup_{N\geq1}\inf_{n\geq N}\mathbf 1_{A_n}(\omega)\\
&=\sup_{N\geq1}\mathbf 1_{\bigcap_{n\geq N}A_n}(\omega)\\
&=\mathbf 1_{\liminf_n A_n}(\omega).
\end{aligned}
$$

Union corresponds to existential quantification and supremum; intersection corresponds to universal quantification and infimum. The set-theoretic terminology is therefore inherited directly from the numerical one. None of these identities requires independence or even a probability measure.

## 4. First example: a fixed real number

Take the measurable space $(\mathbb R,\mathcal B(\mathbb R))$ and define

$$
A_n=\left(-\frac1n,\frac1n\right).
$$

Here $\omega$ is a single real number, not a sequence. Every $A_n$ tests the same number against a progressively smaller interval.

If $\omega=0$, then $\omega\in A_n$ for every $n$, so it belongs to both limiting sets.

If $\omega\neq0$, choose an integer $N>1/\lvert \omega\rvert$. For every $n\geq N$,

$$
\frac1n\leq\frac1N<\lvert\omega\rvert.
$$

Thus $\omega\notin A_n$ for all $n\geq N$. It cannot belong to the limsup, and consequently cannot belong to the liminf either. Therefore

$$
\boxed{\liminf_n A_n=\limsup_n A_n=\{0\}.}
$$

There are no trials here. The index merely labels a sequence of subsets of the real line. The sample point is held fixed throughout.

## 5. Second example: an infinite sequence of real numbers

Now change the sample space to

$$
\Omega=\mathbb R^{\mathbb N},
\qquad
\mathcal F=\bigotimes_{n=1}^{\infty}\mathcal B(\mathbb R).
$$

An outcome is now a sequence $\omega=(\omega_1,\omega_2,\ldots)$. Let $\pi_n:\Omega\to\mathbb R$ be the $n$th coordinate projection and define the cylinder event

$$
A_n:=\pi_n^{-1}\left(\left(-\frac1n,\frac1n\right)\right)
=\left\{\omega\in\Omega:\lvert\omega_n\rvert<\frac1n\right\}.
$$

In the first example, the same real number was tested at every index. Here we test a potentially different coordinate at each index. The outcome $\omega$ itself is still fixed; it is its coordinates that vary.

The two limiting events are now

$$
\limsup_n A_n
=\left\{\omega:\forall N\geq1,\ \exists n\geq N,\
\lvert\omega_n\rvert<\frac1n\right\},
$$

$$
\liminf_n A_n
=\left\{\omega:\exists N\geq1,\ \forall n\geq N,\
\lvert\omega_n\rvert<\frac1n\right\}.
$$

Unlike the intervals in the previous example, these cylinder events are not nested. They constrain different coordinates. The limiting sets are no longer just the singleton containing the zero sequence.

### Example A: a sequence that hits the shrinking interval every time

Let $\omega_n=1/(2n)$. Then $\lvert \omega_n\rvert<1/n$ for every $n\geq1$, so

$$
\omega\in\liminf_n A_n\subseteq\limsup_n A_n.
$$

The same conclusion holds for $\omega_n=1/n^2$, except that at $n=1$ the strict inequality fails. This does not matter for either limiting set, since it holds at every $n\geq2$.

### Example B: convergence to zero is not sufficient

Let $\omega_n=1/\sqrt n$. Although $\omega_n\to0$, we have

$$
\lvert\omega_n\rvert=\frac1{\sqrt n}\geq\frac1n
\qquad\text{for every }n\geq1.
$$

Hence $\omega\notin A_n$ for every $n$, and in particular $\omega\notin\limsup_n A_n$.

The issue is that convergence to zero only requires eventual membership in each *fixed* neighbourhood of zero. Here the neighbourhood changes with $n$. Even the sequence $\omega_n=1/n$ fails membership at every index, because the intervals are open.

### Example C: infinitely often does not require convergence

Let

$$
\omega=(0,1,0,1,\ldots).
$$

For every odd index, $\omega_n=0$, hence $\omega\in A_n$. For every even index, $\omega_n=1$, hence $\omega\notin A_n$.

Therefore

$$
\omega\in\limsup_n A_n\setminus\liminf_n A_n.
$$

The sequence does not converge at all. This corrects the tempting interpretation that the limsup consists of sequences converging sufficiently quickly to zero. It only requires the sequence to hit the shrinking interval at infinitely many indices.

In fact, membership in the limsup implies that some subsequence converges to zero: choose increasing indices $n_k$ satisfying $\lvert \omega_{n_k}\rvert<1/n_k$. But the converse fails, as Example B demonstrates.

## 6. Does membership in the liminf imply convergence?

Yes. Suppose $\omega\in\liminf_n A_n$. By definition there exists $N_0$ such that

$$
\lvert\omega_n\rvert<\frac1n
\qquad\forall n\geq N_0.
$$

Fix any $\varepsilon>0$ and choose $N\geq N_0$ with $N>1/\varepsilon$. Then for every $n\geq N$,

$$
\lvert\omega_n\rvert<\frac1n\leq\frac1N<\varepsilon.
$$

This is exactly the definition of $\omega_n\to0$. Thus

$$
\liminf_n A_n
\subsetneq
\{\omega\in\mathbb R^{\mathbb N}:\omega_n\to0\}.
$$

The inclusion is strict by Example B. Also, if $n\lvert \omega_n\rvert\to0$, then $\omega$ belongs to the liminf, but the converse is false: $\omega_n=1/(2n)$ belongs to every $A_n$ while $n\lvert \omega_n\rvert=1/2$. So even membership in the liminf should not be confused with the stronger rate condition $\omega_n=o(1/n)$.

Putting the examples together:

- The sequences $\omega_n=0$, $\omega_n=1/(2n)$ and $\omega_n=1/n^2$ converge to zero and belong to both limiting sets.
- The sequences $\omega_n=1/\sqrt n$ and $\omega_n=1/n$ converge to zero but belong to neither limiting set.
- The alternating sequence $\omega=(0,1,0,1,\ldots)$ does not converge and belongs to the limsup but not the liminf.

If a probability measure is subsequently placed on this product space, and $X_n=\pi_n$ are its coordinate random variables, these are measurable events concerning the sample paths of $(X_n)$. Their probabilities depend on the chosen measure, but the pointwise conclusions above do not.

## Takeaway

Whenever I see $\{A_n\text{ i.o.}\}$, I should first identify the sample space and ask what a single $\omega$ actually represents. Then I should fix that $\omega$ and interpret membership in the sequence of events using the correct quantifiers.

In an infinite coin-toss experiment, a single outcome is an entire history. On the real line, it is simply a number. On an infinite product of real lines, it is a sequence. In all three cases the definition of infinitely often is identical: **one fixed outcome belongs to the indexed events for infinitely many indices**.

The notation does not prescribe a time dimension, independence, or a convergence rate. Those features, if relevant, come from the choice of sample space, the particular events, and the probability measure.

*Reference: Rick Durrett, Probability: Theory and Examples, 5th ed., §2.3, pp. 58–60 (set-theoretic limsup and liminf, indicator identities, and the Borel–Cantelli lemmas).*
