---
title: "Path Planning"
date: 2024-11-15
draft: true
archived: true
tags: ["Algorithms", "Robotics", "Path-Planning", "Motion-Planning"]
summary: "Fundamental techniques for robot motion planning from grid-based search to sampling-based methods."

---

## Introduction

Path planning is the computational problem of finding a valid sequence of movements from a start configuration to a goal configuration while avoiding obstacles. It is central to robotics, autonomous vehicles, video games, and logistics.

---

## Problem Formulation

Given:
- **Configuration space** $C$ — all possible robot poses
- **Obstacle space** $C_{obs} \subset C$
- **Free space** $C_{free} = C \setminus C_{obs}$
- **Start** $q_{start} \in C_{free}$
- **Goal** $q_{goal} \in C_{free}$

Find: A continuous path $\tau: [0, 1] \to C_{free}$ where $\tau(0) = q_{start}$ and $\tau(1) = q_{goal}$.

---

## Taxonomy of Path Planning

| Category | Methods | Use Case |
|----------|---------|----------|
| **Grid-based** | A*, Dijkstra, D* | Discrete environments, games |
| **Sampling-based** | RRT, RRT*, PRM | High-dimensional spaces |
| **Optimization-based** | CHOMP, TrajOpt | Smooth trajectories |
| **Reactive** | Potential fields, Bug algorithms | Real-time obstacle avoidance |

---

