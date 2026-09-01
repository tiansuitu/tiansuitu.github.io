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

Lemma 1.1.10 is more above FINITE (sub)additivity rather than about countable (sub)additivity. Lemma 1.1.10(b) is essentially Theorem 1.1.1(i)--(ii) repeated for $\bar\mu$ on $\overline{\mathcal S}$: first, $A\subseteq B$ gives monotonicity $\bar\mu(A)\le \bar\mu(B)$; then disjointifying a finite cover gives $\bar\mu(A)\le \sum_{i=1}^n \bar\mu(B_i)$. Thus it is the usual $\text{additivity}\Rightarrow\text{monotonicity}\Rightarrow\text{finite subadditivity}$ argument.

Later on, for Theorem 1.1.9 verification of conditions (i) and (ii), only Lemma 1.1.10(b) is used. Lemma 1.1.10(a) is just used to prove (b).

For proof of Theorem 1.1.4 on page 5,

- **Compactness / finite subcover.**
  Let $(X,\mathcal T)$ be a topological space and let $K\subseteq X$ be compact. If
  $\{O_i\}_{i\in I}\subseteq\mathcal T$ is an open cover of $K$, i.e.
  $K\subseteq\bigcup_{i\in I}O_i$, where $I$ may be arbitrary, then there exists
  a finite subset $J=\{i_1,\ldots,i_m\}\subseteq I$ such that
  $K\subseteq\bigcup_{i\in J}O_i$.

  In Durrett's proof, $K=[a+\delta,b]$, which is compact in $\mathbb R$, and the
  intervals $(a_i,b_i+\eta_i)$ form an open cover of $K$.

- **Right continuity of a nondecreasing function.**
  If $F$ is right continuous at $x_0$, then for every $\varepsilon>0$ there exists
  $\gamma_\varepsilon>0$ such that
  $0<x-x_0<\gamma_\varepsilon$ implies
  $|F(x)-F(x_0)|<\varepsilon$.
  Since $F$ is nondecreasing, for $x>x_0$ we have
  $F(x)-F(x_0)\geq 0$, so
  $0\leq F(x)-F(x_0)<\varepsilon$.
  Hence, choosing any $\delta_\varepsilon\in(0,\gamma_\varepsilon)$, for example
  $\delta_\varepsilon=\gamma_\varepsilon/2$, gives
  $$F(x_0+\delta_\varepsilon)<F(x_0)+\varepsilon$$

Durrett defines the semialgebra as $\mathcal S_1=\{\varnothing\}\cup\{(a,b]:-\infty\le a<b\le\infty\}$. Hence $\varnothing$ is included separately, since the interval notation only allows $a<b$. For Theorem 1.1.4, the set function should therefore be understood as $\mu(\varnothing):=0$ and $\mu((a,b]):=F(b)-F(a)$ for $a<b$. Thus the hypothesis $\mu(\varnothing)=0$ in Theorem 1.1.9 is satisfied by definition.


Why in Theorem 1.1.9 only require countable SUBadditivity, no need countable $+\infty$-wise additivity?

Suppose $S=\bigsqcup_{i=1}^\infty S_i$ with $S,S_i\in\mathcal S$. Condition (i), together with Lemma 1.1.10, already gives the reverse inequality. Indeed, for every $n$,
$$
\bigsqcup_{i=1}^n S_i\subseteq S,
$$
so by Lemma 1.1.10(a)--(b),
$$
\sum_{i=1}^n\mu(S_i)
=
\bar\mu\left(\bigsqcup_{i=1}^nS_i\right)
\leq
\bar\mu(S)
=
\mu(S).
$$
Letting $n\to\infty$ gives
$$
\sum_{i=1}^\infty\mu(S_i)\leq\mu(S).
$$
Therefore Theorem 1.1.9 only needs to assume the opposite inequality
$$
\mu(S)\leq\sum_{i=1}^\infty\mu(S_i),
$$
and combining the two inequalities gives countable additivity
$$
\mu(S)=\sum_{i=1}^\infty\mu(S_i).
$$


*Proof of Theorem 1.1.4.*

*Proof.*

- First note $\mu$ is allowed be on extended real lines, for example for Lesbesgue meausre $\mu(\mathbb R)=+\infty$, with $F(x) = x$, so we can even allow for $F(+\infty)=+\infty$, where

  $$
  F(+\infty) = \lim_{x\uparrow +\infty} F(x) , \qquad F(-\infty) = \lim_{x\downarrow -\infty}F(x)
  $$

- Since $$F:\mathbb R\to\mathbb R, \qquad \forall_{x\in \mathbb R}\, F(x)\in \mathbb R$$ is finite-valued and nondecreasing, we have
  $F(-\infty)=\inf_{x\in\mathbb R}F(x)$. Hence $F(-\infty)=+\infty$ is impossible, because that would force $F(x)=+\infty$ for every $x\in\mathbb R$. Similarly, $F(+\infty)=\sup_{x\in\mathbb R}F(x)$ so $F(+\infty)\neq -\infty$ which would force $F(x)=-\infty\forall x\in \mathbb R$. Thus

  $$
  F(-\infty)<+\infty, \qquad F(+\infty) >-\infty
  $$

