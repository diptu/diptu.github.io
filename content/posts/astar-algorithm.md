---
title: "A* Search Algorithm"
date: 2024-11-10
tags: ["Algorithms", "Pathfinding", "Graph-Search"]
summary: "An informed search algorithm that finds the shortest path using heuristics to guide exploration."
---

## Introduction

A* (A-Star) is an informed search algorithm that finds the shortest path between nodes in a weighted graph. It combines the cost-so-far from Dijkstra with a heuristic estimate to the goal, making it both optimal and efficient.

---

## Core Idea

A* evaluates each node using:

$$f(n) = g(n) + h(n)$$

| Component | Meaning |
|-----------|---------|
| $f(n)$ | Total estimated cost |
| $g(n)$ | Cost from start to current node |
| $h(n)$ | Heuristic estimate from current to goal |

---

## Algorithm Steps