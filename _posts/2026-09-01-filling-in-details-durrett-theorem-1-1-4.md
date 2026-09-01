---
layout: durrett
title: "Filling in Details for Durrett's Proof of Theorem 1.1.4 (p. 5)"
date: 2026-09-01
permalink: /durrett-waffling/filling-in-details-durrett-theorem-1-1-4/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "Working notes filling in the finite-subadditivity, compactness, and endpoint details in Durrett's proof of Theorem 1.1.4."
---

Lemma 1.1.10 is more about **finite** (sub)additivity than about countable (sub)additivity. Lemma 1.1.10(b) is essentially Theorem 1.1.1(i)--(ii) repeated for $\bar\mu$ on $\overline{\mathcal S}$, but only for a finite cover: first, $A\subseteq B$ gives monotonicity $\bar\mu(A)\leq \bar\mu(B)$; then disjointifying a finite cover gives

$$
\bar\mu(A)\leq \sum_{i=1}^n \bar\mu(B_i).
$$

Thus it is the usual

$$
\text{finite additivity}
\Longrightarrow \text{monotonicity}
\Longrightarrow \text{finite subadditivity}
$$

argument.

Later, when verifying conditions (i) and (ii) of Theorem 1.1.9, only Lemma 1.1.10(b) is used directly in the compactness argument. Lemma 1.1.10(a) is used to prove (b).

## Two small facts used in the proof

- **Compactness / finite subcover.** Let $(X,\mathcal T)$ be a topological space and let $K\subseteq X$ be compact. If $\{O_i\}_{i\in I}\subseteq\mathcal T$ is an open cover of $K$, i.e.

  $$
  K\subseteq\bigcup_{i\in I}O_i,
  $$

  where $I$ may be arbitrary, then there is a finite subset $J=\{i_1,\ldots,i_m\}\subseteq I$ such that

  $$
  K\subseteq\bigcup_{i\in J}O_i.
  $$

  In Durrett's proof, $K=[a+\delta,b]$, which is compact in $\mathbb R$, and the intervals $(a_i,b_i+\eta_i)$ form an open cover of $K$.

- **Right continuity of a nondecreasing function.** If $F$ is right-continuous at $x_0$, then for every $\varepsilon>0$ there is a $\gamma_\varepsilon>0$ such that

  $$
  0<x-x_0<\gamma_\varepsilon
  \quad\Longrightarrow\quad
  |F(x)-F(x_0)|<\varepsilon.
  $$

  Since $F$ is nondecreasing, $F(x)-F(x_0)\geq0$ when $x>x_0$. Hence any $\delta_\varepsilon\in(0,\gamma_\varepsilon)$, for example $\delta_\varepsilon=\gamma_\varepsilon/2$, gives

  $$
  F(x_0+\delta_\varepsilon)<F(x_0)+\varepsilon.
  $$

Durrett's semialgebra is

$$
\mathcal S_1=\{\varnothing\}\cup
\{(a,b]:-\infty\leq a<b\leq+\infty\}.
$$

Thus $\varnothing$ is included separately, since the interval notation only allows $a<b$. The set function in Theorem 1.1.4 should therefore be understood as

$$
\mu(\varnothing):=0,
\qquad
\mu((a,b]):=F(b)-F(a).
$$

So the hypothesis $\mu(\varnothing)=0$ in Theorem 1.1.9 is satisfied by definition.

## Why does Theorem 1.1.9 require only countable subadditivity, not countable additivity?

Because condition (i) already supplies finite additivity. Suppose

$$
S=\mathop{\dot\bigcup}_{i=1}^{\infty}S_i,
$$

with $S,S_i\in\mathcal S$. Condition (ii) gives one direction:

$$
\mu(S)\leq\sum_{i=1}^{\infty}\mu(S_i).
$$

For every $n$, finite additivity and monotonicity give

$$
\sum_{i=1}^n\mu(S_i)
=\bar\mu\!\left(\mathop{\dot\bigcup}_{i=1}^nS_i\right)
\leq\mu(S).
$$