- we want to rule out $(+\infty)-(+\infty)$ or $(-\infty)-(-\infty)$. The other combinations $(+\infty) - (-\infty)$ and $(-\infty) - (+\infty)$ are defined in the extended real numbers, but $(-\infty)-(+\infty)=-\infty$ is not an allowed value of a measure. In any case, $(-\infty)-(+\infty)$ is automatically ruled out since $F$ is nondecreasing and hence $F(a)\leq F(b)$ whenever $a<b$. Thus

  $$
  \mu: \mathcal S \to [0,+\infty].
  $$

- To prove (ii) we want finte end points $-\infty<a<b<+\infty$ of $(a,b]$ so later when shifted/enlarged can use compactness

- Without loss of generality WLOG, let

  $$
  (a,b]\subseteq \cup_{i=1}^\infty (a_i,b_i], \qquad -\infty< a_i<b_i<+\infty
  $$

  - Here WLOG means the following, suppose we have proven that for $-\infty<a_i<b_i<+\infty$,
    $
    \mu((a,b])\leq \sum_{i=1}^\infty \mu((a_i,b_i])
    $. Now what if we are given that $(a,b]\subseteq \cup_{i\geq 1}(c_i,d_i]$ where $-\infty\leq c_i<d_i\leq +\infty$. Then define

    $$
    I_i = (a,b]\cap (c_i,d_i] \in \mathcal S.
    $$

    Each nonempty $I_i$ has finite end-points (recall $\mathcal S$ preserves intersections!); empty $I_i$'s can simply be discarded.

  - Thus, recycle above WLOG result, since $(a,b]\subseteq \cup_{i\geq 1} I_i$, we have $\mu((a,b])\leq \sum_{i\geq 1}\mu(I_i)$. Remain to show $\sum_{i\geq 1}\mu(I_i)\leq \sum_{i\geq 1}\mu((c_i,d_i])$:

    *Proof.*

    $\mathcal S\subseteq  \mathcal{\overline{S}}$, so using Lemma 1.1.10(b) (base case $n=1$), $I_i\subseteq (c_i,d_i]$ implies

    $$
    \bar{\mu}(I_i)\leq \bar{\mu}((c_i,d_i]),
    \qquad
    I_i,(c_i,d_i]\in \mathcal S,
    \qquad \forall i\in \mathbb N.
    $$

    Take finite partial sums and then limits, so

    $$
    \sum_{i=1}^\infty\bar\mu(I_i)
    \leq
    \sum_{i=1}^\infty\bar\mu((c_i,d_i]).
    $$

    Then $\bar{\mu}\equiv \mu$ when applied to sets in $\mathcal S$ by defn of extension.

