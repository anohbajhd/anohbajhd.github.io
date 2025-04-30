+++
date = '2025-05-01T00:46:56+05:00'
title = "Dijkstra's Algorithm: Your GPS for the World of Graphs"
tags = ['dijkstra', 'algorithm', 'ubuntu', 'graphs']
+++


# Introduction

Dijkstra’s Algorithm is a popular and efficient algorithm used for finding the shortest path from a single source node to all other nodes in a weighted graph. It is widely used in network routing, mapping applications, and many areas of computer science.

---

## What Is Dijkstra’s Algorithm?

Dijkstra’s Algorithm solves the single-source shortest path problem in a graph with **non-negative edge weights**. It finds the shortest path from a starting node (source) to every other node in the graph.

---

## Key Characteristics

- **Graph Type**: Works on both directed and undirected graphs.

### Directed Graph (Digraph)
- A directed graph has edges with a direction — like a one-way street. Each edge goes from one node to another specific node.  
- Example: If there’s an edge from A to B, it doesn't mean you can go from B to A unless there's a separate edge for that.  
🡒 Notation: **A → B**

### Undirected Graph
- An undirected graph has edges without direction — like a two-way street. If there's an edge between two nodes, you can move in both directions.  
- Example: If there's an edge between A and B, you can go from A to B and also from B to A.  
🡒 Notation: **A — B**

- **Edge Weights**: Requires all edge weights to be non-negative.
- **Optimality**: Guarantees the shortest path from the source to every other node.
- **Greedy Approach**: Selects the node with the smallest known distance at each step.

---

## Terminologies

- **Node/Vertex**: A point in the graph.
- **Edge**: A connection between two nodes.
- **Weight**: The cost to travel between two connected nodes.
- **Visited Set**: Nodes whose shortest distance from the source is finalized.
- **Distance Map**: Stores the currently known shortest distance from the source to each node.

---

## How the Algorithm Works

### Initialization

- Set the distance to the source node as `0`.
- Set the distance to all other nodes as `∞` (infinity).
- Keep all nodes as unvisited.
- Create a priority queue or min-heap to fetch the node with the smallest distance.

> **Priority Queue**: A priority queue is like a line where each item has a number (priority), and the item with the smallest number gets picked first — not just the one who came first. In Dijkstra’s Algorithm, it helps quickly find the next closest node to visit.

---

### Main Loop

1. Pick the unvisited node with the smallest known distance.
2. For each of its neighbors:
   - Calculate the new distance using:  
     `new_distance = current_distance + edge_weight`
   - If `new_distance` is less than the known distance, update it.
3. Mark the current node as visited.
4. Repeat until all nodes are visited or the shortest path is found.

---

## Example

Given the following weighted graph:

A ---3--- B  
|         |  
1         2  
|         |  
C ---4--- D


**Starting from A:**

- Initial distances: A = 0, B = ∞, C = ∞, D = ∞
- Visit A: Update B = 3, C = 1
- Visit C: Update D = 1 + 4 = 5
- Visit B: Update D = min(5, 3 + 2) = 5 (no change)
- Final distances: A = 0, B = 3, C = 1, D = 5

---

## Why Dijkstra Does Not Support Negative Weights

Dijkstra’s Algorithm assumes that once the shortest path to a node is found, it will not change. This assumption fails with **negative weights**, where a shorter path might appear later. Therefore, the algorithm does **not work correctly with negative-weight edges**.

---

## Comparison with Other Algorithms

| Algorithm      | Handles Negative Weights | Use Case                                      |
|----------------|---------------------------|-----------------------------------------------|
| Dijkstra       |    No                     | Fastest for non-negative weights              |
| Bellman-Ford   |    Yes                    | Used when graph may contain negative weights  |
| Floyd-Warshall |    Yes                    | Computes all-pairs shortest paths             |
| A* Search      |    (typically)            | Best for pathfinding with a known goal        |

---

## Applications

- GPS and Navigation systems
- Network routing protocols (e.g., OSPF)
- Robot and AI pathfinding
- Traffic simulation
- Flight scheduling systems

---

## Summary

- Dijkstra’s Algorithm is used to find the shortest paths from a single source node to all other nodes.
- It works only with non-negative edge weights.
- The algorithm uses a greedy approach and a priority queue for efficiency.
- It’s fast, reliable, and widely used in real-world applications.
