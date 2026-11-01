---
layout: stat5010
title: "Chapter 7: Conditioning, Sufficiency, and UMVUEs"
date: 2026-11-02
permalink: /stat5010-study/chapter-7-conditioning-sufficiency-umvue/
read_time: false
share: false
related: false
tags:
  - stat5010-study
excerpt: "Questions and intuitions about Rao–Blackwellization, sufficiency, and the Lehmann–Scheffé theorem."
---

*STAT5010 — Chapter 7, Methods of Point Estimation.*

## Why does conditioning on a sufficient statistic \(T\) lead to less variation?

Suppose that

$$
\hat{\phi}(X_{1:n})
=
E_{\theta}\left[\tilde{\phi}(X_{1:n})\mid T\right].
$$

Informally, it is taking an average across the slices (or stripes) corresponding to \(T=t\). Taking averages within each stripe intuitively leads to a constant within that stripe. So only the **variation across the groups** \(T=t\) contributes to the variation of \(E_\theta[\tilde{\phi}(X_{1:n})\mid T]\), rather than the variation **both across and within** the groups.

Typically,

$$
E_{\theta}\left[\tilde{\phi}(X_{1:n})\mid T\right]
=
g_{\theta}(T)
$$

may depend on \(\theta\), since we are taking an expectation and the expectation operator depends on \(\theta\).

But when \(T\) is a **sufficient statistic (SS)**, the function can be chosen to be free of \(\theta\): by the definition of sufficiency, the conditional distribution \([X_{1:n}\mid T=t]\) is free of \(\theta\). Moreover, \(\tilde{\phi}\) is just a \(\theta\)-independent transformation of \(X_{1:n}\). Hence we can write

$$
E_{\theta}\left[\tilde{\phi}(X_{1:n})\mid T\right]
=
g(T),
$$

where \(g\) is free of \(\theta\).

## What if we condition on a CSS, MSS, or SS?

Can we show a relationship between conditioning on a **complete sufficient statistic (CSS)**, a **minimal sufficient statistic (MSS)**, and an arbitrary **sufficient statistic (SS)**?

*Conjecture / question to check:*

$$
\begin{aligned}
\operatorname{Var}_{\theta}\left(
E_{\theta}[\tilde{\phi}\mid T_{\mathrm{CSS}}]
\right)
&\stackrel{?}{\leq}
\operatorname{Var}_{\theta}\left(
E_{\theta}[\tilde{\phi}\mid T_{\mathrm{MSS}}]
\right)\\
&\stackrel{?}{\leq}
\operatorname{Var}_{\theta}\left(
E_{\theta}[\tilde{\phi}\mid T_{\mathrm{SS}}]
\right).
\end{aligned}
$$

What relationships between the statistics (or their generated \(\sigma\)-fields) would be needed for such a comparison?

## A note on equation (7.5)

For equation (7.5), we do need \(T\) to be an SS **if** we want \(h_2\) to be free of \(\theta\). In general, conditional expectation is a function of \(T\), but that function may depend on the underlying distribution:

$$
E_{\theta}[h_1(X_{1:n})\mid T]
=
h_{2,\theta}(T).
$$

When \(T\) is sufficient, we can write

$$
E_{\theta}[h_1(X_{1:n})\mid T]
=
h_2(T),
$$

with \(h_2\) free of \(\theta\).

## Example 7.13, Question 3 — Find a UMVUE of \(\theta\)

We already know that \(\bar X_n\) is a CSS for \(\theta\). Also, because \(X_1,\ldots,X_n\) are iid with \(E_\theta[X_i]=\theta\),

$$
E_\theta[\bar X_n]=\theta.
$$

Thus \(\bar X_n\) is itself an unbiased function of the CSS. By the **Lehmann–Scheffé theorem**, \(\bar X_n\) is already the UMVUE of \(\theta\)!

There is no need to explicitly calculate \(E_\theta[X_1\mid\bar X_n]\) in this question.

## Extra question — Can randomizing a sufficient statistic help?

Show that a **randomized transformation** of a sufficient statistic cannot outperform the UMVUE **within the class of unbiased estimators with finite variance**.

What changes if we allow biased estimators, or compare mean squared error rather than variance?
