---
layout: durrett
title: "From Generated Sigma-Fields to Independence: An Active Recall Note"
date: 2026-11-23
permalink: /durrett-waffling/generated-sigma-fields-to-independence/
read_time: false
share: false
related: false
tags:
  - durrett-waffling
excerpt: "Active recall of Theorem 1.3.1 and Exercise 1.3.1, connecting inverse images, generated sigma-fields, pi-systems, and independence in Theorem 2.1.8."
---

## On generated stuff: \(\pi\)-systems to independence

so first recall suppose

$$
X:(\Omega,\mathcal F)\to(S,\mathcal S).
$$

suppose $\mathcal A$ generates $\mathcal S$ i.e. $\sigma(\mathcal A)=\mathcal S$.

im trying active recall **Theorem 1.3.1** so

If $X$ is $\mathcal F$-$\mathcal A$ mble, then $X$ is $\mathcal F$-$\sigma(\mathcal A)$ mble

so the idea is that we do not need to check so many members of $\mathcal S$, we only need to check for members/sets of $\mathcal A$.

proof is as follows. the idea is to first collect stuff (members/sets) from $\sigma(\mathcal A)$ that indeed satisfies the deriable property:

$$
\mathcal G:=\{B\in \sigma(\mathcal A): X^{-1}(B)\in \mathcal F \}.
$$

then given $X^{-1}(A)\in \mathcal F$ for all $A\in \mathcal A$,

$\mathcal A\subseteq \mathcal G$, and hence

$$
\sigma(\mathcal A)\subseteq \sigma(\mathcal G).
$$

then suppose we can show $\mathcal G$ is a $\sigma$-algebra, then given $\mathcal G\subseteq \sigma(\mathcal A)$, altogether imply

$$
\sigma(\mathcal A)\subseteq \sigma(\mathcal G) =\mathcal G\subseteq \sigma(\mathcal A)
$$

which implies $\mathcal G = \sigma(\mathcal A)$.

## Exercise 1.3.1: Inverse images and generation

now we go to exercise 1.3.1 first introduce some notations:

suppose again

$$
X: (\Omega, \mathcal F)\to (S, \mathcal S).
$$

- $X^{-1}(\mathcal A)=\{X^{-1}(A): A\in \mathcal A\}$ for any collection/family of sets $\mathcal A$
- $\sigma(X)=\{X^{-1}(B): B\in \mathcal S\}$, usually $\mathcal S=\mathcal B(\mathbb R)$. then
- $\sigma(X)\equiv X^{-1}(\mathcal S)$

in previous proof, we cared about output space generateion $\mathcal A$ generates $\mathcal S$ which is sigma field in the OUTPUT space, now to bring similar idea to INPUT space, we hope to show that, (say $\mathcal S=\sigma(\mathcal A)$, and notice $X^{-1}(\mathcal A)\subseteq \mathcal F$ where $\mathcal A\subseteq \mathcal S$ can be any family of sets in OUTPUT space)

$$
\sigma(X^{-1}(\mathcal A))=X^{-1}(\sigma(\mathcal A)).
$$

i.e. $\mathcal A$ generates $\mathcal S$ implies $X^{-1}(\mathcal A)$ generates $X^{-1}(\mathcal S)$, so applying this (collection of)set inverse $X^{-1}(.)$ operation preserves generation process in some vague sense

**Remark**. this connects to independence in chapter 2 when proving that checking $X_i\leq x_i$ is enough for showing independence of random variables. the idea is that, we just now found a way in **Theorem 1.3.1** to check MEASURABILITY of smaller colelction of sets, here for checking INDEPENDENCE, we also only need to check for the generat*OR*s like $X_i\leq x_i$ no need to check for generated Borel sigma algbera

proof is as follows.

easy direction first, conveniently

