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
