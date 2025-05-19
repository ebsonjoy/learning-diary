# 🌐 Graph

**Date:** 2025-05-19

---

## 📘 What is a Graph?

- A **Graph** is a non-linear data structure consisting of:
  - **Vertices (Nodes)**: Entities
  - **Edges (Links)**: Connections between nodes

---

## ✨ Real-World Examples

| Example               | Description                           |
|------------------------|---------------------------------------|
| Social Networks        | Users = vertices, Friendships = edges |
| Maps / GPS             | Places = nodes, Roads = edges         |
| Web Page Links         | Pages = nodes, Hyperlinks = edges     |
| Networks (LAN/WAN)     | Devices = nodes, Cables = edges       |

---

## 🧱 Types of Graphs

| Type                 | Description |
|----------------------|-------------|
| **Directed**          | Edges have direction (A ➝ B) |
| **Undirected**        | Edges have no direction (A — B) |
| **Weighted**          | Edges have weights/costs |
| **Unweighted**        | No weights on edges |
| **Cyclic**            | Contains cycles (A ➝ B ➝ C ➝ A) |
| **Acyclic**           | No cycles |
| **Connected**         | Every node is reachable from another |
| **Disconnected**      | Some nodes are isolated |
| **Tree**              | Special type of acyclic connected graph |
| **DAG** (Directed Acyclic Graph) | Directed with no cycles (used in scheduling, compilers) |

---

## 💾 Graph Representations

### 1. Adjacency Matrix

2D matrix where G[i][j] = 1 if edge exists between i and j
Space: O(V²)

### 2. Adjacency List


Each node stores a list of its neighbors
Space: O(V + E)


---

## ⚙️ Graph Operations & Time Complexity

| Operation             | Adjacency List | Adjacency Matrix |
|------------------------|----------------|-------------------|
| Add Vertex             | O(1)           | O(V²) (rebuild matrix) |
| Add Edge               | O(1)           | O(1) |
| Remove Vertex          | O(V + E)       | O(V²) |
| Remove Edge            | O(E)           | O(1) |
| Search (DFS/BFS)       | O(V + E)       | O(V²) |
| Check Edge Existence   | O(V)           | O(1) |

---

## 🔍 Graph Traversal Algorithms

| Algorithm | Description | Time Complexity |
|----------|-------------|------------------|
| **DFS** (Depth First Search) | Explore as far as possible before backtracking | O(V + E) |
| **BFS** (Breadth First Search) | Explore neighbors first | O(V + E) |

---

## 🧠 Other Common Graph Algorithms

| Algorithm           | Purpose                          | Time Complexity |
|---------------------|----------------------------------|------------------|
| **Dijkstra’s**       | Shortest path (non-negative weights) | O(V + E log V) |
| **Bellman-Ford**     | Shortest path (with negative weights) | O(V × E) |
| **Floyd-Warshall**   | All-pairs shortest path          | O(V³) |
| **Kruskal’s**        | Minimum Spanning Tree            | O(E log E) |
| **Prim’s**           | Minimum Spanning Tree            | O(E + log V) |
| **Topological Sort** | Ordering in DAG                  | O(V + E) |

---

## ✅ Advantages

- Represents **complex relationships** (e.g., networks).
- Helps solve **shortest path**, **cycle detection**, **connectivity**, etc.
- Very useful in **real-life applications**.

---

## ❌ Disadvantages

- Graphs can be **space-consuming**, especially with adjacency matrices.
- Algorithms can be **computationally expensive** on large graphs.

---

## 📦 Use Cases of Graphs

| Area                | Example |
|---------------------|---------|
| **Social Networks** | Friend suggestions |
| **Maps/GPS**        | Shortest path |
| **Computer Networks** | Routing algorithms |
| **Search Engines**  | Page ranking (Google) |
| **Compilers**       | Task scheduling using DAG |
| **Games**           | AI navigation/pathfinding |

---

## 🧭 Summary

- Graph = Nodes + Edges
- Types: Directed/Undirected, Weighted/Unweighted, Cyclic/Acyclic
- Use **Adjacency List** for space efficiency
- Important algorithms: DFS, BFS, Dijkstra’s, MST (Kruskal/Prim)