$$
\mathcal A\subseteq \sigma(\mathcal A)
\implies X^{-1}(\mathcal A)\subseteq X^{-1}(\sigma(\mathcal A))
\implies \sigma(X^{-1}(\mathcal A))\subseteq
\sigma(X^{-1}(\sigma(\mathcal A)))
$$

where $\sigma(X^{-1}(\sigma(\mathcal A)))=X^{-1}(\sigma(\mathcal A))=\sigma(X)$ already a sigma-field (under $\mathcal S=\sigma(\mathcal A)$).

now the hard direction is to show

$$
X^{-1}(\sigma(\mathcal A))\subseteq \sigma(X^{-1}(\mathcal A)).
$$

i have been trying this exercise for like 3-4 times, i developed my own proof/thinking during 2nd time when i found the solution very confusing or counterintuitive, and i have never tried to active recall or learn the so called official solution lol, lemme try it again this time

### My own solution first

we recycle theorem 1.3.1 so using above notations, we translate

If $X$ is $\mathcal F$-$\mathcal A$ mble, then $X$ is $\mathcal F$-$\sigma(\mathcal A)$ mble, into something mroe set like:

$$
X^{-1}(\mathcal A)\subseteq \mathcal F
\implies
X^{-1}(\sigma(\mathcal A))\subseteq \mathcal F.
$$

and i immediately already noticed that the term $X^{-1}(\mathcal A)$ appears on LHS of our desired to show statement and on RHS of above given result from Theorem 1.3.1. Now just pick $\mathcal F=\sigma(X^{-1}(\mathcal A))$, and indeed $X^{-1}(\mathcal A)\subseteq \sigma(X^{-1}(\mathcal A))=\mathcal F$ so we indeed use the theorem 1.3.1. set formulated result. then we are done

i think my proof above is more elegant maybe as it recycles the OUTPUT space result directly back to INPUT space, now the solution notes i have had to construct another family of sets. for learning purposes i try to active recall now.

### Active recall of the auxiliary-\(\mathcal G\) solution

again the purpose is to show

$$
X^{-1}(\sigma(\mathcal A))\subseteq \sigma(X^{-1}(\mathcal A)).
$$

so let us translate: Need to show

$$
\forall D\in X^{-1}(\sigma(\mathcal A)),
\quad D\in \sigma(X^{-1}(\mathcal A))
$$

that is if $D=X^{-1}(S)$ for some $S\in \sigma(\mathcal A)$, then $D=X^{-1}(S)\in \sigma(X^{-1}(\mathcal A))$

or alternatively,

$$
\forall B\in \sigma(\mathcal A),
\quad X^{-1}(B)\in \sigma(X^{-1}(\mathcal A)).
$$

so the idea is to gather stuff in INPUT space (as last time gather stuff in OUTPUT space sth like $B:X^{-1}(B)\in \mathcal F$) with desirable properties so

$$
\mathcal G :=\{X^{-1}(S): \text{???}\}
$$

chatgpt: The confusion seems to be about where the auxiliary collection $\mathcal G$ should live. Recall that measurability connects two spaces:

$$
X:(\Omega,\mathcal F)\longrightarrow(S,\mathcal S).
$$

We test sets in the output space $S$, but the condition we check concerns their inverse images in the input space $\Omega$. So your earlier construction for Theorem 1.3.1 is still relevant. You do not necessarily need to construct a collection of subsets of $\Omega$.

Thus, hinted by gpt, recall our earlier definiton

$$
\mathcal G
=\{B\in\sigma(\mathcal A):X^{-1}(B)\in\mathcal F\},
$$

so now, compare to our target: $\forall B\in \sigma(\mathcal A), X^{-1}(B)\in \sigma(X^{-1}(\mathcal A))$, thus again similar to my ABOVE prove, simply choose $\mathcal F\equiv \sigma(X^{-1}(\mathcal A))$!

so

$$
\mathcal G
=\{B\in\sigma(\mathcal A):X^{-1}(B)\in \sigma(X^{-1}(\mathcal A))\},
$$

