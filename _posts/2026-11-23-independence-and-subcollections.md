---
layout: durrett
title: "Independence and the Hidden Sub-Index Condition"
date: 2026-11-23
permalink: /durrett-waffling/independence-and-subcollections/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "Why independence always concerns every subcollection, even when Durrett's definitions for sigma-fields and random variables do not mention sub-indices."
---

While reading Durrett, *Probability: Theory and Examples* (5th ed.), §2.1, I wondered why **independence of events** is stated using *every subset of indices*, whereas independence of **random variables** and **sigma-fields** is stated using only the full index set.

The point is that **mutual independence is always a statement about every subcollection**. At the higher levels, the sub-index condition is already built into the definition.

## Three levels of independence

Work on a probability space $(\Omega,\mathcal F,\mathbb P)$, with indices $\{1,\ldots,n\}$.

- **Sigma-fields.** Sigma-fields $\mathcal F_1,\ldots,\mathcal F_n\subseteq\mathcal F$ are independent if, for every choice $A_i\in\mathcal F_i$,
  
  $$
  \mathbb P\left(\bigcap_{i=1}^n A_i\right)
  =\prod_{i=1}^n\mathbb P(A_i).
  $$
  
  Why is there no explicit sub-index condition? Given any $I\subseteq\{1,\ldots,n\}$, set $A_j=\Omega$ for $j\notin I$. Every sigma-field contains $\Omega$, and $\mathbb P(\Omega)=1$. Thus the full-index identity also gives
  
  $$
  \mathbb P\left(\bigcap_{i\in I}A_i\right)
  =\prod_{i\in I}\mathbb P(A_i).
  $$

- **Random variables.** A real-valued random variable $X_i$ generates the smallest sigma-field making it measurable:
  
  $$
  \sigma(X_i)=\{X_i^{-1}(B):B\in\mathcal B(\mathbb R)\}.
  $$
  
  Independence of $X_1,\ldots,X_n$ is exactly independence of $\sigma(X_1),\ldots,\sigma(X_n)$. To omit an index $j$ from the joint-probability identity, simply choose the Borel set $B_j=\mathbb R$: then $\{X_j\in B_j\}=\Omega$.

- **Events.** An event $E_i\in\mathcal F$ is represented by its indicator random variable $\mathbf 1_{E_i}$. Indeed,
  
  $$
  \sigma(\mathbf 1_{E_i})
  =\{\varnothing,E_i,E_i^c,\Omega\}.
  $$
  
  Thus independence of events is a special case of independence of random variables. But if we write the condition directly in terms of the **given events** $E_1,\ldots,E_n$, we must require
  
  $$
  \mathbb P\left(\bigcap_{i\in I}E_i\right)
  =\prod_{i\in I}\mathbb P(E_i)
  \qquad
  \text{for every nonempty }I\subseteq\{1,\ldots,n\}.
  $$
  
  A given event $E_j$ cannot simply be replaced by $\Omega$ while remaining the same event. Hence the sub-index condition must appear explicitly.

The same issue occurs for **arbitrary collections of sets** $\mathcal A_i\subseteq\mathcal F$, which need not contain $\Omega$. This is the motivation behind Durrett's Lemma 2.1.5: adjoining $\Omega$ to each collection makes the full-index formulation sufficient.

**Takeaway.** There is no change in the meaning of independence as we move from sigma-fields to random variables to events. We always want independence of *every subcollection*; the only difference is whether we can encode omitted indices by choosing the whole space.

*Reference: Durrett (5th ed.), §2.1, Theorems 2.1.1–2.1.3 and Lemma 2.1.5.*

## An equivalent, more parallel formulation

Durrett (5th ed., pp. 38–39) states independence of both **events** and **collections of events** using every sub-index set $I\subseteq\{1,\ldots,n\}$. This initially looks different from the full-index definitions for sigma-fields and random variables. But the difference is not substantive: as in the $B_i$ notation described in Fang's notes, we can write both definitions in a parallel full-index form.

**1. Independence of events.** Events $A_1,\ldots,A_n\in\mathcal F$ are independent **if and only if**

$$
\boxed{
\mathbb P\left(\bigcap_{i=1}^n B_i\right)
=\prod_{i=1}^n\mathbb P(B_i)
\qquad
\text{for every choice }B_i\in\{A_i,\Omega\}.
}
$$

Indeed, for any $I\subseteq\{1,\ldots,n\}$, choose $B_i=A_i$ when $i\in I$ and $B_i=\Omega$ otherwise. Since intersection with $\Omega$ changes nothing and $\mathbb P(\Omega)=1$, this is exactly Durrett's sub-index condition:

$$
\mathbb P\left(\bigcap_{i\in I}A_i\right)
=\prod_{i\in I}\mathbb P(A_i).
$$

**2. Independence of collections of events.** Let $\mathcal A_1,\ldots,\mathcal A_n\subseteq\mathcal F$ be arbitrary collections, and put $\overline{\mathcal A}_i=\mathcal A_i\cup\{\Omega\}$. These collections are independent **if and only if**

$$
\boxed{
\mathbb P\left(\bigcap_{i=1}^n B_i\right)
=\prod_{i=1}^n\mathbb P(B_i)
\qquad
\text{for every choice }B_i\in\mathcal A_i\cup\{\Omega\}.
}
$$

In other words, at each index we may select an event from the original collection $\mathcal A_i$, **or** select $\Omega$ to omit that index. This is equivalent to requiring, for every $I\subseteq\{1,\ldots,n\}$ and every choice $A_i\in\mathcal A_i$ for $i\in I$,

$$
\mathbb P\left(\bigcap_{i\in I}A_i\right)
=\prod_{i\in I}\mathbb P(A_i).
$$

Thus the two boxed definitions have precisely the same structure. In the second, we are choosing an event from each *collection*, rather than starting with one prescribed event at each index. This is also the content of Durrett's **Lemma 2.1.5**: adjoining $\Omega$ makes the sub-index requirement implicit in a full-index formula, just as it already is for sigma-fields and random variables.

*Reference: Durrett, 5th ed., pp. 38–39 (definitions of independence and Lemma 2.1.5).*

