---
layout: durrett
title: "Waffling on the Weak Law: Truncation, Rare Extremes, and the Cauchy Distribution"
date: 2026-11-04
permalink: /durrett-waffling/weak-law-truncation-rare-extremes-cauchy/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "Reading Durrett's Theorems 2.2.11, 2.2.12, and 2.2.14 as one story: eliminate rare extremes, control the truncated fluctuations, and ask whether the moving center converges."
---

*Reading notes on Durrett, Probability: Theory and Examples, 5th edition, Section 2.2.3 (pp. 53–56).*

## The question that made the three theorems click

When I first read the truncation argument for the weak law of large numbers (WLLN), I thought we were trying to prove the usual statement

$$
\frac{S_n}{n}\xrightarrow{\mathbb P}\mathbb E[X_1],
\qquad S_n=X_1+\cdots+X_n.
$$

But Durrett does **not** begin there. In Theorem 2.2.11, he proves that a normalized sum is close *in probability to a centering term that changes with* \(n\). At that stage, we do not know whether these centers approach anything at all.

This suggests a useful way to read the progression:

$$
\boxed{
\text{control the extreme observations}
\;\longrightarrow\;
\text{control fluctuations about a moving center}
\;\longrightarrow\;
\text{identify a fixed limit}.
}
$$

The sequence of results is

$$
\text{Theorem 2.2.11}
\;\longrightarrow\;
\text{Theorem 2.2.12}
\;\longrightarrow\;
\text{Theorem 2.2.14}.
$$

The Cauchy distribution then tells us what can go wrong when the extreme events are not rare *enough*.

Throughout, random variables are defined on a probability space \((\Omega,\mathcal F,\mathbb P)\). Convergence in probability means that, for every \(\varepsilon>0\), the probability of an error larger than \(\varepsilon\) tends to zero.

## 1. Why the rate \(x\mathbb P(|X_1|>x)\) matters

Of course, for any finite real-valued random variable \(X_1\),

$$
\mathbb P(|X_1|>x)\longrightarrow 0
\qquad (x\to\infty).
$$

But that statement alone is too weak for a law of large numbers. We are not drawing just one observation: at sample size \(n\), we have **\(n\) opportunities to see an extreme observation**.

For i.i.d. \(X_1,\ldots,X_n\), the union bound gives

$$
\begin{aligned}
\mathbb P\left(\max_{1\leq k\leq n}|X_k|>n\right)
&=\mathbb P\left(\bigcup_{k=1}^{n}\{|X_k|>n\}\right)\\
&\leq\sum_{k=1}^{n}\mathbb P(|X_k|>n)\\
&=n\mathbb P(|X_1|>n).
\end{aligned}
$$

An observation of order \(n\) can contribute an amount of order one to the sample average. So the meaningful question is not merely whether the probability of one such observation goes to zero; it is whether the probability of **at least one among the first \(n\)** goes to zero.

This is the intuition behind the tail condition in Theorem 2.2.12:

$$
\boxed{x\mathbb P(|X_1|>x)\longrightarrow0.}
$$

The factor \(x\) is crucial. It compares the frequency of very large observations with the number of opportunities to encounter them at the corresponding averaging scale. The condition is sufficient to make the chance that truncation changes *any* of the \(n\) observations vanish.

Does a finite first absolute moment imply this condition? Yes. For \(x>0\),

$$
x\mathbf 1_{\{|X_1|>x\}}
\leq |X_1|\mathbf 1_{\{|X_1|>x\}},
$$

and hence

$$
0\leq x\mathbb P(|X_1|>x)
\leq \mathbb E\!\left[|X_1|\mathbf 1_{\{|X_1|>x\}}\right]
\longrightarrow0
$$

provided \(\mathbb E|X_1|<\infty\). The last step is the dominated convergence theorem: the integrand tends pointwise to zero and is bounded by the integrable variable \(|X_1|\).

I find this a useful interpretation of integrability: **finite absolute expectation says that not only is the tail probability small, but the expected magnitude carried by the far tail must disappear**.

It is important, however, not to reverse that implication. The rate condition can hold even if \(\mathbb E|X_1|=\infty\); we will come back to that.

## 2. Theorem 2.2.11: a general truncation machine

This theorem is more general than the usual i.i.d. setting. For each \(n\), take an independent row \(X_{n,1},\ldots,X_{n,n}\), not necessarily identically distributed. Choose \(b_n>0\) with \(b_n\to\infty\), and define

