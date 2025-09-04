---
layout: cheatsheet
title: Data Structures & Sorting Cheatsheet
category: programming
---

# Data Structures & Sorting Cheat Sheet

| Structure / Algorithm                 | Search (Avg) | Insert (Avg) | Delete (Avg) | Search (Worst) | Insert (Worst) | Delete (Worst) | **Sort Time**                                             |
| ------------------------------------- | ------------ | ------------ | ------------ | -------------- | -------------- | -------------- | --------------------------------------------------------- |
| **Array**                             | O(n)         | O(n)         | O(n)         | O(n)           | O(n)           | O(n)           | **O(n log n)** (e.g., quicksort/mergesort)                |
| **Dynamic Array (list/vector)**       | O(n)         | O(1)*        | O(n)         | O(n)           | O(n)           | O(n)           | **O(n log n)**                                            |
| **Singly Linked List**                | O(n)         | O(1)         | O(1)         | O(n)           | O(1)           | O(1)           | **O(n log n)** (merge sort)                               |
| **Doubly Linked List**                | O(n)         | O(1)         | O(1)         | O(n)           | O(1)           | O(1)           | **O(n log n)** (merge sort)                               |
| **Stack**                             | O(n)         | O(1)         | O(1)         | O(n)           | O(1)           | O(1)           | N/A                                                       |
| **Queue**                             | O(n)         | O(1)         | O(1)         | O(n)           | O(1)           | O(1)           | N/A                                                       |
| **Deque**                             | O(n)         | O(1)         | O(1)         | O(n)           | O(1)           | O(1)           | N/A                                                       |
| **Binary Search Tree (BST)**          | O(log n)     | O(log n)     | O(log n)     | O(n)           | O(n)           | O(n)           | **O(n log n)** (in-order traversal + rebalance if needed) |
| **AVL Tree**                          | O(log n)     | O(log n)     | O(log n)     | O(log n)       | O(log n)       | O(log n)       | **O(n log n)**                                            |
| **Red-Black Tree**                    | O(log n)     | O(log n)     | O(log n)     | O(log n)       | O(log n)       | O(log n)       | **O(n log n)**                                            |
| **Heap (Min/Max)**                    | O(n)         | O(log n)     | O(log n)     | O(n)           | O(log n)       | O(log n)       | **O(n log n)** (heap sort)                                |
| **Skip List**                         | O(log n)     | O(log n)     | O(log n)     | O(n)           | O(n)           | O(n)           | **O(n log n)**                                            |
| **Trie (Prefix Tree)**                | O(k)         | O(k)         | O(k)         | O(k)           | O(k)           | O(k)           | **O(n·k)** (lexicographic traversal)                      |
| **Hash Map / Dictionary (unordered)** | O(1)         | O(1)         | O(1)         | O(n)           | O(n)           | O(n)           | **O(n log n)** (need to extract keys/values + sort)       |
| **Tree Map / Ordered Map**            | O(log n)     | O(log n)     | O(log n)     | O(log n)       | O(log n)       | O(log n)       | **O(n log n)**                                            |
| **Skip List Map**                     | O(log n)     | O(log n)     | O(log n)     | O(n)           | O(n)           | O(n)           | **O(n log n)**                                            |
| **Trie Map (string keys)**            | O(k)         | O(k)         | O(k)         | O(k)           | O(k)           | O(k)           | **O(n·k)** (prefix order)                                 |
| **B-Tree / B+Tree**                   | O(log n)     | O(log n)     | O(log n)     | O(log n)       | O(log n)       | O(log n)       | **O(n log n)**


## Sorting Algorithms Quick Reference

| Algorithm          | Best       | Average    | Worst      | Stable? | Notes                                                   |
| ------------------ | ---------- | ---------- | ---------- | ------- | ------------------------------------------------------- |
| **Quicksort**      | O(n log n) | O(n log n) | O(n²)      | No      | Very fast in practice, worst-case rare with good pivots |
| **Mergesort**      | O(n log n) | O(n log n) | O(n log n) | Yes     | Needs O(n) extra space                                  |
| **Heapsort**       | O(n log n) | O(n log n) | O(n log n) | No      | In-place, slower constants than quicksort               |
| **Insertion Sort** | O(n)       | O(n²)      | O(n²)      | Yes     | Good for small or nearly sorted data                    |
| **Selection Sort** | O(n²)      | O(n²)      | O(n²)      | No      | Rarely used in practice                                 |
| **Bubble Sort**    | O(n)       | O(n²)      | O(n²)      | Yes     | Educational, not practical                              |
| **Counting Sort**  | O(n + k)   | O(n + k)   | O(n + k)   | Yes     | For integers in a limited range                         |
| **Radix Sort**     | O(n·k)     | O(n·k)     | O(n·k)     | Yes     | k = digit/key length                                    |
| **Bucket Sort**    | O(n + k)   | O(n + k)   | O(n²)      | Depends | Works best with uniform distribution                    |