then we can recylce all arguments, since $\sigma(X^{-1}(\mathcal A))$ is indeed a sigma-field by $\sigma(.)$ notation and, once $\mathcal G$ is checked to be a sigma-field and $\mathcal A\subseteq\mathcal G$, we have

$$
\sigma(\mathcal A)\subseteq \sigma(\mathcal G)=\mathcal G.
$$

so indeed $\forall B\in \sigma(\mathcal A), X^{-1}(B)\in\mathcal F\equiv \sigma(X^{-1}(\mathcal A))$.

WE still need to check $\mathcal G$ is a $\sigma$-field. and $\mathcal A\subseteq\mathcal G$. but these are trivial

### EXTENSION: Direct images

To establish

$$
\sigma(X(\mathcal A))=X(\sigma(\mathcal A)),
$$

a sufficient assumption is that $X:\Omega \to \mathbb R$ is bijective so then for any sequence $(B_i)_{i\ge1}$ of subsets of $\Omega$,

$$
X\left(\bigcup_{i=1}^{\infty}B_i\right)
=
\bigcup_{i=1}^{\infty}X(B_i).
$$

In fact, this identity holds for every function, without bijectivity. For complements, proposed identity is

$$
X(\Omega\setminus B)
=
\mathbb R\setminus X(B),
\qquad B\subseteq\Omega.
$$

This is also correct when $X$ is bijective. Notice that complements are taken relative to their respective ambient spaces.

## Finally, independence: Theorem 2.1.8 (Durrett, 5th ed., p. 40)

ok now finally we can walk to independence

it says that we only need to check $\leq x_i$ for random variables independence:

$$
P\left(
X_1^{-1}((-\infty,x_1])\cap\cdots\cap
X_n^{-1}((-\infty,x_n])
\right)
=
\prod_{i=1}^n P\left(X_i^{-1}((-\infty,x_i])\right).
$$

fist notice that we can let $x_i=+\infty$ so that $\{X_i\le+\infty\}=\Omega$ (here $X_i$ is real-valued).

so it is easy to show that each

$$
\mathcal A_i
=
\{X_i^{-1}((-\infty,x_i]):x_i\in(-\infty,+\infty]\}
=
X_i^{-1}(\mathcal S_i),
$$

where

$$
\mathcal S_i
:=
\{(-\infty,x_i]:x_i\in(-\infty,+\infty]\}
$$

(with the threshold $x_i=+\infty$ interpreted as giving the entire real line) is a $\pi$-system, and above given condition means $\mathcal A_1,\ldots,\mathcal A_n$ are independent collection of sets. Thus, by Theorem 2.1.7 (using $\pi$-$\lambda$ theorem as bridge) we have

$$
\sigma(\mathcal A_1),\ldots,\sigma(\mathcal A_n)
$$

are independent ($\sigma$-fields), then the only thing left to show is

$$
\sigma(\mathcal A_i)=X_i^{-1}(\mathcal B(\mathbb R))=\sigma(X_i).
$$

assuming $X_i:(\Omega,\mathcal F)\to(\mathbb R,\mathcal B(\mathbb R))$

Recall $\mathcal A_i=X_i^{-1}(\mathcal S_i)$, that means from exercise 1.3.1 for second equlaity below

$$
\sigma(\mathcal A_i)
=
\sigma(X_i^{-1}(\mathcal S_i))
=
X_i^{-1}(\sigma(\mathcal S_i))
=
X_i^{-1}(\mathcal B(\mathbb R)).
$$

although i think we can be as smart as Fang Xiao and write directly intuitively get

$$
\sigma(X_i)
:=
\sigma\left(\{X_i^{-1}((-\infty,x_i]):x_i\in(-\infty,+\infty]\}\right)
=
\sigma\left(\{X_i\leq x_i:x_i\in(-\infty,+\infty]\}\right).
$$

and $\{X_i\leq x_i:x_i\in(-\infty,+\infty]\}$ is a $\pi$-system.
