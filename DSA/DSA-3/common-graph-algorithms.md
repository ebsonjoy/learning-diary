# ⚙️ Common Graph Algorithms

**Date:** 2025-05-19

---

## 🔍 What Are Graph Algorithms?

Graph algorithms are used to:
- Traverse graphs
- Find shortest paths
- Detect cycles
- Find minimum spanning trees
- Topologically sort nodes

---

## 🚶 1. **Graph Traversal**

### 🔹 Depth First Search (DFS)
- Explores as far as possible along one branch before backtracking.
- Can be implemented using recursion or a stack.
- **Time Complexity**: O(V + E)
- **Use Cases**: Path finding, cycle detection, topological sort.

### 🔹 Breadth First Search (BFS)
- Explores all neighbors at the current level before moving to the next.
- Uses a queue.
- **Time Complexity**: O(V + E)
- **Use Cases**: Shortest path in unweighted graphs, level-order traversal.

---

## 🛣️ 2. **Shortest Path Algorithms**

### 🔸 Dijkstra’s Algorithm
- Finds the shortest path from a source to all nodes (no negative weights).
- Uses a priority queue (min-heap).
- **Time Complexity**: O(V + E log V)
- **Use Case**: Maps (Google Maps, GPS), routing.

### 🔸 Bellman-Ford Algorithm
- Also finds the shortest path, but **works with negative weights**.
- Detects negative weight cycles.
- **Time Complexity**: O(V × E)
- **Use Case**: Currency arbitrage, graphs with negative costs.

### 🔸 Floyd-Warshall Algorithm
- All-pairs shortest path (i.e., from every node to every other node).
- Uses dynamic programming.
- **Time Complexity**: O(V³)
- **Use Case**: Precomputing shortest paths for small dense graphs.

---

## 🌲 3. **Minimum Spanning Tree (MST)**

An MST connects all the nodes in an **undirected**, **weighted** graph with the **minimum total edge weight** and **no cycles**.

### ✅ Properties
- Only for **connected, undirected** graphs.
- Spanning = includes all vertices.
- Tree = no cycles.

### 🛠️ Algorithms to Find MST:

#### 📌 Kruskal’s Algorithm
- Sort edges by weight.
- Add edges one by one (using Disjoint Set Union - DSU) to avoid cycles.
- **Time Complexity**: O(E log E)

#### 📌 Prim’s Algorithm
- Start from one node.
- Add the smallest edge connecting to an unvisited node (uses min-heap).
- **Time Complexity**: O(E + log V)

---

## 🔄 4. **Topological Sort**

- Applies to **Directed Acyclic Graphs (DAGs)**.
- Produces a linear ordering of tasks such that for every edge `u → v`, `u` comes before `v`.
- Implemented via:
  - DFS + Stack
  - BFS (Kahn’s Algorithm)

- **Time Complexity**: O(V + E)
- **Use Case**: Task scheduling, build systems, course prerequisite order.

---

## 🔁 5. **Cycle Detection**

### In Undirected Graph:
- Use DFS and track parent nodes.
- Or use Disjoint Set Union (Union-Find).

### In Directed Graph:
- Use DFS and a recursion stack.

- **Time Complexity**: O(V + E)
- **Use Case**: Detect deadlocks, infinite loops.

---

## 🔍 6. **Connected Components**

- Find all isolated subgraphs in an undirected graph.
- Use DFS/BFS.
- **Time Complexity**: O(V + E)

---

## 🧠 Summary Table

| Algorithm         | Use Case                         | Time Complexity  |
|------------------|----------------------------------|------------------|
| DFS              | Traversal, cycle detection       | O(V + E)         |
| BFS              | Traversal, shortest unweighted   | O(V + E)         |
| Dijkstra         | Shortest path (no negative)      | O(V + E log V)   |
| Bellman-Ford     | Shortest path (with negative)    | O(V × E)         |
| Floyd-Warshall   | All-pairs shortest path          | O(V³)            |
| Kruskal          | Minimum Spanning Tree            | O(E log E)       |
| Prim             | Minimum Spanning Tree            | O(E + log V)     |
| Topological Sort | Task ordering in DAG             | O(V + E)         |
| Cycle Detection  | Deadlock detection               | O(V + E)         |
| Connected Components | Find isolated graphs         | O(V + E)         |

---

## ✅ Real-Life Use Cases

| Problem               | Algorithm       |
|------------------------|-----------------|
| Finding shortest route | Dijkstra        |
| Task build order       | Topological Sort|
| Cable/road optimization| Kruskal / Prim  |
| Internet routing       | BFS / Dijkstra  |
| Detecting fraud cycles | Cycle Detection |

