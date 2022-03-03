---
title: (DRAFT) A multitool
date: 2022-03-02
---

{% include scripts.html %}

Perhaps a common tool for many, *diagonalization* is one those seemingly simple techniques that has
blown my mind over and over. Like most people, my first encounter with it was with Cantor's proof
that $$\|\mathbb{N}\| < \|\mathbb{R}\|$$. I must admit, the beauty of the technique was lost onto
me the first time I saw, it seemed too simple to matter, just like the Pigeon Hole Principle or the
triangle inequalities (again, *seemed*). After spending some time studying complexity theory and
how diagonalization has been used to prove some **very** interesting theorems, I now can admit how
wrong I was. The intention of this post is for me to pay tribute to the wonderful technique with
which Georg Cantor has gifted us.

For those not familiar with the technique, allow me to demonstrate the core idea by first outlining
how the technique operates and then providing an example. Let's say that you want to prove that a
certain object $$x$$ does not exist in a particular
[countably infinite](https://en.wikipedia.org/wiki/Countable_set)
set $$L$$. Since $$L$$ is countably infinite, we can assign each of its elements with a unique
positive natural index $$i$$ and use $$L_i$$ to denote the element of $$L$$ with index $$i$$.
In its simplest form, proceeds by constructing $$x$$ in stages, ensuring at each stage $$i>0$$,
$$x \neq L_i$$, without affecting the outcome of prior stages.

**Example:** Suppose we want to show that there is a language that is not
[recursively enumerable](https://en.wikipedia.org/wiki/Recursively_enumerable_language) (RE).
Since the class of RE sets ($$\Sigma_1^0$$) is countably infinite and they are each accepted by some
Turing machine, we can assume that we have a list of those machines as $$M_1, M_2, M_3, \ldots$$.
We can also assume that each string in over our alphabet is ordered as $$s_0, s_1, s_2, \ldots$$.
Now let us devise our stages.

*Stage 0*: Initialize $$A_0 = \emptyset$$.

*Stage* $$i>0$$: If $$M_i$$ rejects $$s_i$$, set $$A_i = A_{i-1} \cup \{s_i\}$$, otherwise set
$$A_i = A_{i-1}$$. (This clearly does not affect what could have happened at stages $$ < i$$.)

If you set $$A = \bigcup_{i \in \mathbb{N}} A_i$$ and you end up with
 $$A = \{ i \mid M_i \text{ does not accept the string } s_i\}$$.
Is $$A \in \Sigma_1^0$$? Well, let's assume it is and that there is a machine that accepts
$$A$$, i.e., $$A = L(M_j)$$. Without loss of generality, let that machine be $$M_j$$ in the list of
machines. Then, $$s_j \in A \iff s_j \not\in L(M_j)$$. This is clearly contradicts the fact that
$$$A = L(M_j)$$, which means that $$A \not\in \Sigma_1^0$$.


$$\begin{tabular}{|c|c|c|c|c|c|c|c|}
\hline
 & s_0 & s_1 & s_2 & s_3 & s_4 & s_5 & s_6 & s_7\\
M_1 & \times & & & & & & \\
\hline
M_2 & & \times & & & & & \\
\hline
M_3 & & & \times & & & & \\
\hline
M_4 & & & & \times & & & \\
\hline
M_5 & & & & & \times & & \\
\hline
M_6 & & & & & & \times & \\
\hline
M_7 & & & & & & & \times
\hline
\end{tabular}$$


Pretty neat, huh! The natural question that follows is to ask how far can we push this technique?

Among computability and complexity theory, there are many theorems that rely on diagonalization.
Just a few are:
1. The Halting Problem is undecidable.
2. Every RE set has an infinite recursive subset (who?).
3. There is an infinite set that has no RE subset (and no coRE subset) (who?).
4. The [Time Hierarchy Theorem](https://en.wikipedia.org/wiki/Time_hierarchy_theorem)
(Hartmanis and Stearns).
5. The [Space Hierarchy Theorem](https://en.wikipedia.org/wiki/Space_hierarchy_theorem)
(Hartmanis and Stearns).
6. If $${\rm P \neq \rm NP}$$, then there is an $${\rm NP}$$ set that is not in
$${\rm P}$$ and is not $${\rm NP}$$-complete (Ladner's Theorem).
7. There is an oracle $$B$$ such that $${\rm P^B \neq NP^B}$$ (Baker, Gill, and Solovay).
8. There is an oracle $$A$$ such that $${\rm P^A = UP^A \neq NP^A}$$ (Hartmanis and Hemachandra)
(originally proven by Rackoff using a different technique).

Some of the results above use what's called a *delayed diagonalization*, where the conflict
does not occur on the main diagonal. Can you figure out which? (These are not trivial either, so
  don't worry if you don't.)

So how much more flexible does this get? Injury methods allow you to affect previously satisfied
stages, either finitely often, or infinitely often. These types of arguments are even more
complicated to handle, but can prove additional results. Here are some examples from computability
and complexity theory:
**Need to list some