Letting $n\to\infty$ gives the reverse inequality. Thus conditions (i) and (ii) together already imply the required countable additivity whenever the countable disjoint union stays in $\mathcal S$. It would be redundant to assume it again.

## Proof of Theorem 1.1.4, with the details filled in

*Proof.* First note that $\mu$ is allowed to take values in the extended nonnegative reals. For example, when $F(x)=x$, the resulting Lebesgue measure has $\mu(\mathbb R)=+\infty$.

Since $F:\mathbb R\to\mathbb R$ is finite-valued and nondecreasing, the limits

$$
F(+\infty):=\lim_{x\uparrow+\infty}F(x)
=\sup_{x\in\mathbb R}F(x)
$$

and

$$
F(-\infty):=\lim_{x\downarrow-\infty}F(x)
=\inf_{x\in\mathbb R}F(x)
$$

exist in the extended reals. Moreover,

$$
F(-\infty)<+\infty,
\qquad
F(+\infty)>-\infty.
$$

Indeed, $F(-\infty)\leq F(x)\leq F(+\infty)$ for every finite $x$, while $F(x)\in\mathbb R$. Therefore $F(b)-F(a)$ is well-defined in $[0,+\infty]$ whenever $a<b$. The possible forms are finite minus finite, $+\infty$ minus finite, finite minus $-\infty$, or $+\infty$ minus $-\infty$. The undefined forms $+\infty-(+\infty)$ and $-\infty-(-\infty)$ cannot occur here. Notice also that $-\infty-(+\infty)$ is not a valid nonnegative extended-real difference; it is ruled out by $a<b$ and monotonicity.

### Condition (i): finite additivity

Suppose, after discarding any empty pieces, that

$$
(a,b]=\mathop{\dot\bigcup}_{i=1}^n(a_i,b_i].
$$

After relabelling the intervals from left to right, there can be neither gaps nor overlaps, so

$$
a_1=a,
\qquad
b_n=b,
\qquad
a_i=b_{i-1}\quad(2\leq i\leq n).
$$

Therefore the sum telescopes:

$$
\sum_{i=1}^n\mu((a_i,b_i])
=\sum_{i=1}^n\bigl(F(b_i)-F(a_i)\bigr)
=F(b)-F(a)
=\mu((a,b]).
$$

The same conclusion holds in the extended-real boundary cases. Hence condition (i) of Theorem 1.1.9 holds.

### Condition (ii): countable subadditivity

First suppose the interval on the left has finite endpoints:

$$
-\infty<a<b<+\infty,
\qquad
(a,b]\subseteq\bigcup_{i=1}^{\infty}(c_i,d_i].
$$

Durrett's claim that we may assume the covering intervals have finite endpoints is justified as follows. Define

$$
I_i:=(c_i,d_i]\cap(a,b].
$$

Then $I_i$ is either empty or

$$
I_i=\bigl(\max\{c_i,a\},\,\min\{d_i,b\}\bigr].
$$

Since $a$ and $b$ are finite, every nonempty $I_i$ has finite endpoints, even when $c_i=-\infty$ or $d_i=+\infty$. The $I_i$ still cover $(a,b]$. Also $I_i\subseteq(c_i,d_i]$, so monotonicity from Lemma 1.1.10(b), in the case of one covering set, gives

$$
\mu(I_i)=\bar\mu(I_i)
\leq\bar\mu((c_i,d_i])
=\mu((c_i,d_i]).
$$

Thus replacing the original intervals by the $I_i$ does not weaken the desired covering inequality. Rename the nonempty $I_i$ as $(a_i,b_i]$, so now

$$
-\infty<a_i<b_i<+\infty.
$$

Fix $\varepsilon>0$. By right continuity of $F$ at $a$, choose $\delta>0$, small enough that $a+\delta<b$, such that

$$
F(a+\delta)<F(a)+\varepsilon.
$$

