---
name: fluid-design-tokens
description: Generates mathematical fluid typography, scalable spacing tokens, and contrast-guaranteed dark mode palettes using CSS clamp() formulas.
---

# Mathematical Fluid Design Tokens & Dynamic Theming

This skill directs the generation of screen-agnostic fluid typography, proportional spacing scales, and WCAG-compliant dynamic theming tokens.

## 1. CSS `clamp()` Mathematical Scaling

1. **Fluid Typography Formula**:
   - Calculate linear interpolation between minimum viewport (e.g. 375px mobile) and maximum viewport (e.g. 1440px desktop):
     `font-size: clamp(1rem, 0.8rem + 1vw, 1.5rem);`
   - Eliminates hundreds of fragmented `@media` queries; text scales continuously like a vector.
2. **Harmonic Spacing Scales**:
   - Apply fluid padding and gap tokens (`--space-sm`, `--space-md`, `--space-lg`) using proportional viewport percentages.

## 2. Contrast-Guaranteed OKLCH Color Systems
- Define design tokens in `oklch()` color space for perceptually uniform lightness and chroma adjustments.
- Automatically guarantee minimum 4.5:1 contrast ratios between foreground text and dynamic dark/light mode background surfaces.
