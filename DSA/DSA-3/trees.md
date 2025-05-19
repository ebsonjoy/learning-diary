# 🌳 DSA - Tree

**Date:** 2025-05-19

---

## 🔍 What is a Tree?

- A **tree** is a **non-linear**, **hierarchical** data structure.
- It consists of **nodes** connected by **edges**.
- The top node is called the **root**.
- Each node stores **data** and links to **child nodes**.
- Unlike graphs, trees do **not** contain cycles.

---

## 🛠 Where is Tree Used?

- Hierarchical data like **file systems**, **organization structures**
- **Databases** (e.g., B-Trees, Tries in indexing)
- **Routing algorithms**, **AI (Decision Trees)**
- **Compilers** (Abstract Syntax Tree)
- HTML DOM is a tree structure
- Used in **compression algorithms**, **priority queues**, etc.

---


## 🌲 Types of Trees in Data Structures

| Tree Type                 | Description |
|----------------------------|-------------|
| **Binary Tree**            | Each node has **at most two children** (left and right). |
| **Binary Search Tree (BST)** | A binary tree where **left < root < right**. Provides efficient search. |
| **AVL Tree**               | A **self-balancing** BST. Balance factor of each node is -1, 0, or 1. |
| **Red-Black Tree**         | Self-balancing BST where each node is either red or black. Guarantees O(log n) operations. |
| **Splay Tree**             | A self-adjusting BST where recently accessed elements are moved to the root. |
| **Treap**                  | A combination of **Binary Search Tree** and **Heap**. Maintains both BST and heap properties. |
| **Segment Tree**           | Used for **range queries** (like sum, min, max) and updates in logarithmic time. |
| **Fenwick Tree (Binary Indexed Tree)** | Efficient for range sum queries and point updates. Simpler and faster for some cases than segment trees. |
| **Heap (Min/Max)**         | A **complete binary tree** where parent node is either greater (max-heap) or smaller (min-heap) than its children. |
| **Trie (Prefix Tree)**     | A tree used for **efficient retrieval of strings**, especially for autocomplete and dictionary operations. |
| **N-ary Tree**             | A tree where each node can have **N children** (not just 2). Used in file systems and hierarchies. |
| **B-Tree**                 | A self-balancing search tree for **sorted data**, allows search, sequential access, insertions, and deletions in logarithmic time. Common in databases. |
| **B+ Tree**                | Extension of B-Tree. All values are stored at leaf nodes and linked, supporting **faster range queries**. |
| **Ternary Search Tree**    | Hybrid of BST and Trie. Each node has 3 children — less, equal, and greater — used in string searching. |
| **Expression Tree**        | Used in compilers to represent expressions (e.g., `a + b * c`). Leaves are operands; internal nodes are operators. |
| **Decision Tree**          | Used in **AI and machine learning** for decision-making. Nodes represent questions/conditions, and edges represent answers. |
| **Suffix Tree**            | A compressed trie of all suffixes of a given string. Used in string processing (e.g., substring search). |
| **KD Tree (K-Dimensional Tree)** | Used to organize points in a k-dimensional space. Often used in **nearest neighbor search**. |
| **Quad Tree**              | A tree in which each internal node has exactly four children. Used in **2D spatial partitioning** (e.g., image processing, maps). |
| **Octree**                 | Like a quad tree but for **3D space** — each internal node has eight children. Used in 3D graphics. |
| **R-Tree**                 | A tree used for **spatial access methods**, like querying 2D rectangles or 3D boxes in GIS and databases. |
| **General Tree**           | No restriction on number of children per node. Useful to represent **any hierarchy**. |

---



### 📗 Special Binary Trees

| Tree Type             | Description |
|------------------------|-------------|
| **Full Binary Tree**   | Every node has **0 or 2 children** (no node with only one child) |
| **Complete Binary Tree** | All levels are completely filled **except possibly the last**, and all nodes are as **left as possible** |
| **Perfect Binary Tree** | All internal nodes have 2 children and **all leaves are at same level** |
| **Balanced Binary Tree** | Height of left and right subtree of any node differs by at most 1 |
| **Degenerate Tree** (Skewed Tree) | Each parent has only one child — acts like a **linked list** (left-skewed or right-skewed) |

---

## 🖼 Visual Example

     A
   /   \
  B     C
 / \   / \
D   E F   G



---

## ✅ Properties of Tree

- **Root**: Topmost node
- **Leaf**: Node with no children
- **Internal Node**: A node that has at least one child
- **Height**: Longest path from root to a leaf
- **Depth**: Distance from root to that node
- **Level**: Depth + 1
- **Degree**: Number of children a node has

---

## 👍 Advantages

- Reflects **hierarchical data** naturally
- Efficient **search, insert, delete** (especially in BST, AVL)
- Enables **fast lookups and range queries**
- Widely used in real-time systems and AI

---

## 👎 Disadvantages

- More **complex** to implement than arrays or linked lists
- Can become **unbalanced**, degrading performance
- Traversal may require **recursion or stack**

---

## 📚 Tree Traversal Methods

| Method         | Order |
|----------------|-------|
| **In-order**   | Left → Root → Right |
| **Pre-order**  | Root → Left → Right |
| **Post-order** | Left → Right → Root |
| **Level-order**| Breadth-first |

---

## 💡 Real-World Examples

| Application          | Tree Used         |
|----------------------|-------------------|
| File System          | N-ary Tree        |
| Google Search        | Trie              |
| Heap Sorting / PQ    | Binary Heap       |
| MySQL/DB Indexing    | B+ Tree           |
| Compiler Design      | Syntax Tree       |
| AI Decision Making   | Decision Tree     |

---

