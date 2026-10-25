---
name: framer-motion-wizard
description: Designs and crafts Awwwards-caliber web animations, micro-interactions, scroll-driven effects, gesture physics, and fluid transitions using Framer Motion, Tailwind CSS, and modern React.
---

# Framer Motion & Micro-Interactions Wizard

This skill empowers the agent to build award-winning interactive UI elements, silky smooth layout transitions, and high-performance physics-based motion in React and Next.js applications.

## 1. Animation Design Principles

- **Fluid Springs over Linear Easing**: Always prefer spring physics (`stiffness`, `damping`, `mass`) for interactive widgets like modals, buttons, and cards.
- **Performance First**: Animate strictly GPU-accelerated CSS properties (`transform: translate3d/scale/rotate` and `opacity`). Never animate `top`, `left`, `width`, `height`, or `margin` directly without `layout` prop.
- **Reduced Motion Support**: Respect user accessibility preferences (`useReducedMotion` hook).

## 2. Core Interactive Patterns

### A. Magnetic Hover Buttons
```tsx
import { motion, useMotionValue, useSpring } from "framer-motion";
import { useRef } from "react";

export function MagneticButton({ children }: { children: React.ReactNode }) {
  const ref = useRef<HTMLButtonElement>(null);
  const x = useMotionValue(0);
  const y = useMotionValue(0);
  const springX = useSpring(x, { stiffness: 150, damping: 15 });
  const springY = useSpring(y, { stiffness: 150, damping: 15 });

  const handleMouseMove = (e: React.MouseEvent) => {
    if (!ref.current) return;
    const { left, top, width, height } = ref.current.getBoundingClientRect();
    x.set((e.clientX - (left + width / 2)) * 0.35);
    y.set((e.clientY - (top + height / 2)) * 0.35);
  };

  const handleMouseLeave = () => {
    x.set(0);
    y.set(0);
  };

  return (
    <motion.button
      ref={ref}
      style={{ x: springX, y: springY }}
      onMouseMove={handleMouseMove}
      onMouseLeave={handleMouseLeave}
      whileTap={{ scale: 0.95 }}
      className="px-6 py-3 rounded-full bg-gradient-to-r from-blue-500 to-indigo-600 text-white font-medium shadow-lg"
    >
      {children}
    </motion.button>
  );
}
```

### B. Scroll-Triggered Reveal with Stagger
- Use `useScroll` with `useTransform` for parallax effects.
- Use `variants` with `staggerChildren: 0.08` for seamless list and grid reveals.

### C. Layout Morphing (`layoutId`)
- Utilize `layoutId` across shared components (e.g. active tab indicators, expanding cards to modal views) for zero-jank morphing.
