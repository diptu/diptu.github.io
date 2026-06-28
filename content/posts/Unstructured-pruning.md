---
title: "UnStructured 🤝🏾 Pruning"
date: 2026-06-27
draft: false
archived: false
tags: ["ML", "Model Compression", "Model-Pruning", "Deep Learning"]
summary: "Reduce model size by removing individual weights while maintaining model accuracy through sparse neural networks."
---
# Unstructured 🤝🏾 Pruning

Unstructured pruning is a model compression technique that removes **individual weights** from a neural network rather than entire neurons or channels. Instead of deleting complete structures, it sets less important weights to **zero**, creating a **sparse neural network**.

Unlike structured pruning, the architecture remains unchanged, but many connections become inactive.

---

## What is Unstructured Pruning?

Consider the following weight matrix:

```text
Before

[
  0.8  -0.3   0.6
 -0.1   0.4   0.9
  0.2  -0.7   0.5
]
```

After pruning 40% of the smallest weights:

```text
[
  0.8   0.0   0.6
  0.0   0.0   0.9
  0.0  -0.7   0.5
]
```

The model still has the **same dimensions**, but many values are zero.

---

## Why Unstructured Pruning?

Neural networks often contain millions—or even billions—of parameters.

Research has shown that many of these parameters contribute very little to the final prediction. By removing insignificant weights, we can:

* Reduce memory usage
* Compress model storage
* Lower communication cost during distributed training
* Improve inference on hardware supporting sparse computation
* Reduce overfitting in some cases

---

## Structured vs Unstructured Pruning

| Aspect                        | Unstructured Pruning    | Structured Pruning         |
| ----------------------------- | ----------------------- | -------------------------- |
| **Removed elements**          | Individual weights      | Channels, filters, neurons |
| **Network shape**             | Unchanged               | Modified                   |
| **Sparsity**                  | Fine-grained            | Coarse-grained             |
| **Compression ratio**         | Very high               | Moderate                   |
| **Hardware acceleration**     | Requires sparse kernels | Works on standard hardware |
| **Implementation complexity** | Moderate                | Easier deployment          |

---

## Types of Unstructured Pruning

### Magnitude-Based Pruning

The simplest and most widely used method.

Weights with the **smallest absolute values** are removed.

Example:

```text
Weights:

[0.91, -0.02, 0.63, 0.01, -0.78]

↓

Pruned:

[0.91, 0.00, 0.63, 0.00, -0.78]
```

Small weights usually contribute less to the output.

---

### Global Pruning

Instead of pruning layer by layer, all weights across the network compete together.

```text
Layer 1

0.8
0.02
0.5

Layer 2

0.7
0.01
0.4

↓

Remove the globally smallest weights.
```

Advantages:

* Better overall sparsity
* More flexible allocation of parameters

---

### Layer-wise Pruning

Each layer prunes a fixed percentage independently.

Example:

```text
Conv1 → prune 20%

Conv2 → prune 20%

Linear → prune 20%
```

This avoids removing too many weights from a single layer.

---

## Importance Metrics

The importance of a weight can be estimated in several ways.

| Method           | Idea                                             |
| ---------------- | ------------------------------------------------ |
| Magnitude        | Small absolute values are less important         |
| Gradient         | Small gradients imply low influence              |
| Hessian          | Uses second-order information                    |
| Taylor Expansion | Estimates change in loss after removing a weight |
| SNIP             | Measures connection sensitivity before training  |
| GraSP            | Preserves gradient flow during pruning           |

---

## PyTorch Example

PyTorch provides built-in pruning utilities through `torch.nn.utils.prune`.

```python
import torch
import torch.nn as nn
import torch.nn.utils.prune as prune

model = nn.Sequential(
    nn.Linear(100, 50),
    nn.ReLU(),
    nn.Linear(50, 10)
)

# Prune 30% of weights using L1 magnitude
prune.l1_unstructured(
    model[0],
    name="weight",
    amount=0.30
)

print(model[0].weight)
```

---

## Making Pruning Permanent

Initially, pruning only applies a **mask**.

To permanently remove the mask:

```python
prune.remove(model[0], "weight")
```

The masked weights become permanent zeros.

---

## Iterative Pruning

Instead of pruning a large percentage at once, prune gradually.

```text
Train

↓

Prune 10%

↓

Fine-tune

↓

Prune another 10%

↓

Fine-tune

↓

Repeat
```

This usually preserves higher accuracy.

---

## Lottery Ticket Hypothesis

One of the most influential ideas in pruning is the **Lottery Ticket Hypothesis**.

It states:

> Within a large randomly initialized neural network exists a much smaller subnetwork that can achieve nearly the same accuracy when trained in isolation.

This suggests that large models contain "winning tickets" that are sufficient for learning.

---

## Advantages

* Extremely high sparsity
* Significant model compression
* Reduced storage requirements
* Lower communication overhead
* Can retain high accuracy
* Supported by many research papers

---

## Limitations

* No change in network architecture
* Sparse computation is not efficiently supported on all hardware
* GPU speedups are often limited
* Additional sparse matrix libraries may be required
* Fine-tuning is usually necessary after pruning

---

## Typical Workflow

```text
Train Dense Model
        │
        ▼
Compute Importance Scores
        │
        ▼
Remove Small Weights
        │
        ▼
Fine-tune Model
        │
        ▼
Repeat (Optional)
        │
        ▼
Deploy Sparse Model
```

---

## When Should You Use It?

Use unstructured pruning when:

* Storage size matters more than inference speed.
* Target hardware supports sparse computation.
* Deploying models on memory-constrained devices.
* Compressing large language models or transformer-based architectures.
* Reducing communication costs in distributed training.

---

## Best Practices

* Start with **10–30% sparsity** and gradually increase.
* Prefer **iterative pruning** over one-shot pruning.
* Fine-tune after every pruning stage.
* Use **global pruning** for better compression.
* Combine pruning with **quantization** for maximum model size reduction.
* Evaluate both **accuracy** and **latency**, as higher sparsity does not always translate into faster inference.

---

## Summary

Unstructured pruning is a **fine-grained model compression technique** that removes individual, less important weights to create sparse neural networks. It achieves excellent compression while often preserving model accuracy, making it ideal for reducing storage and memory usage. However, because the network structure remains unchanged, real-world inference speed improvements depend heavily on hardware support for sparse computations.

It is one of the foundational techniques in model compression and is frequently combined with **quantization**, **knowledge distillation**, and **structured pruning** to build efficient deep learning models for production deployment.
