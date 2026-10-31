---
name: threejs-webgl-modernist
description: Builds Apple and Awwwards-caliber interactive 3D web experiences, floating holographic models, PBR materials, and 60fps GPU-optimized WebGL scenes.
---

# Three.js & WebGL Modernist 3D Experiences

This skill directs the creation of ultra-performant, high-end 3D web environments using Three.js, React Three Fiber (R3F), and native WebGL.

## 1. 3D Scene Architecture & Lighting

1. **Photorealistic PBR Materials**:
   - Leverage `MeshPhysicalMaterial` with realistic `roughness`, `metalness`, `transmission` (frosted glass/acrylic), and clearcoat layers.
   - Use high-dynamic-range environment maps (HDRIs) with tone mapping (`ACESFilmicToneMapping`) for cinematic reflections without bloated directional lights.
2. **Camera & Responsive Viewports**:
   - Handle aspect ratio resizing cleanly on window resize:
     `camera.aspect = width / height; camera.updateProjectionMatrix(); renderer.setSize(width, height);`
   - Implement mouse-parallax spring physics: camera subtly tracks cursor motion smoothly.

## 2. 60fps/120fps GPU Performance Discipline
- **Geometry Instancing**: Never render thousands of independent meshes. Always use `InstancedMesh` to render repetitive particles, floating shards, or geometric grids in a single GPU draw call.
- **Dispose Protocol**: Explicitly call `.dispose()` on geometries, materials, and textures when components unmount to prevent catastrophic WebGL memory leaks and context loss.
