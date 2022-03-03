---
title: (DRAFT) A multitool
---

{% include scripts.html %}

Perhaps a common tool for many, *diagonalization* is one those seemingly simple techniques that has blown my mind
over and over. Like most people, my first encounter with it was with Cantor's proof that $$\|\mathbb{N}\| < \|\mathbb{R}\|$$.
I must admit, the beauty of the technique was lost onto me the first time I saw, it seemed too simple to matter, just like
the Pigeon Hole Principle or the triangle inequalities (again, *seemed*). After spending some time studying complexity 
theory and how diagonalization has been used to prove some **very** interesting theorems, I now can admit how wrong I was.
The intention of this post is for me to pay tribute to the wonderful technique with which Georg Cantor has gifted us.

For those not familiar with the technique, allow me to demonstrate the core idea by first outlining how the technique operates and then providing an example.
Let's say that you want to prove that a certain object $$x$$ does not exist in a particular [countably infinite](https://en.wikipedia.org/wiki/Countable_set) 
set $$L$$. Since $$L$$ is countably infinite, we can assign each of its elements with a unique positive natural index $$i$$
and use $$L_i$$ to denote the element of $$L$$ with index $$i$$.
In its simplest form, proceeds by constructing $$x$$ in stages, ensuring at each stage $$i>0$$, $$x \neq L_i$$.

**Example:** Suppose we want to show that there is a language that is not 
[recursively enumerable](https://en.wikipedia.org/wiki/Recursively_enumerable_language).
Since the set of recursively enumerable languages is countably infinite and they are each accepted by some 
Turing machine, we can assume that we have a list of those machines as $$M_1, M_2, M_3, \ldots$$.
We can also assume that each string in over our alphabet is ordered as $$s_0, s_1, s_2, \ldots$$.
Now let us devise our stages.

*Stage 0*: Initialize $$A_0 = \emptyset$$.

*Stage* $$i>0$$: If $$M_i$$ rejects $$s_i$$, set $$A_i = A_{i-1} \cup \{s_i\}$$, otherwise set $$A_i = A_{i-1}$$.

If you set $$A = \bigcup_{i \in \mathbb{N}} A_i$$ and you end up with
 $$A = \{ i \mid M_i \text{ does not accept the string} s_i\}$$.
Can this language be recursively enumerable? Well, let's assume that there is a machine that accepts $$A$$. Without loss
of generality, let that machine be $$M_j$$ in the list of machines. Then, $$s_j \in A \iff s_j \not\in L(M_j)$$. This is
clearly a contradiction, which means that $$A$$ is not recursively enumerable!

Pretty neat, huh. The natural question that follows is to ask how far can we push this technique?


introduce diagonalization

historical

early application in computability

uses in complexity

where to go after with similar techniques
