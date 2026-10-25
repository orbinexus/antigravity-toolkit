---
name: svg-infographic-architect
description: Designs and generates scalable, pixel-perfect SVG diagrams, mind maps, technical architecture visualizers, and cheat sheets with embedded CSS styles.
---

# SVG Infographic & Diagram Architect

This skill guides the direct procedural generation of crisp, standalone vector graphics (SVG) for architecture diagrams, comparison flowcharts, and technical infographics.

## 1. Vector Design Standards

1. **Responsiveness & ViewBox**:
   - Always use a properly proportioned `viewBox` (e.g. `0 0 1200 800`) and omit hardcoded pixel width/height where embedding in web containers.
2. **Modern Color Schemes & Typography**:
   - Utilize clean developer aesthetics (Dark mode slate backgrounds `#0f172a`, vibrant accent gradients, clean system sans-serif fonts: Inter, SF Pro, system-ui).
3. **Hierarchy & Visual Containers**:
   - Use rounded rectangle cards (`rx="12"`), drop-shadow filter definitions (`<filter id="shadow">`), and glowing subtle borders.
   - Use distinct color coding for inputs, processing units, data storage, and external outputs.

## 2. Connectors and Flowlines

- Use cubic/quadratic bezier paths (`M ... C ...`) or orthogonal stepped lines with rounded markers (`<marker id="arrowhead">`).
- Add dashed stroke animation capabilities (`stroke-dasharray`, `stroke-dashoffset`) for depicting real-time data flow.
