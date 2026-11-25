---
layout: durrett
title: "From Independent Sigma-Fields to Functions of Disjoint Collections"
date: 2026-11-26
permalink: /durrett-waffling/independence-of-disjoint-collections/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "Expanding Durrett's proofs of Theorems 2.1.9 and 2.1.10 using triangular arrays, pi-systems, and the independence of generated sigma-fields."
---

*My working notes, with mathematical corrections and LaTeX formatting by ChatGPT.*

I think pp. 40–41 of Durrett (5th edition) are written a bit too compactly, so I just want to expand some details.

I guess a "trick" is that $$\pi$$-systems are about intersections, which then relate to the definition of independence:

$$
\mathbb P(A\cap B)=\mathbb P(A)\mathbb P(B).
$$

This is why independence proofs rely a lot on $$\pi$$-systems: they seem to be collections of sets built naturally for discussing intersection properties. More precisely, the useful machinery is Theorem 2.1.7, which uses Dynkin's $$\pi$$-$$\lambda$$ theorem to extend independence of $$\pi$$-systems to independence of their generated sigma-fields. Of course, closure under intersections alone does not imply independence; we still need to check the probability factorisation.

Durrett's next goal is to prove that functions of disjoint collections of independent random variables are independent. First prove an analogous result for sigma-fields, as random variables are independent iff their smallest sigma-fields making them measurable are independent.

## Theorem 2.1.9

Work on a probability space $$(\Omega,\mathcal F,\mathbb P)$$. Suppose the sigma-fields

$$
\mathcal F_{ij}\subseteq\mathcal F,
\qquad 1\leq i\leq n,\quad 1\leq j\leq m(i),
$$

are mutually independent, where each $$m(i)$$ is a positive integer. Let

$$
\mathcal G_i:=\sigma\left(\bigcup_{j=1}^{m(i)}\mathcal F_{ij}\right).
$$

Then the sigma-fields $$\mathcal G_1,\ldots,\mathcal G_n$$ are independent.

One motivation is to think of this as **triangular arrays of sigma-fields**. So if we take the special case $$m(i)=i$$, the first three rows look like

$$
\begin{array}{ccc}
\mathcal F_{11} & &\\
\mathcal F_{21} & \mathcal F_{22} &\\
\mathcal F_{31} & \mathcal F_{32} & \mathcal F_{33}
\end{array}
$$

All the $$\mathcal F_{ij}$$ are mutually (not just pairwise) independent, and we want to show rowwise independence. If we associate a random variable with each entry, something like

$$
\mathcal F_{ij}=\sigma(X_{ij}),
$$

then the interpretation of row $$i$$,

$$
\mathcal G_i
=\sigma\left(\bigcup_{j=1}^{m(i)}\sigma(X_{ij})\right),
$$

is the smallest sigma-field making the entire row of random variables $$X_{i1},X_{i2},\ldots,X_{i,m(i)}$$ measurable.

### Proof