$$
\overline X_{n,k}
=X_{n,k}\mathbf 1_{\{|X_{n,k}|\leq b_n\}},
\qquad
S_n=\sum_{k=1}^n X_{n,k},
\qquad
a_n=\sum_{k=1}^n\mathbb E[\overline X_{n,k}].
$$

Durrett assumes

$$
\tag{i}
\sum_{k=1}^n\mathbb P(|X_{n,k}|>b_n)\longrightarrow0
$$

and

$$
\tag{ii}
\frac{1}{b_n^2}
\sum_{k=1}^n\mathbb E[\overline X_{n,k}^{\,2}]
\longrightarrow0.
$$

The conclusion is

$$
\boxed{\frac{S_n-a_n}{b_n}\xrightarrow{\mathbb P}0.}
$$

These two hypotheses do different jobs.

**Condition (i): truncation almost never changes the row.** Let \(\overline S_n=\sum_{k=1}^n\overline X_{n,k}\). Then

$$
\mathbb P(S_n\neq\overline S_n)
\leq\sum_{k=1}^n\mathbb P(|X_{n,k}|>b_n)
\longrightarrow0.
$$

**Condition (ii): the truncated sum has negligible fluctuations on the \(b_n\) scale.** Since \(a_n=\mathbb E[\overline S_n]\), Chebyshev's inequality and independence give

$$
\begin{aligned}
\mathbb P\left(
\left|\frac{\overline S_n-a_n}{b_n}\right|>\varepsilon
\right)
&\leq\frac{\operatorname{Var}(\overline S_n)}{\varepsilon^2b_n^2}\\
&=\frac{\sum_{k=1}^n\operatorname{Var}(\overline X_{n,k})}
{\varepsilon^2b_n^2}\\
&\leq\frac{\sum_{k=1}^n\mathbb E[\overline X_{n,k}^{\,2}]}
{\varepsilon^2b_n^2}
\longrightarrow0.
\end{aligned}
$$

The original sum and its truncated version therefore differ with vanishing probability, and the truncated version concentrates around \(a_n\).

Here was an important correction to my initial reading: **each \(a_n\) is finite**, because each \(\overline X_{n,k}\) is bounded by \(b_n<\infty\) and the row has finitely many entries. What may fail is the existence of a *limit* for \(a_n/b_n\). The theorem does not assert that such a limit exists.

Also, identical distributions are nowhere required in Theorem 2.2.11. In fact, the proof only needs **pairwise independence within each row** for the variance identity: mutual independence is stronger than necessary for this argument. The union bound itself does not require any independence.

## 3. Theorem 2.2.12: specialize to i.i.d. variables

Now suppose \(X_1,X_2,\ldots\) are i.i.d. and

$$
x\mathbb P(|X_1|>x)\longrightarrow0.
$$

Durrett chooses \(X_{n,k}=X_k\) and \(b_n=n\). With

$$
\mu_n=\mathbb E\left[X_1\mathbf 1_{\{|X_1|\leq n\}}\right],
$$

we have \(a_n=n\mu_n\). Consequently, the conclusion of Theorem 2.2.11 becomes

$$
\boxed{\frac{S_n}{n}-\mu_n\xrightarrow{\mathbb P}0.}
$$

Why are its two hypotheses satisfied?

First, for condition (i),

$$
\sum_{k=1}^n\mathbb P(|X_k|>n)
=n\mathbb P(|X_1|>n)\longrightarrow0.
$$

Second, condition (ii) reduces to

$$
\frac{1}{n}
\mathbb E\left[X_1^2\mathbf 1_{\{|X_1|\leq n\}}\right]
\longrightarrow0.
$$

This is where Durrett's Lemma 2.2.13 (the tail-integral formula for moments) enters. Writing \(Y_n=|X_1|\mathbf 1_{\{|X_1|\leq n\}}\),

$$
\begin{aligned}
\mathbb E[Y_n^2]
&=\int_0^\infty 2t\,\mathbb P(Y_n>t)\,dt\\
&\leq\int_0^n 2t\,\mathbb P(|X_1|>t)\,dt.
\end{aligned}
$$

Define \(g(t)=2t\mathbb P(|X_1|>t)\). Our tail assumption says \(g(t)\to0\), so its averages also tend to zero:

$$
0\leq\frac{\mathbb E[Y_n^2]}{n}
\leq\frac1n\int_0^n g(t)\,dt
\longrightarrow0.
$$

