# 🔡 Trie (Prefix Tree)

**Date:** 2025-05-19

---

## 📘 What is a Trie?

- A **Trie** is a special type of **tree** used to store **strings**, especially useful for **prefix-based searching**.
- Each node represents a **character**, and the path from root to a node represents a **prefix** or a complete word.
- Words with the same prefix share the same initial path in the tree.

---

## 🧠 Example

Inserting `"cat"`, `"can"`, and `"car"` in a trie:

      (root)
       |
       c
       |
       a
     / | \
    t  n  r


---

## ⚙️ Common Operations with Time Complexities

| Operation     | Description                                   | Time Complexity |
|---------------|-----------------------------------------------|------------------|
| **Insert**     | Add a word to the Trie                        | O(L) — where L is the length of the word |
| **Search**     | Search for an exact word                      | O(L) |
| **StartsWith** | Check if any word starts with given prefix   | O(L) |
| **Delete**     | Remove a word from the Trie                   | O(L) |
| **Auto-complete** | Return all words with a given prefix      | O(L + M) — M is total matched characters |

---

## ✅ Advantages

- **Efficient prefix search**: Quickly find words that share a common prefix.
- **Fast lookup**: Faster than hashing for prefix matching.
- **Space-optimized for shared prefixes**: Saves space compared to storing full strings.
- **Autocomplete & Spell Checker**: Easily supports suggestions based on input prefix.

---

## ❌ Disadvantages

- **High memory usage**: Every character needs a node; sparse usage wastes memory.
- **Not suitable for numeric range queries**: Better for string-based structures.
- **Complex to implement**: Compared to hash maps or arrays.

---

## 🧩 Use Cases / Real-Life Applications

| Application               | Description |
|---------------------------|-------------|
| **Autocomplete systems**   | Suggests next words from input (Google, IDEs, etc.) |
| **Spell checkers**         | Detect and suggest corrections for words |
| **IP routing (Longest Prefix Matching)** | Used in networking |
| **Dictionary/Thesaurus apps** | Quick word lookup |
| **T9 keyboard prediction** | Suggests possible matches from number sequences |
| **Word games (like Boggle)** | Find all possible words from characters |

---

## 🏗️ Trie Node Structure (Conceptual)

Each node usually contains:
- A **map or array** of children (for each character)
- A **boolean flag** indicating if the node is the **end of a word**

---

## 📌 Summary

- Best for **string matching**, **prefix search**, **dictionary operations**.
- Avoid if memory is a major concern and prefix search is not required.

