# 🧱 Heap (Min Heap / Max Heap)

**Date:** 2025-05-19

---

## 📘 What is a Heap?

- A **Heap** is a **complete binary tree** that satisfies the **heap property**.
- Heaps are mainly used to **quickly access the smallest or largest element**.
- Commonly implemented using **arrays** (not linked nodes like binary trees).

---

## 🔄 Types of Heaps

| Type         | Property |
|--------------|----------|
| **Min Heap** | Parent node is **less than or equal** to its children. Root is the **minimum** element. |
| **Max Heap** | Parent node is **greater than or equal** to its children. Root is the **maximum** element. |

---

## 🧠 Heap Representation (Array Based)

For node at index `i`:
- Left child index: `2i + 1`
- Right child index: `2i + 2`
- Parent index: `(i - 1) / 2` (floor)

---

## ⚙️ Common Operations and Time Complexities

| Operation      | Description                            | Time Complexity |
|----------------|----------------------------------------|------------------|
| **Insert**      | Add a new element                      | O(log N) |
| **Peek**        | Return min/max (root) without removing | O(1) |
| **Extract**     | Remove min/max (root)                  | O(log N) |
| **Heapify**     | Convert array into a heap              | O(N) |
| **Merge Heaps** | Merge two heaps                        | O(N + M) |
| **Replace Root**| Replace and reorder heap               | O(log N) |

---

## ✅ Advantages

- Efficient **access to largest/smallest** element.
- Good for **priority queue** implementation.
- Easy to represent using arrays.
- Fast **insertion/deletion** compared to sorted arrays.

---

## ❌ Disadvantages

- **Not suitable** for fast searching of arbitrary elements.
- **Balancing logic** is more complex than simple arrays/lists.
- Can be inefficient when needing frequent **random access**.

---

## 🧩 Real-Life Applications

| Use Case                     | Description |
|------------------------------|-------------|
| **Priority Queues**           | Tasks with different priority levels |
| **Heap Sort Algorithm**       | In-place sorting using a heap |
| **Dijkstra’s Algorithm**      | Efficient shortest path algorithm |
| **A\* Pathfinding**           | Used in games/maps for optimal paths |
| **Median Maintenance**        | Keep track of median dynamically |
| **Job Scheduling**            | Based on priority or deadlines |
| **Load Balancing**            | Assign tasks based on least-loaded servers |

---

## 🏗️ Heap Variants

| Variant             | Purpose |
|---------------------|---------|
| **Binary Heap**      | Common form using binary tree |
| **Fibonacci Heap**   | Faster amortized time for some operations |
| **Binomial Heap**    | Used in advanced graph algorithms |
| **Pairing Heap**     | Simpler and faster in practice |
| **Skew Heap**        | Self-adjusting heap with simpler structure |

---

## 🔁 Heap vs Binary Search Tree (BST)

| Feature         | Heap              | BST                |
|-----------------|-------------------|---------------------|
| Structure       | Complete binary tree | Binary tree (not always complete) |
| Search          | O(N)               | O(log N) (balanced) |
| Insert/Delete   | O(log N)           | O(log N)            |
| Access min/max  | O(1)               | O(log N)            |

---

## 📌 Summary

- Use **Min Heap** when you frequently need the **minimum** element.
- Use **Max Heap** for **maximum** element access.
- Heaps are excellent for **priority-based scheduling** and **greedy algorithms**.

