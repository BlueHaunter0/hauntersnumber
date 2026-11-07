# The Haunter's Number — $H(3)$

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Status: Active Specification](https://img.shields.io/badge/Status-Active-success.svg)]()
[![Googology Wiki](https://img.shields.io/badge/Googology-Wiki%20Spec-orange.svg)](https://googology.miraheze.org/)

**The Haunter's Number** (denoted as **$H(3)$**) is a formal fast-growing googological function and finite tree-embedding game governed by recursive shadow subtrees and ancestor-preserving topological minor embeddings. 

This repository houses the definitive mathematical specification, formal axioms, and reference validation scripts for $H(3)$.

---

## 📐 Formal Mathematical Specification

### 1. The Structure of a Haunter
A **Haunter** $T$ is defined inductively as a finite rooted tree where each node $v \in V(T)$ possesses two primary attributes:
* **A color** $c(v)$ mapping to the finite set $\{1, 2, 3\}$.
* **A shadow** $S(v)$, which is itself a strictly smaller Haunter containing fewer total nodes than the parent tree ($\vert{}V(S(v))\vert{} < \vert{}V(T)\vert{}$). 

The empty shadow is denoted as $\emptyset$. By definition, $\emptyset$ is haunted only by $\emptyset$, and no non-empty shadow can contain $\emptyset$ as a valid base component without recursive termination.

### 2. The Haunting Relation
A Haunter $A$ is said to *haunt* another Haunter $B$ (denoted $A \sqsupseteq B$) if and only if there exists an injective topological tree embedding $\phi: V(A) \to V(B)$ such that:
* **Color Preservation:** For every node $u \in V(A)$, $c(u) = c(\phi(u))$.
* **Structural Adjacency:** Parent-child edges are preserved under $\phi$.
* **Ancestor-Preserving Paths:** If node $u$ is an ancestor of node $v$ in $A$, then $\phi(u)$ remains an ancestor of $\phi(v)$ in $B$.

### 3. Sequence Generation and Termination ($H(3)$)
The growth function generates a sequence of Haunters $(T_1, T_2, T_3, \dots, T_n)$ subject to two strict rules:
1. **Size Constraint:** The $n$-th Haunter $T_n$ is constrained such that its total node count—including all recursive nesting layers, shadow trees, and sub-shadows—does not exceed $n$:
   $$\sum_{v \in V(T_n)} \left( 1 + \vert{}V(S(v))\vert{} \right) \leq n$$
2. **Termination Condition:** The sequence terminates immediately at step $N$ the moment **any** earlier Haunter $T_i$ (where $1 \le i < N$) successfully haunts $T_N$ ($T_i \sqsupseteq T_N$).

The value **$H(3)$** represents the maximum possible finite length $N$ that the sequence can achieve before termination is triggered.

---

## 🐍 Reference Implementation (Python)

```python
class HaunterNode:
    def __init__(self, color: int, shadow=None):
        if color not in {1, 2, 3}:
            raise ValueError("Color must be in {1, 2, 3}")
        self.color = color
        self.shadow = shadow  # Can be another HaunterNode tree or None (empty shadow)
        self.children = []    # List of child HaunterNodes

    def add_child(self, child_node):
        self.children.append(child_node)

    def total_size(self) -> int:
        """Computes the total node count including recursive shadow layers."""
        shadow_size = self.shadow.total_size() if self.shadow else 0
        children_size = sum(c.total_size() for c in self.children)
        return 1 + shadow_size + children_size
