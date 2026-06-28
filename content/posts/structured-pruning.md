---
title: "Structured 🤝🏾 Pruning"
date: 2026-06-27
draft: false
archived: false
tags: ["ML", "Quantization", "Model-Pruning"]
summary: "Reducing model size and inference latency through structured weight pruning techniques for edge deployment."

---

## Structured pruning 

Structured pruning removes entire channels, filters, or layers from a neural network rather than individual weights. This produces hardware-friendly sparse models that can run efficiently on GPUs and edge accelerators.

---

## Why Structured Pruning?

| Aspect | Unstructured Pruning | Structured Pruning |
|--------|---------------------|-------------------|
| **Sparsity pattern** | Random weights zeroed | Entire channels removed |
| **Hardware speedup** | Limited (needs sparse kernels) | Direct speedup on standard hardware |
| **Model size** | Smaller (with compression) | Smaller (native) |
| **Implementation** | Complex | Straightforward |

---

## Methods

### Channel Pruning

Remove entire input/output channels based on importance scores:

- **L1 norm**: Sum of absolute weights per filter
- **L2 norm**: Euclidean norm of filter weights
- **BN scaling factor**: Use BatchNorm γ parameters as proxy for importance

### Filter Pruning

Similar to channel pruning but operates on convolutional filters:

```python
import torch
import torch.nn as nn

def prune_filters(model, pruning_ratio=0.3):
    for name, module in model.named_modules():
        if isinstance(module, nn.Conv2d):
            # Compute L1 norm per filter
            l1_norm = torch.sum(torch.abs(module.weight), dim=(1,2,3))
            n_prune = int(pruning_ratio * module.out_channels)
            _, prune_indices = torch.topk(l1_norm, n_prune, largest=False)
            
            # Create mask
            mask = torch.ones(module.out_channels)
            mask[prune_indices] = 0
            
            # Apply mask
            module.weight.data *= mask.view(-1, 1, 1, 1)
    return model