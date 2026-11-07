The Haunter's Number H(3)
Author: Haunter (`BlueHaunter0`)  
Created: 2026  
Status: Original mathematical construction; finiteness and growth rate not yet established
Abstract
The Haunter's Number, denoted $H(3)$, is a proposed finite tree-embedding game based on recursively shadow-decorated rooted trees. Each vertex has one of three colors and carries a smaller recursive structure called its shadow.
The construction defines a family of bad sequences: sequences in which no earlier structure embeds into a later one. The size restriction on the $n$-th term is $\lVert T_n\rVert\leq n$.
This document specifies the construction and distinguishes its definition from claims about its finiteness and growth rate, which require additional proof.
1. Mathematical preliminaries
A finite rooted tree is a finite connected acyclic graph with a distinguished vertex called its root. For vertices $u,v$ of a rooted tree $T$, write:
$u\preceq_T v$ if $u$ is an ancestor of $v$, including the case $u=v$.
$u\wedge_T v$ for their greatest common ancestor.
Trees are considered up to rooted, color- and shadow-preserving isomorphism.
2. Definition of a Haunter
A Haunter $T$ is a finite rooted tree equipped with two decorations at every vertex $v$:
A color $c_T(v)\in{1,2,3}$.
A shadow $S_T(v)$, which is itself a Haunter.
The recursive construction is well-founded: every shadow has strictly smaller size than the Haunter containing it. The empty Haunter is denoted by $\emptyset$.
There are no vertices in $\emptyset$, and its size is zero.
3. Recursive size
Define the size function recursively by
```math
\lVert\emptyset\rVert=0
```
and
```math
\boxed{\lVert T\rVert=\sum_{v\in V(T)}\left(1+\lVert S_T(v)\rVert\right).}
```
This counts every vertex and recursively counts all shadow structures attached to it.
Example
Let $T$ be a single vertex with color $1$ and empty shadow. Then $\lVert T\rVert=1$.
If the root instead has a shadow consisting of a single vertex with empty shadow, then $\lVert T\rVert=2$.
The shadow is counted recursively, not merely by the number of ordinary tree vertices in the outer tree.
4. The haunting relation
Let $A$ and $B$ be Haunters. We say that $A$ haunts $B$, written
```math
A\preceq_H B,
```
if there exists an injective map
```math
\phi:V(A)\longrightarrow V(B)
```
satisfying all of the following conditions.
4.1 Meet preservation
For every $u,v\in V(A)$,
```math
\phi(u\wedge_A v)=\phi(u)\wedge_B\phi(v).
```
This preserves the greatest common ancestor of every pair of vertices. In particular, it preserves the ancestor relation on the image.
4.2 Color preservation
For every $u\in V(A)$,
```math
c_A(u)=c_B(\phi(u)).
```
4.3 Shadow preservation
For every $u\in V(A)$,
```math
S_A(u)\preceq_H S_B(\phi(u)).
```
This condition is recursive and terminates because shadows are strictly smaller than their containing Haunters.
The empty Haunter haunts every Haunter, vacuously. No nonempty Haunter haunts the empty Haunter.
Terminology note: This specification uses meet-preserving embeddings. It does not require the image of the root of $A$ to be the root of $B$, and it does not require parent-child edges to map to single edges. These choices are part of the definition and should not be silently replaced by a different tree-embedding convention.
5. Bad sequences
A sequence
```math
T_1,T_2,\ldots,T_N
```
is a Haunter bad sequence if:
Each $T_n$ is a Haunter.
The size restriction holds:
```math
\lVert T_n\rVert\leq n.
```
No earlier Haunter haunts a later one:
```math
T_i\not\preceq_H T_j\qquad\text{for all }1\leq i<j\leq N.
```
A sequence ceases to be a bad sequence as soon as an earlier term haunts a later term.
6. Definition of H(3)
Define
```math
H(3)=\sup\left\{N\in\mathbb N:\text{there exists a Haunter bad sequence of length }N\right\}.
```
The supremum is taken in $\mathbb N\cup{\infty}$. If the attainable lengths are bounded, their supremum is their maximum and $H(3)$ is a finite natural number. If the lengths are unbounded, the definition gives $H(3)=\infty$.
Thus, finiteness is a property to be proved, not an assumption built into the definition.
7. Relation to established mathematics
The construction is motivated by bad-sequence problems and well-quasi-ordering results for finite trees. Relevant background includes:
Kruskal's Tree Theorem, which establishes a well-quasi-ordering result for finite trees under appropriate tree-embedding relations.
Nash-Williams's minimal-bad-sequence approach to well-quasi-ordering finite trees.
Higman's lemma, which establishes a well-quasi-ordering result for finite sequences over a well-quasi-ordered set.
These results motivate the construction but do not, by themselves, prove that recursively shadow-decorated Haunters are well-quasi-ordered under the haunting relation.
8. Finiteness status
The finiteness of $H(3)$ is not established in this specification.
A proof would need to establish that the haunting relation is a well-quasi-order on the entire recursively defined class of Haunters. An argument using Kruskal's Tree Theorem must justify that the recursive shadow labels satisfy the hypotheses of the applicable tree-embedding theorem.
Until such a proof is supplied, $H(3)$ should not be described as a proven finite natural number.
9. Growth-rate status
No established comparison with the TREE sequence, the fast-growing hierarchy, or other major googological functions is claimed here. A growth-rate classification requires explicit mathematical upper or lower bounds.
10. Creator and source
The Haunter's Number was created by Haunter (`BlueHaunter0`) in 2026. This README is the primary specification of the construction. It is self-published and has not been peer-reviewed. Future changes to the definition should be versioned so that readers can identify the exact specification being discussed.
References
Kruskal, J. B. (1960). “Well-quasi-ordering, the tree theorem, and Vázsonyi's conjecture.” Transactions of the American Mathematical Society, 95(2), 210–225. https://doi.org/10.2307/1993287.
Nash-Williams, C. St. J. A. (1963). “On well-quasi-ordering finite trees.” Proceedings of the Cambridge Philosophical Society, 59(4), 833–835. https://doi.org/10.1017/S0305004100003844.
Higman, G. (1952). “Ordering by divisibility in abstract algebras.” Proceedings of the London Mathematical Society, 3(2), 326–336.
Haunter (`BlueHaunter0`). “The Haunter's Number H(3): Formal Specification.” GitHub repository, 2026. https://github.com/BlueHaunter0/hauntersnumber.
