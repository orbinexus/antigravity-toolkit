---
name: algorithmic-complexity-optimizer
description: Optimizes runtime time and space complexity, replacing O(N^2) loops with O(N) or O(1) hash lookups, two-pointers, sliding windows, and bitwise operations.
---

# Algorithmic Complexity & Big-O Optimizer

This skill audits execution profiles to eliminate algorithmic bottlenecks, excessive memory allocation, and nested loop degradations.

## 1. Complexity Reduction Patterns

1. **Quadratic ($O(N^2)$) to Linear ($O(N)$)**:
   - Replace nested array iterations (`array.filter(a => otherArray.includes(a.id))`) with pre-indexed `Set` or `Map` lookups ($O(1)$ amortized).
2. **Two-Pointer & Sliding Window**:
   - Process sorted arrays, subarray sums, and string substrings in a single linear pass ($O(N)$ time, $O(1)$ space).
3. **Memoization & Dynamic Programming**:
   - Cache expensive recursive subproblem calculations using LRU caches or hash tables to avoid exponential ($O(2^N)$) explosion.

## 2. Memory & Garbage Collection Optimization
- Pre-allocate arrays and buffers with known capacities to prevent continuous memory reallocation and copying.
- Pool reusable objects in high-frequency loops to minimize garbage collection (GC) pauses.
