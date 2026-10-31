---
name: runtime-performance-budget
description: Enforces strict 60fps/120fps UI render budgets, zero layout-thrashing, sub-1-second LCP, and aggressive GPU compositing optimizations.
---

# UI Runtime Performance Budget & 60fps Discipline

This skill guarantees that rich 3D visuals, complex animations, and dense dashboards run buttery smooth without causing battery drain, dropped frames, or laggy scrolling.

## 1. Frame Budget & GPU Compositing

1. **16ms Frame Budget**:
   - Every animation tick must resolve in < 16.6ms (for 60Hz) or < 8.3ms (for 120Hz ProMotion screens).
   - Animate strictly composite properties: `transform` and `opacity`.
   - Never animate `height`, `width`, `top`, `margin`, or `padding` directly without CSS `will-change: transform`.
2. **Layout Thrashing Elimination**:
   - Never interleave DOM style writes (`element.style.width = ...`) with DOM geometry reads (`element.offsetWidth`).
   - Batch all reads first, then execute writes in a single `requestAnimationFrame` pass.

## 2. Dynamic Performance Degradation
- Detect lower-end mobile devices or battery saver modes (`navigator.hardwareConcurrency < 4` or high frame drops).
- Automatically toggle off expensive post-processing bloom shaders, falling back to clean CSS gradients without degrading functionality.
