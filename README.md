# The Haunter's Number H(3)
**Author:** Haunter (`BlueHaunter0`)  
**Created:** 2026  
**Status:** Original mathematical construction; finiteness and growth rate not yet established

## Abstract

The Haunter's Number, denoted \(H(3)\), is a proposed finite tree-embedding game based on recursively shadow-decorated rooted trees. Each vertex has one of three colors and carries a smaller recursive structure called its shadow.

The construction defines a family of bad sequences: sequences in which no earlier structure embeds into a later one. The size restriction on the \(n\)-th term is \(\|T_n\|\le n\).

This document specifies the construction and distinguishes its definition from the currently unproved claims about its finiteness and growth rate.

## 1. Mathematical preliminaries

A finite rooted tree is a finite connected acyclic graph with a distinguished vertex called its root.

For vertices \(u,v\) of a rooted tree, write:

- \(u\preceq_T v\) if \(u\) is an ancestor of \(v\), including the case \(u=v\).
- \(u\wedge_T v\) for their greatest common ancestor.

All trees in this specification are finite and rooted.

## 2. Definition of a Haunter

A **Haunter** \(T\) is a finite rooted tree equipped with two decorations at every vertex \(v\):

1. A color \(c_T(v)\in\{1,2,3\}\).
2. A shadow \(S_T(v)\), which is itself a Haunter.

The recursive construction is required to be well-founded: every shadow must have strictly smaller size than the Haunter containing it.

The empty Haunter is denoted by \(\emptyset\).

There are no vertices in \(\emptyset\), and its size is zero.

## 3. Recursive size

Define the size function \(\|\cdot\|\) recursively by

\[
\|\emptyset\|=0
\]

and

\[
\boxed{
\|T\|=
\sum_{v\in V(T)}
\left(1+\|S_T(v)\|\right).
}
\]

This counts every vertex and recursively counts all shadow structures attached to it.

The well-foundedness condition requires

\[
\|S_T(v)\|<\|T\|
\]

for every vertex \(v\in V(T)\).

### Example

Let \(T\) be a single vertex with color \(1\) and empty shadow.

Then

\[
\|T\|=1+\|\emptyset\|=1.
\]

If the root instead has a shadow consisting of a single vertex with empty shadow, then

\[
\|T\|=1+1=2.
\]

The shadow is counted recursively, not merely by its number of ordinary tree vertices.

## 4. The haunting relation

Let \(A\) and \(B\) be Haunters.

We say that **\(A\) haunts \(B\)**, written

\[
A\sqsupseteq B,
\]

if there exists an injective map

\[
\phi:V(A)\longrightarrow V(B)
\]

satisfying all of the following.

### 4.1 Root preservation

The root of \(A\) maps to the root of \(B\):

\[
\phi(r_A)=r_B.
\]

### 4.2 Ancestor and meet preservation

For every \(u,v\in V(A)\),

\[
\phi(u\wedge_A v)
=
\phi(u)\wedge_B\phi(v).
\]

This preserves the rooted branching structure and greatest common ancestors.

### 4.3 Color preservation

For every \(u\in V(A)\),

\[
c_A(u)=c_B(\phi(u)).
\]

### 4.4 Shadow preservation

For every \(u\in V(A)\),

\[
S_A(u)\sqsupseteq S_B(\phi(u)).
\]

This condition is recursive and terminates because shadows are strictly smaller than their containing Haunters.

### 4.5 Empty structure

The empty Haunter haunts every Haunter, vacuously.

No nonempty Haunter haunts the empty Haunter.

The notation \(\sqsupseteq\) is intentionally used for the haunting relation. It should not be interpreted as ordinary numerical inequality.

## 5. Bad sequences

A sequence

\[
T_1,T_2,\ldots,T_N
\]

is a **Haunter bad sequence** if:

1. Each \(T_n\) is a Haunter.
2. The size restriction holds:

\[
\|T_n\|\le n.
\]

3. No earlier Haunter haunts a later one:

\[
\forall\,1\le i<j\le N,\qquad
T_i\not\sqsupseteq T_j.
\]

The sequence terminates when an earlier Haunter first haunts a later Haunter.

## 6. Definition of H(3)

Define

\[
H(3)=
\sup\left\{
N\in\mathbb N:
\begin{array}{l}
\text{there exists a Haunter bad sequence}\\
T_1,\ldots,T_N
\end{array}
\right\}.
\]

Here the supremum is taken in

\[
\mathbb N\cup\{\infty\}.
\]

If the set of attainable lengths is bounded, its supremum is the maximum attainable length and \(H(3)\) is a finite natural number.

If the lengths are unbounded, the definition gives

\[
H(3)=\infty.
\]

Thus the finiteness of \(H(3)\) is a mathematical question rather than an assumption built into its definition.

## 7. Relation to established mathematics

The construction is inspired by bad-sequence problems and tree-embedding results in googology.

Relevant background includes:

- Kruskal's Tree Theorem, which establishes a well-quasi-ordering result for finite trees under appropriate tree embeddings.
- Nash-Williams's proof of the well-quasi-ordering of finite trees.
- Higman's lemma, concerning well-quasi-orderings of finite sequences over well-quasi-ordered sets.

These results motivate the construction but do not automatically establish the well-quasi-ordering of recursively shadow-decorated Haunters.

## 8. Finiteness status

**The finiteness of \(H(3)\) is not established in this specification.**

A proof would need to establish that the haunting relation is a well-quasi-order on the entire recursively defined class of Haunters.

The recursive shadow condition introduces additional structure beyond ordinary finite rooted trees. In particular, an argument using Kruskal's Tree Theorem must justify why the recursive shadow labels satisfy the hypotheses of the applicable tree-embedding theorem.

Until such a proof is completed, \(H(3)\) should not be claimed to be finite.

## 9. Growth-rate status

No established comparison with the TREE sequence, the fast-growing hierarchy, or other major googological functions is claimed here.

The construction is intended as a candidate for further investigation in combinatorial googology.

A growth-rate classification requires explicit mathematical upper or lower bounds.

## 10. Creator and source

The Haunter's Number was created by Haunter (`BlueHaunter0`) in 2026.

This README is the primary specification of the construction. It is self-published and has not been peer-reviewed.

The definition and any future changes should be versioned to preserve reproducibility.

## References

1. Kruskal, J. B. (1960). “Well-quasi-ordering, the tree theorem, and Vázsonyi's conjecture.” *Transactions of the American Mathematical Society*, 95(2), 210–225. https://doi.org/10.1090/S0002-9947-1960-0111704-6

2. Nash-Williams, C. St. J. A. (1963). “On well-quasi-ordering finite trees.” *Proceedings of the Cambridge Philosophical Society*, 59(4), 833–835. https://doi.org/10.1017/S0000000000003844

3. Higman, G. (1952). “Ordering by divisibility in abstract algebras.” *Proceedings of the London Mathematical Society*, 3(2), 326–336.

4. Haunter (`BlueHaunter0`). “The Haunter's Number H(3): Formal Specification.” GitHub repository, 2026. https://github.com/BlueHaunter0/hauntersnumber