For completeness, this last implication is simply the continuous Cesàro principle: split the integral at a fixed large \(M\); the contribution from \([0,M]\), divided by \(n\), vanishes, and the average over \([M,n]\) is arbitrarily small because \(g(t)\) is small for all \(t\geq M\).

Thus Theorem 2.2.12 identifies a *moving, truncated mean* \(\mu_n\) as the right center for \(S_n/n\), even without assuming that the untruncated expectation exists.

This is an important kind of weak law in its own right: it is a statement of **asymptotic concentration relative to a deterministic sequence**, not necessarily convergence to a fixed deterministic constant.

## 4. Theorem 2.2.14: why finite first moment finally gives the familiar WLLN

Now impose the stronger condition

$$
\mathbb E|X_1|<\infty
$$

and write \(\mu=\mathbb E[X_1]\). There are now two separate conclusions:

1. The tail-rate condition holds, as shown earlier; Theorem 2.2.12 therefore yields \(S_n/n-\mu_n\xrightarrow{\mathbb P}0\).
2. The moving centers actually converge:

$$
\mu_n
=\mathbb E\left[X_1\mathbf 1_{\{|X_1|\leq n\}}\right]
\longrightarrow \mathbb E[X_1]=\mu
$$

by dominated convergence, since \(X_1\mathbf 1_{\{|X_1|\leq n\}}\to X_1\) almost surely and its absolute value is bounded by the integrable \(|X_1|\).

Finally,

$$
\frac{S_n}{n}-\mu
=
\underbrace{\left(\frac{S_n}{n}-\mu_n\right)}_{\xrightarrow{\mathbb P}0}
+
\underbrace{(\mu_n-\mu)}_{\longrightarrow0},
$$

so

$$
\boxed{\frac{S_n}{n}\xrightarrow{\mathbb P}\mu.}
$$

This is Theorem 2.2.14, the familiar i.i.d. WLLN.

The logical roles are worth separating. **The tail-rate condition handles the rare extremes and the truncated fluctuations; integrability also makes the moving truncated mean converge to the ordinary finite mean.**

We do not need a finite second moment of \(X_1\): truncation makes a second-moment bound available at each \(n\), and the normalization makes it small.

## 5. Cauchy: why averaging does not wash out the extremes

Durrett follows the WLLN with the Cauchy example (Example 2.2.15). Suppose the \(X_k\) are i.i.d. *standard Cauchy*, with density

$$
f(x)=\frac{1}{\pi(1+x^2)}.
$$

The absolute tail behaves as

$$
\mathbb P(|X_1|>x)
=\frac{2}{\pi}\int_x^\infty\frac{dt}{1+t^2}
\sim\frac{2}{\pi x},
\qquad x\to\infty.
$$

Therefore

$$
x\mathbb P(|X_1|>x)\longrightarrow\frac2\pi\neq0.
$$

The probability of an observation larger than the averaging scale \(n\) is of order \(1/n\). With \(n\) opportunities for one, an extreme observation remains a real possibility. The rare-event argument of Theorem 2.2.12 breaks down.

There is also a striking exact result. The characteristic function of a standard Cauchy variable is

$$
\varphi_{X_1}(t)=e^{-|t|}.
$$

Independence gives

$$
\varphi_{S_n/n}(t)
=\prod_{k=1}^n\varphi_{X_k}(t/n)
=\bigl(e^{-|t|/n}\bigr)^n
=e^{-|t|}.
$$

Thus, for **every** \(n\),

$$
\boxed{\frac{S_n}{n}\overset{d}{=}X_1.}
$$

The sample mean has exactly the same nondegenerate Cauchy distribution as one observation. Averaging has not narrowed the distribution at all.

For any candidate constant \(c\), convergence in probability to \(c\) would imply convergence in distribution to the point mass at \(c\). But the distribution of \(S_n/n\) is always the same nondegenerate Cauchy law. Hence

$$
\frac{S_n}{n}\not\xrightarrow{\mathbb P}c
\qquad\text{for every }c\in\mathbb R.
$$

Indeed, Durrett notes that no sequence of deterministic centers can make \(S_n/n\) concentrate in probability at zero after centering. The stable Cauchy law has a fixed spread, and shifting its center cannot remove that spread.

It *is* true that \(S_n/n\xrightarrow{d}X_1\), simply because its distribution is constant in \(n\). But this is **convergence in distribution**, not a WLLN and not convergence in probability to a constant. Those distinctions matter.

