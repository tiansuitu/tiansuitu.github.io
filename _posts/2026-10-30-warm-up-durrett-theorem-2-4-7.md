---
layout: durrett
title: "A Quick Warm-up for Durrett's Theorem 2.4.7 (p. 67)"
date: 2026-10-30
permalink: /durrett-waffling/warm-up-durrett-theorem-2-4-7/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "A quick warm-up showing the renewal inequalities T(N_t) <= t < T(N_t + 1)."
---

Referring to Durrett, 5th ed., Theorem 2.4.7, p. 67,

$$
\begin{aligned}
T(n) &= \sum_{i=1}^n X_i, \\
N_t &= \sup\{n\in\mathbb N:T(n)\leq t\}.
\end{aligned}
$$

Just as a quick warm-up, show

$$
T(N_t)\leq t<T(N_t+1).
$$
*Proof.* Let \\(A\_t:=\\{n\in\mathbb N:T(n)\leq t\\}\\). Assume \\(A\_t\neq\varnothing\\) and \\(N\_t<\infty\\).

- First show \\(T(N\_t)\leq t\\).

  The easiest intuition is that \\(A\_t\subseteq\mathbb N\\) and \\(N\_t<\infty\\), so the supremum over an upper-bounded subset of \\(\mathbb N\\) is exactly the maximum. Thus \\(N\_t=\max A\_t\in A\_t\\), which implies \\(T(N\_t)\leq t\\). But to be more rigorous and more fun, as hinted by ChatGPT:

  By the definition of supremum, choose \\(\epsilon=1\\) to utilise the space of natural numbers. There exists \\(m\in A\_t\\) such that

  $$
  N_t-1<m\leq N_t.
  $$

  We want to show that \\(m\\) is an upper bound for \\(A\_t\\), i.e.

  $$
  \forall n\in A_t,\quad m\geq n.
  $$

  Suppose by contradiction that there exists \\(n\in A\_t\\) such that \\(m<n\\). Since \\(m,n\in\mathbb N\\), we have \\(m+1\leq n\\). Since \\(n\in A\_t\\), we also have \\(n\leq N\_t\\). On the other hand, \\(N\_t-1<m\\) implies \\(N\_t<m+1\\). Thus

  $$
  N_t<m+1\leq n\leq N_t,
  $$

  a contradiction.

  Thus, we are now safe that

  $$
  \forall n\in A_t,\quad m\geq n.
  $$

  So \\(m\\) is an upper bound for \\(A\_t\\). By the definition of supremum, \\(N\_t\\) is the least upper bound, so

  $$
  N_t\leq m.
  $$

  Combined with \\(m\leq N\_t\\), we have

  $$
  N_t=m\in A_t\implies T(N_t)\leq t.
  $$

- Now the easiest part: show \\(t<T(N\_t+1)\\). Since \\(N\_t\\) is an upper bound for \\(A\_t\\) and \\(N\_t+1>N\_t\\), we have

  $$
  N_t+1\notin A_t
  \iff T(N_t+1)\not\leq t
  \iff t<T(N_t+1).
  $$

Therefore,

$$
T(N_t)\leq t<T(N_t+1).
$$

p.68: since $T_n<+\infty$, for all $n$, we have $N_t \uparrow +\infty$ as $t\to \infty$:

*Proof.* Fix $M>0$, and choose $m_M>M$. Since $T(m_M)<+\infty$ we can pick $T(m_M)\in \mathbb R$ such that for all $t\geq T(m_M)$, 

$$
N_{t}\geq N_{T(m_M)} = \sup\{n\in\mathbb N:T(n)\leq T(m_M)\}\geq m_M>M,
$$

thus $N_{t}>M$ for any arbitrary $M$ by choosing large enough $t$.  Remark. More detailed as $T_n<\infty$ a.e. not everywhere: suppose $T_n<\infty$ a.s. for every $n\in\mathbb N$. Let
$\Omega_0:=\bigcap_{n=1}^{\infty}\{\omega:T_n(\omega)<\infty\},$ so that $\mathbb P(\Omega_0)=1$. Fix $\omega\in\Omega_0$ and $M>0$. Choose $m\in\mathbb N$ with $m>M$ and set $t_0=T_m(\omega)<\infty$. Then, for all $t\ge t_0$, $N_t(\omega)\ge N_{t_0}(\omega)=\sup\{n\in\mathbb N:T_n(\omega)\le t_0\} \ge m>M$. Since $M>0$ is arbitrary and $N_t$ is nondecreasing in $t$, we conclude that $N_t\uparrow+\infty$ as $t\to\infty$ a.s.