So now the proof is basically using $$\pi$$-systems, then showing that the generated sigma-fields are large enough to contain the desired sigma-fields. Define for each row $$i=1,\ldots,n$$ (still FINITE, not to infinity; can think later about how to extend this to infinite collections, e.g. in connection with Kolmogorov's zero-one law)

$$
\mathcal A_i:=
\left\{
\bigcap_{j=1}^{m(i)}A_{ij}:
A_{ij}\in\mathcal F_{ij}
\text{ for every }j
\right\}.
$$

We have the following properties.

**1. Each collection is a pi-system.** If $$C,D\in\mathcal A_i$$, then there exist sets $$A_{ij},B_{ij}\in\mathcal F_{ij}$$ such that

$$
C=\bigcap_{j=1}^{m(i)}A_{ij},
\qquad
D=\bigcap_{j=1}^{m(i)}B_{ij}.
$$

Hence

$$
C\cap D
=\bigcap_{j=1}^{m(i)}(A_{ij}\cap B_{ij})
\in\mathcal A_i,
$$

since each $$\mathcal F_{ij}$$ is a sigma-field, so it is closed under intersections.

**2. The whole space belongs to each collection.**

$$
\Omega\in\mathcal A_i,\qquad i=1,\ldots,n.
$$

We need this so that later we do not need to consider sub-index collections separately (Lemma 2.1.5). I feel like since we are considering sigma-fields $$\mathcal F_{ij}$$, this is automatic? Indeed it is: just choose $$A_{ij}=\Omega$$ for every $$j$$. Durrett is making explicit why the full-index factorisation will suffice for the collections $$\mathcal A_i$$, which are not assumed to be sigma-fields.

**3. The union of the row's sigma-fields is contained in the pi-system.**

$$
\bigcup_{j=1}^{m(i)}\mathcal F_{ij}
\subseteq\mathcal A_i.
$$

Simply fix $$i$$ and take any

$$
B_i\in\bigcup_{j=1}^{m(i)}\mathcal F_{ij}.
$$

Then there exists some index $$\hat j$$ with $$B_i\in\mathcal F_{i\hat j}$$. Simply choose the sets

$$
A_{i\hat j}=B_i,\qquad
A_{ij}=\Omega\quad(j\neq\hat j).
$$

This gives

$$
B_i=\bigcap_{j=1}^{m(i)}A_{ij}\in\mathcal A_i.
$$

### Independence of the pi-systems

Now we must show the collections $$\mathcal A_1,\ldots,\mathcal A_n$$ are independent (being pi-systems does not automatically give this).

For each $$i$$, take an arbitrary $$C_i\in\mathcal A_i$$ and write

$$
C_i=\bigcap_{j=1}^{m(i)} A_{ij},
\qquad A_{ij}\in\mathcal F_{ij}.
$$

Then

$$
\begin{aligned}
\mathbb P\left(\bigcap_{i=1}^{n} C_i\right)
&=\mathbb P\left(\bigcap_{i=1}^{n}
                    \bigcap_{j=1}^{m(i)} A_{ij}\right)\\
&=\prod_{i=1}^{n}\prod_{j=1}^{m(i)}\mathbb P(A_{ij})\\
&=\prod_{i=1}^{n}
   \mathbb P\left(\bigcap_{j=1}^{m(i)}A_{ij}\right)\\
&=\prod_{i=1}^{n}\mathbb P(C_i).
\end{aligned}
$$

The second equality holds since all the sigma-fields $$\mathcal F_{ij}$$ across $$i,j$$ are mutually independent. The third holds because each row is a subcollection of this independent family.

Since $$\Omega\in\mathcal A_i$$ for every $$i$$, this full-index factorisation implies independence of the collections by Lemma 2.1.5.

Now Theorem 2.1.7 extends independence from the pi-systems $$\mathcal A_1,\ldots,\mathcal A_n$$ to the sigma-fields

$$
\sigma(\mathcal A_1),\ldots,\sigma(\mathcal A_n).
$$

### Do we really need equality of the generated sigma-fields?

I think we often try to prove equality of the generated sigma-fields:

$$
\sigma(\mathcal A_i)
=\sigma\left(\bigcup_{j=1}^{m(i)}\mathcal F_{ij}\right).
$$

But maybe the equality is not necessary here. We only need the inclusion proved above,

$$
\bigcup_{j=1}^{m(i)}\mathcal F_{ij}\subseteq\mathcal A_i,
$$

because it implies

$$
\mathcal G_i
=\sigma\left(\bigcup_{j=1}^{m(i)}\mathcal F_{ij}\right)
\subseteq\sigma(\mathcal A_i).
$$

So independence has already been extended from the pi-systems to the generated sigma-fields, and can then be restricted to $$\mathcal G_1,\ldots,\mathcal G_n$$. Indeed, if we choose any event from each $$\mathcal G_i$$, we have also chosen an event from the corresponding $$\sigma(\mathcal A_i)$$. Hurray :)

The equality that Durrett writes is also true. The other inclusion is immediate: each set in $$\mathcal A_i$$ is a finite intersection of sets in $$\mathcal G_i$$, hence belongs to $$\mathcal G_i$$. Because the latter is a sigma-field,

$$
\mathcal A_i\subseteq\mathcal G_i
\implies \sigma(\mathcal A_i)\subseteq\mathcal G_i.
$$

Thus we actually have

$$
\boxed{
\sigma(\mathcal A_i)
=\mathcal G_i
=\sigma\left(\bigcup_{j=1}^{m(i)}\mathcal F_{ij}\right).
}
$$

