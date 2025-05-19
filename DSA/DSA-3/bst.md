# 🌳 Binary Search Tree (BST)

**Date:** 2025-05-19

---

## 📘 What is a BST?

- A **Binary Search Tree** is a binary tree where:
  - The **left child** has a value **less than** the parent.
  - The **right child** has a value **greater than** the parent.
- Ensures faster search and ordered structure.

---

## ⚙️ Common BST Operations with Time Complexities

| Operation          | Description                                                                 | Average Case | Worst Case |
|--------------------|-----------------------------------------------------------------------------|--------------|-------------|
| **Insert**         | Add a new node to the correct position following BST rules.                 | O(log n)     | O(n)        |
| **Search**         | Find a value by comparing and traversing left/right.                        | O(log n)     | O(n)        |
| **Delete**         | Remove a node and rearrange links to maintain BST structure.                | O(log n)     | O(n)        |
| **Inorder Traversal**   | Traverse left → root → right (returns sorted values).                     | O(n)         | O(n)        |
| **Preorder Traversal**  | Traverse root → left → right.                                             | O(n)         | O(n)        |
| **Postorder Traversal** | Traverse left → right → root.                                             | O(n)         | O(n)        |
| **Level Order Traversal** | Traverse level by level using a queue (BFS style).                     | O(n)         | O(n)        |
| **Min Value**      | Go to the leftmost node.                                                   | O(log n)     | O(n)        |
| **Max Value**      | Go to the rightmost node.                                                  | O(log n)     | O(n)        |
| **Height of Tree** | Measure the longest path from root to leaf.                                | O(n)         | O(n)        |
| **Is Balanced**    | Check if left and right subtree heights differ by no more than 1.          | O(n)         | O(n)        |
| **Count Nodes**    | Count total number of nodes in the BST.                                    | O(n)         | O(n)        |
| **Count Leaf Nodes** | Count nodes with no children.                                              | O(n)         | O(n)        |
| **Validate BST**   | Ensure the tree follows BST rules throughout.                              | O(n)         | O(n)        |
| **Find Inorder Successor** | Find the next greater value after a given node.                     | O(log n)     | O(n)        |
| **Find Inorder Predecessor** | Find the previous smaller value before a given node.              | O(log n)     | O(n)        |
| **Lowest Common Ancestor (LCA)** | Find the lowest shared ancestor of two nodes.               | O(log n)     | O(n)        |
| **Kth Smallest / Largest** | Find the kth smallest/largest using modified inorder traversal.     | O(k)         | O(k)        |
| **Range Sum / Range Count** | Sum or count of values between a given range [L, R].              | O(log n + k) | O(n)        |

---

## 🧠 Notes

- **Average Case:** Balanced tree → height is log(n).
- **Worst Case:** Skewed tree (like linked list) → height becomes n.
- **Self-balancing trees** like **AVL** and **Red-Black** avoid worst cases.

---


## ✅ Advantages of BST

- **Efficient Search, Insert, and Delete**: O(log n) time in average case.
- **Sorted Data Retrieval**: Inorder traversal gives sorted order.
- **Flexible Size**: Dynamically grows and shrinks with insertions and deletions.
- **Custom Orderings**: Can create trees for specific orderings of data.
- **Memory Efficient**: Linked-node structure uses memory efficiently (no unused space like arrays).

---

## ❌ Disadvantages of BST

- **Unbalanced Tree = Poor Performance**: Worst-case time becomes O(n) if not balanced.
- **More Complex than Arrays/Linked Lists**: Requires additional logic for maintaining structure.
- **No Random Access**: Accessing the k-th element takes O(k) time.
- **Rebalancing Not Automatic**: Requires additional logic or self-balancing variants (like AVL, Red-Black).

---

## 💡 Real-Life Applications of BST

| Application                           | Description |
|--------------------------------------|-------------|
| **Database Indexing**                | BST variants like B-Trees used to index and retrieve data efficiently. |
| **Searching in Large Datasets**      | Quickly find records from sorted data. |
| **Dynamic Sorting**                  | Keeps items in sorted order with fast insert/delete (e.g. event queues). |
| **Symbol Table in Compilers**        | BSTs are used to maintain variable scopes and symbol tables. |
| **Autocomplete Suggestions**         | With prefix trees and BSTs combined for optimized search. |
| **Memory Management in OS**          | Used in free space management or memory allocation trees. |
| **Map and Set Data Structures**      | Many language libraries (like Java `TreeMap`, C++ `map`) use self-balancing BSTs.

---