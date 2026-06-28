---
title: "Dijkstra's Algorithm"
date: 2024-11-12
tags: ["Algorithms", "Graph-Search", "Shortest-Path"]
summary: "The classic single-source shortest path algorithm for weighted graphs with non-negative edges."
---

## Introduction

Dijkstra's algorithm finds the shortest path from a source node to all other nodes in a weighted graph with non-negative edge weights. It is the foundation for many routing protocols and navigation systems.

---

## Core Idea

Maintain a set of visited nodes and a distance estimate for each node:

1. Start with source node distance = 0, all others = ∞
2. At each step, visit the unvisited node with smallest distance
3. Update neighbors' distances if a shorter path is found
4. Repeat until all nodes visited

---