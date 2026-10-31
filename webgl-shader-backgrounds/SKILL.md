---
name: webgl-shader-backgrounds
description: Crafts hypnotic, lightweight GPU fragment shaders (GLSL), fluid neon waves, grain noise, and dynamic mesh gradients running in under 10KB.
---

# GLSL Fragment Shaders & Fluid WebGL Backgrounds

This skill guides the authoring of lightweight, standalone GLSL fragment shaders to create hypnotic living canvas backgrounds without video bandwidth overhead.

## 1. Fragment Shader Architecture

1. **Standard Uniforms**:
   - `uniform float u_time;` (Elapsed delta time).
   - `uniform vec2 u_resolution;` (Viewport dimensions in pixels).
   - `uniform vec2 u_mouse;` (Normalized mouse pointer coordinates).
2. **Noise & Procedural Gradients**:
   - Leverage Simplex Noise and Fractional Brownian Motion (FBM) directly in GLSL to generate silky organic fluid waves.
   - Mix colors using smooth Hermite interpolation (`smoothstep`) for neon atmospheric glows.

## 2. High-Performance Canvas Mounting
- Render to a fullscreen quad canvas positioned fixed behind content:
  `position: fixed; inset: 0; pointer-events: none; z-index: -1;`
- Cap pixel ratio: clamp `renderer.setPixelRatio(Math.min(window.devicePixelRatio, 2))` to prevent mobile GPUs from choking on 3x/4x retina displays.
