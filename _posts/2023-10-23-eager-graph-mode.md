---
title: 'Eager Mode And Graph Mode'
date: 2023-10-23
permalink: /posts/2023/10/eager-graph-mode/
tags:
  - DL compilers
---

### Eager mode

Eager mode is similar to interpreting. In eager mode, operators in a model are immediately executed as they are encountered. Eager mode is easier to use, more suitable for ML researchers, and hence is the default mode of execution. The eager mode does not build graphs, and the operations return actual values instead of computational graphs to run later, and hence can introduce complex control flow operations and simplify the debugging. 

### Graph mode

In contrast, in graph mode, operators are first synthesized into a graph, which will then be compiled and executed as a whole.

Specifically, graph mode enables operator fusion, wherein one operator is merged with another to reduce/localize memory reads as well as total kernel launch overhead. Therefore, graph mode typically delivers higher performance and hence is heavily used in production.

### PyTorch and TensorFlow

PyTorch 2.x and TensorFlow 2.x now support both eager mode and graph mode.

### AD mechanism

There exists auto-differentiation (AD) mechanism in deep learning frameworks. With such a mechanism, users only need to declare the forward execution part of the DNN, and the framework automatically performs backpropagation. For example, in PyTorch, grad_fn in forward func will automatically generate for backward execution. In general, by calling the loss.backward, the backpropagation will be performed in the reverse order compared to forward operations.

### Reference

1. https://pytorch.org/blog/optimizing-production-pytorch-performance-with-graph-transformations/
2. https://towardsdatascience.com/eager-execution-vs-graph-execution-which-is-better-38162ea4dbf6