For every $i$, by right continuity at $b_i$, choose $\eta_i>0$ such that

$$
F(b_i+\eta_i)<F(b_i)+\varepsilon 2^{-i}.
$$

Why exactly these shifts? The right endpoints $b_i$ are enlarged so that the covering sets become open, while the left endpoint $a$ is moved to the right so that the set being covered becomes compact. Indeed,

$$
[a+\delta,b]
\subseteq(a,b]
\subseteq\bigcup_{i=1}^{\infty}(a_i,b_i]
\subseteq\bigcup_{i=1}^{\infty}(a_i,b_i+\eta_i).
$$

The set $[a+\delta,b]$ is compact and the intervals $(a_i,b_i+\eta_i)$ are open. By Heine--Borel, there is a finite set of indices $i_1,\ldots,i_J$ such that

$$
[a+\delta,b]
\subseteq\bigcup_{j=1}^J(a_{i_j},b_{i_j}+\eta_{i_j}).
$$

Hence

$$
(a+\delta,b]
\subseteq\bigcup_{j=1}^J(a_{i_j},b_{i_j}+\eta_{i_j}].
$$

These half-open intervals lie in $\mathcal S_1\subseteq\overline{\mathcal S_1}$, and their union is finite. Lemma 1.1.10(b) therefore gives

$$
F(b)-F(a+\delta)
\leq
\sum_{j=1}^J
\bigl(F(b_{i_j}+\eta_{i_j})-F(a_{i_j})\bigr).
$$

Every term is nonnegative, so we may bound the selected finite sum by the entire series:

$$
F(b)-F(a+\delta)
\leq
\sum_{i=1}^{\infty}
\bigl(F(b_i+\eta_i)-F(a_i)\bigr).
$$

By the choices of $\delta$ and $\eta_i$,

$$
F(b)-F(a)
<F(b)-F(a+\delta)+\varepsilon
$$

and

$$
\sum_{i=1}^{\infty}
\bigl(F(b_i+\eta_i)-F(a_i)\bigr)
\leq
\sum_{i=1}^{\infty}
\bigl(F(b_i)-F(a_i)\bigr)
+\varepsilon\sum_{i=1}^{\infty}2^{-i}.
$$

Since $\sum_{i=1}^{\infty}2^{-i}=1$, we obtain

$$
\mu((a,b])
=F(b)-F(a)
\leq
2\varepsilon+
\sum_{i=1}^{\infty}\mu((a_i,b_i]).
$$

Because $\varepsilon>0$ is arbitrary,

$$
\mu((a,b])
\leq
\sum_{i=1}^{\infty}\mu((a_i,b_i]).
$$

Finally, remove the finite-endpoint restriction on $(a,b]$. Keep each finite endpoint fixed; approximate only an infinite endpoint. Choose finite intervals $(A_n,B_n]\subseteq(a,b]$ so that

$$
A_n\downarrow-\infty\quad\text{if }a=-\infty,
\qquad
B_n\uparrow+\infty\quad\text{if }b=+\infty.
$$

For every $n$, the result already proved gives

$$
F(B_n)-F(A_n)
\leq
\sum_{i=1}^{\infty}\bigl(F(b_i)-F(a_i)\bigr).
$$

By the definitions of $F(-\infty)$ and $F(+\infty)$,

$$
F(B_n)-F(A_n)\longrightarrow F(b)-F(a).
$$

The right-hand side is constant in $n$, so taking the limit gives condition (ii) in full generality. There is no need to put an extra, useless limit around the series on the right.

Theorem 1.1.9 now extends $\mu$ to a measure on $\sigma(\mathcal S_1)=\mathcal B(\mathbb R)$. Finally,

$$
\mathbb R=\bigcup_{n=1}^{\infty}(-n,n]
$$

and

$$
\mu((-n,n])=F(n)-F(-n)<\infty,
$$

so the extension is $\sigma$-finite. The uniqueness conclusion in Theorem 1.1.9 therefore applies. $\square$