Small correction to my original notes: it is the **generated** sigma-field $$\sigma(\mathcal A_i)$$ that equals $$\mathcal G_i$$, not necessarily the pi-system $$\mathcal A_i$$ itself. And if proving only one inclusion, the one we need is $$\mathcal G_i\subseteq\sigma(\mathcal A_i)$$, not the reverse.

## Theorem 2.1.10

If for $$1\leq i\leq n$$ and $$1\leq j\leq m(i)$$ the real-valued random variables $$X_{ij}$$ are mutually independent, and

$$
f_i:\mathbb R^{m(i)}\longrightarrow\mathbb R
$$

are Borel measurable, then

$$
f_1(X_{11},\ldots,X_{1,m(1)}),
\ldots,
f_n(X_{n1},\ldots,X_{n,m(n)})
$$

are independent.

We specialise by setting

$$
\mathcal F_{ij}:=\sigma(X_{ij}),
\qquad
\mathcal G_i=\sigma\left(\bigcup_j\mathcal F_{ij}\right).
$$

So the function $$f_i$$ only takes random variables from row $$i$$ as inputs.

By the definitions of mutual independence of random variables and sigma-fields (the generalisation of Theorem 2.1.1), the $$X_{ij}$$ are independent iff the $$\mathcal F_{ij}$$ are independent across $$i,j$$. Then Theorem 2.1.9 gives independence of the row sigma-fields $$\mathcal G_i$$.

We know that $$f_i$$ is measurable from the Borel sigma-field of $$\mathbb R^{m(i)}$$ to that of $$\mathbb R$$. The row vector

$$
\mathbf X_i:=(X_{i1},\ldots,X_{i,m(i)})
$$

is measurable with respect to

$$
\mathcal G_i
=\sigma(X_{i1},\ldots,X_{i,m(i)}),
$$

by coordinatewise measurability (Theorem 1.3.5 and the fact that the Borel sigma-field on a finite-dimensional Euclidean space is the product Borel sigma-field). Thus the whole chain function

$$
g_i:=f_i\circ\mathbf X_i:\Omega\longrightarrow\mathbb R
$$

is measurable from $$\mathcal G_i$$ to $$\mathcal B(\mathbb R)$$.

In the textbook this is written using the shorthand

$$
f_i(X_{i1},\ldots,X_{i,m(i)})\in\mathcal G_i.
$$

This is not literal set membership: a random variable is a function, whereas the elements of a sigma-field are events. Durrett uses this notation to say that the random variable is measurable with respect to the sigma-field. In terms of generated sigma-fields, we can write

$$
\sigma(g_i)\subseteq\mathcal G_i.
$$

Just treat $$g_i$$ as a random variable from $$\Omega$$ to $$\mathbb R$$. That means

$$
g_i^{-1}(B_i)\in\mathcal G_i
\qquad\text{for every }B_i\in\mathcal B(\mathbb R).
$$

Hence independence of the row sigma-fields across $$i$$ implies

$$
\begin{aligned}
\mathbb P\left(\bigcap_{i=1}^{n}\{g_i\in B_i\}\right)
&=\mathbb P\left(\bigcap_{i=1}^{n}g_i^{-1}(B_i)\right)\\
&=\prod_{i=1}^{n}\mathbb P(g_i^{-1}(B_i))\\
&=\prod_{i=1}^{n}\mathbb P(g_i\in B_i),
\end{aligned}
$$

for all choices of Borel sets $$B_1,\ldots,B_n$$. This is exactly independence of $$g_1,\ldots,g_n$$.

**Reference note.** In the 5th edition, the proof of Theorem 2.1.10 refers to Exercise 2.1.1, but that exercise concerns factorisation of densities. The result being used here follows directly from the definitions on p. 38, generalising Theorem 2.1.1. This appears to be a cross-reference error.

## Why care?

This is precisely the machinery we used for the maximal-inequality proofs. If the $$X_i$$ are independent, the partial sum $$S_n-S_k$$ only depends on future increments, whereas the indicator of a first-crossing event at time $$k$$ only depends on past increments. Theorem 2.1.10 gives independence of these two functions of disjoint collections.

*Reference: Durrett, Probability: Theory and Examples (5th ed.), pp. 37–41, especially Lemma 2.1.5 and Theorems 2.1.7, 2.1.9 and 2.1.10.*
