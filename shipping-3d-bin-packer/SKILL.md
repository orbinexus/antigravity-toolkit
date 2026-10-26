---
name: shipping-3d-bin-packer
description: Solves 3D bin packing problems to select optimal box packaging sizes and packing orientations for multi-item e-commerce orders, minimizing dimensional weight freight costs.
---

# 3D Bin Packing & Box Selection Optimizer

This skill directs 3D volumetric packaging optimization algorithms, calculating the smallest carton box required to fit multi-item orders.

## 1. 3D Bin Packing Algorithm

1. **Item & Box Geometry**:
   - Model items as cuboids: `(Length, Width, Height, Weight)`.
   - Consider item fragility, rotational constraints (e.g. shampoo bottle cannot be rotated upside down), and max box weight limits.
2. **Heuristic Placement**:
   - Implement First Fit Decreasing (FFD) or Guillotine cutting heuristics to test packing configurations across standard company box inventory (Small, Medium, Large, Extra Large).
3. **Dimensional Weight (DIM Weight) Cost Reduction**:
   - `DIM Weight = (Length * Width * Height) / Dimensional Divisor (e.g. 5000)`.
   - Minimize empty void space to eliminate carrier dimensional weight surcharges.
