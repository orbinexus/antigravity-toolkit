---
name: micro-interactions-physics
description: Crafts dynamic mouse spotlight hover effects, button tactile press physics, shimmer skeleton loading states, and living UI micro-animations.
---

# UI Micro-Interactions & Tactile Physics

This skill empowers the agent to inject life, tactile feedback, and interactive delight into digital components.

## 1. Living Surface Micro-Interactions

1. **Mouse Spotlight Hover Effect**:
   - Cards track cursor coordinates (`mousemove` event) and position a radial gradient:
     `background: radial-gradient(600px circle at ${x}px ${y}px, rgba(255,255,255,0.06), transparent 40%)`
   - Gives cards a physical spotlight shine that moves seamlessly across grids.
2. **Tactile Button Press**:
   - `active:scale-[0.98] transition-transform duration-100 ease-out`
   - Subtle inner glow: `shadow-[inset_0_1px_0_0_rgba(255,255,255,0.2)]`.

## 2. Skeleton Loaders & Progressive Feedback
- Replace boring circular spinners with pulsing gradient shimmer skeletons:
  `bg-gradient-to-r from-zinc-800 via-zinc-700 to-zinc-800 bg-[length:200%_100%] animate-shimmer`
- Tooltips: Snappy fade with micro-spring transform (`translate-y-1` to `translate-y-0`).