## 6. Is a finite first moment necessary for a weak law?

Here is a subtle point I would have missed if I jumped directly from the Cauchy counterexample to the conventional WLLN.

The implication

$$
\mathbb E|X_1|<\infty
\quad\Longrightarrow\quad
x\mathbb P(|X_1|>x)\to0
$$

does **not** have a converse. To see what this means, construct a positive random variable \(Y\) with survival function

$$
\mathbb P(Y>x)=
\begin{cases}
1, & 0\leq x<e,\\[3pt]
\dfrac{e}{x\log x}, & x\geq e.
\end{cases}
$$

For \(x\geq e\),

$$
x\mathbb P(Y>x)=\frac{e}{\log x}\longrightarrow0,
$$

yet the tail-integral formula gives

$$
\mathbb E[Y]
=\int_0^\infty\mathbb P(Y>x)\,dx
\geq e\int_e^\infty\frac{dx}{x\log x}
=\infty.
$$

If we take i.i.d. copies of this *positive* \(Y\), Theorem 2.2.12 still applies: \(S_n/n-\mu_n\to0\) in probability. However, the truncated means \(\mu_n=\mathbb E[Y\mathbf 1_{\{Y\leq n\}}]\) increase to \(+\infty\), by monotone convergence. There is no finite limiting center.

Now make the example symmetric. Let \(R\) be an independent random sign with \(\mathbb P(R=1)=\mathbb P(R=-1)=1/2\), and set \(X=RY\). Then

$$
\mathbb E|X|=\infty,\qquad
x\mathbb P(|X|>x)\to0,
$$

but symmetry gives

$$
\mathbb E\left[X\mathbf 1_{\{|X|\leq n\}}\right]=0
\qquad\text{for every }n.
$$

For i.i.d. copies \(X_1,X_2,\ldots\), Theorem 2.2.12 therefore yields

$$
\boxed{\frac1n\sum_{k=1}^n X_k\xrightarrow{\mathbb P}0,
\qquad\text{even though }\mathbb E|X_1|=\infty.}
$$

This is a weak-law-type conclusion to a fixed constant **without** an ordinary finite expectation. It does not contradict Theorem 2.2.14, which states a sufficient condition, not a necessary one. Nor does it contradict the almost-sure result discussed in Durrett's Theorem 2.3.8: the strong law for i.i.d. variables has a sharper integrability requirement.

The distinction is that a weak law can tolerate occasional very large observations whose probability vanishes at each averaging scale. An almost-sure law must control the behavior along almost every entire sample path.

## 7. My reading of the whole storyline

I now read these theorems as answering three successive questions:

| Result | What gets added? | What can we conclude? |
|---|---|---|
| **2.2.11** | Independent triangular-array rows; negligible extreme-event probability; small scaled truncated second moments | \((S_n-a_n)/b_n\to0\) in probability |
| **2.2.12** | i.i.d. observations and \(x\mathbb P(|X_1|>x)\to0\), with \(b_n=n\) | \(S_n/n-\mu_n\to0\) in probability |
| **2.2.14** | Finite first absolute moment \(\mathbb E|X_1|<\infty\) | The center \(\mu_n\to\mu=\mathbb E[X_1]\), hence \(S_n/n\to\mu\) in probability |

There are two different issues that can otherwise get conflated:

- **Concentration:** Does the normalized sum stay close to an appropriate center? Truncation and the two conditions of Theorem 2.2.11 address this.
- **Convergence of the center:** Does that center itself approach a fixed finite number? The integrability argument in Theorem 2.2.14 addresses this.

The Cauchy distribution fails already at the first issue: the normalized sum retains its spread. A distribution with tail of order \(1/(x\log x)\) illustrates something different: the first issue can be solved even with an infinite first absolute moment, while the second issue depends on what the truncated centers do.

So, to me, truncation is not merely a technical trick for dodging an infinite variance. It reveals the *two logically separate mechanisms* behind the usual WLLN: **rare extremes no longer disrupt the average, and the appropriate truncated center settles at a finite limit.**

---

**Reference.** Rick Durrett, *Probability: Theory and Examples*, 5th ed., Section 2.2.3, Theorems 2.2.11, 2.2.12 and 2.2.14, Lemma 2.2.13, Example 2.2.15 (pp. 53–56); and Theorem 2.3.8 (pp. 60–61). [Book page](https://www.cambridge.org/core/books/probability/DD9A1907F810BB14CCFF022CDFC5677A).