- anyways so now consider $-\infty<a<b<+\infty$ and $-\infty<a_i<b_i<+\infty$.

  Our aim now is to reduce the RHS of $\subseteq$ from countable union to finite union. so use heine borel. Heine--Borel can only be applied to a compact set that is actually covered by the given open cover. We are given

  $$
  (a,b]\subseteq \cup_{i\geq 1} (a_i,b_i]
  $$

  We now examine both left and right end points of $(a,b]$ for a) compactness, and of each $(a_i,b_i]$ for b) openness for open cover. so that later can use Heine-Borel:

  1. Right end: we can enlarge $b_i$ to some $b_i+\eta_i$ for some chosen $\eta_i>0$ and get open cover prepared for later Heine-Borel:

     $$
     (a,b]\subseteq \cup_{i\geq 1} (a_i,b_i+\eta_i)
     $$

     also $b]$ is consistent with compactness $[.,.]$ interval design

  2. Left end: $(a_i,$ already openness on the left, but this is not compact, and we are NOT sure whether slightly enlarged $[a,b]$ can be covered by open sets. so instead of open covering whole $(a,b]$, we will later open cover $(a+\delta,b]$ and in fact, for compactness,

     $$
     [a+\delta,b],
     $$

     for some $\delta>0$, and we are indeed sure that there exists open cover for this because

     $$
     (a+\delta, b]\subseteq[a+\delta, b]\subseteq (a,b]\subseteq \cup_{i\geq 1} (a_i,b_i]\subseteq \cup_{i\geq 1} (a_i,b_i+\eta_i)
     $$

  3. To summarise, we only open cover a subset inside of $(a,b]$, later we will control $\delta$ to make it small. Also note that here $(.,.)$ may NOT be in $\mathcal S$, above are just pure subset relations, have not applied $\mu$ on them yet so no worry.

- Fix $\epsilon>0$. By right continuity, choose $\delta>0$ and $\eta_i>0$, $i\in\mathbb N$, such that

  $$
  F(a+\delta)<F(a)+\epsilon,
  \qquad
  F(b_i+\eta_i)<F(b_i)+\epsilon 2^{-i}.
  $$

  Using compactness of $[a+\delta, b]$ and openness of $(a_i, b_i+\eta_i)$, by Heine-Borel, there exists finite subcover indexed by $i_j,\forall j=1,\ldots,J$, $\{i_1,\ldots,i_J\}\subseteq \mathbb N$, such that

  $$
  [a+\delta, b]\subseteq \cup_{i= 1}^\infty (a_i,b_i+\eta_i)
  \implies
  [a+\delta, b]\subseteq \cup_{j= 1}^J (a_{i_j},b_{i_j}+\eta_{i_j}).
  $$

  <!--
  now let
  $$
  \alpha_j:= a_{i_j}, \qquad \beta_j := b_{i_j}+\eta_{i_j}, \qquad j=1,\ldots,J
  $$
  -->

- Thus, since $(a+\delta,b]\subseteq [a+\delta,b]$, and $ \cup_{j= 1}^J (a_{i_j},b_{i_j}+\eta_{i_j})\subseteq \cup_{j= 1}^J (a_{i_j},b_{i_j}+\eta_{i_j}]$, we have:

  $$
  (a+\delta,b]\subseteq \cup_{j= 1}^J (a_{i_j},b_{i_j}+\eta_{i_j}].
  $$

  Since $(.,.]\in \mathcal S\subseteq \mathcal{\overline{S}}$ which is an algebra including finite unions $\cup_{j=1}^J$, apply Lemma 1.1.10(b) finite subadditivity:

  $$
  \bar{\mu} ((a+\delta,b])\leq \sum_{j=1}^J
  \bar{\mu}\left((a_{i_j},b_{i_j}+\eta_{i_j}]
  \right)
  $$

  and since $\mu(S)\equiv \bar \mu(S)$ forall $S\in \mathcal S$,

  $$
  \implies {\mu} ((a+\delta,b])\leq \sum_{j=1}^J
  {\mu}\left((a_{i_j},b_{i_j}+\eta_{i_j}]
  \right)
  \leq \sum_{i=1}^\infty
  {\mu}\left((a_{i},b_{i}+\eta_{i}]
  \right)
  $$

  since each $\mu(.)\geq 0$. then finally,

  $$
  \implies F(b) - F(a+\delta) \leq \sum_{i=1}^\infty
  [
  F(b_{i}+\eta_{i})- F(a_{i})].
  $$

- then use continuity on the choice of $\delta$ and $\eta_i$. Since

  $$
  F(a+\delta)<F(a)+\epsilon
  $$

  we have

  $$
  F(b)-F(a)
  <
  F(b)-F(a+\delta)+\epsilon.
  $$

  Also,

  $$
  F(b_i+\eta_i)-F(a_i)
  <
  F(b_i)-F(a_i)+\epsilon2^{-i}.
  $$

  Therefore,

  $$
  F(b)-F(a)
  \leq
  \sum_{i=1}^\infty [F(b_i)-F(a_i)]
  +
  \epsilon
  +
  \sum_{i=1}^\infty\epsilon2^{-i}
  =
  \sum_{i=1}^\infty [F(b_i)-F(a_i)]
  +2\epsilon.
  $$

  Since $\epsilon>0$ is arbitrary,

  $$
  F(b)-F(a)
  \leq
  \sum_{i=1}^\infty [F(b_i)-F(a_i)].
  $$

- To remove the finite-endpoint restriction, work at the level of $F$, not by continuity of $\mu$ as not guaranteed. If $a=-\infty$, choose finite $A_n\downarrow-\infty$, so $F(A_n)\to F(-\infty)=F(a)$ by definition. If $b=+\infty$, choose finite $B_n\uparrow+\infty$, so $F(B_n)\to F(+\infty)=F(b)$ by definition. If $a>-\infty$, keep $A_n=a$ fixed, and if $b<\infty$, keep $B_n=b$ fixed rather than take $B_n\uparrow b$, since right continuity does not imply $F(B_n)\to F(b)$ from the left; the limit could be $F(b-)$. Thus one only approximates the infinite endpoints by finite ones, and then passes to the limit in the expressions $F(B_n)-F(A_n)$.

  For every $n$, $(A_n,B_n]\subseteq(a,b]$, so the finite-endpoint result gives

  $$
  F(B_n)-F(A_n)
  \leq
  \sum_{i=1}^\infty (F(b_i)-F(a_i)).
  $$

  Therefore,

  $$
  \mu((a,b])
  =
  F(b)-F(a)
  =
  \lim_{n\to\infty}\bigl(F(B_n)-F(A_n)\bigr)
  \leq
  \sum_{i=1}^\infty (F(b_i)-F(a_i)).
  $$

  Note that there is no need for a limit on the RHS, since it does not depend on $n$.
