---
layout: durrett
title: "For Preparing Exercise 3.2.9: An IVT Warm-up"
date: 2026-11-07
permalink: /durrett-waffling/ivt-warm-up-exercise-3-2-9/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "A short real-analysis application of the intermediate value theorem while preparing Durrett Exercise 3.2.9."
---

For preparing Exercise 3.2.9 on uniform convergence of distribution functions \(F_n\) to a continuous \(F\), I want to do a real-analysis application of the intermediate value theorem real quick.

So recall IVT: suppose \(f:D\to\mathbb R\) and \(f\) is continuous on some \([a,b]\subseteq D\subseteq\mathbb R\). Suppose for some \(s\) that \(f(a)<s<f(b)\). Then IVT says there exists some \(x_0\in(a,b)\) such that \(f(x_0)=s\). Note the use of round and closed square brackets in stating the theorem.

Now we want to show that if, additionally, \(f:\mathbb R\to\mathbb R\) is continuous on \(\mathbb R\), \(f(x)\in[0,1]\) for all \(x\in\mathbb R\), and

$$
\lim_{x\to+\infty}f(x)=1,\qquad
\lim_{x\to-\infty}f(x)=0,
$$

then IVT should give us:

$$
\forall y\in(0,1),\ \exists x\in\mathbb R:\ f(x)=y.
$$

*Proof.* Fix some \(y\in(0,1)\). Since \((0,1)\) is open in \(\mathbb R\), there exists \(\delta>0\) such that

$$
y\in(y-\delta,y+\delta)\subseteq(0,1).
$$

Since \(\lim_{x\to+\infty}f(x)=1\) and \(\lim_{x\to-\infty}f(x)=0\), choose

$$
\varepsilon':=\frac12\min\{1-(y+\delta),\,y-\delta\}>0.
$$

Then there exists \(M>0\), large enough for both limits, such that

$$
\forall x\in(M,+\infty),\quad |1-f(x)|=1-f(x)<\varepsilon',
$$

$$
\forall x\in(-\infty,-M),\quad |f(x)-0|=f(x)<\varepsilon',
$$

where we use \(0\leq f(x)\leq1\). This implies

$$
f(M+1)>y+\delta,
$$

$$
f(-M-1)<y-\delta,
$$

or collectively,

$$
f(-M-1)<y-\delta<y<y+\delta<f(M+1).
$$

Now since \(f\) is continuous on the whole \(\mathbb R\), it is also continuous on \([-M-1,M+1]\subseteq\mathbb R\). Here \(a=-M-1\) and \(b=M+1\) in the IVT stated above. So we apply IVT to get that there exists \(x_y\in(-M-1,M+1)\subseteq\mathbb R\) such that \(f(x_y)=y\).

Note that above we actually did **not** use monotonicity.
