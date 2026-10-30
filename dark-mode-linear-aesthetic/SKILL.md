---
name: dark-mode-linear-aesthetic
description: Designs ultra-sleek Linear and Vercel inspired modern dark-mode interfaces with glassmorphic cards, subtle radial glow spotlights, fine 1px translucent borders, and noise-textured backgrounds.
---

# Linear & Vercel Sleek Dark Mode Aesthetic

This skill directs the creation of ultra-modern, high-end digital product UIs modeled after Linear, Vercel, Supabase, and Raycast standards.

## 1. Color Palette & Surface Elevation

1. **True Depth over Flat Grays**:
   - Never use flat pitch `#000000` or washed-out `#333333`.
   - Use deep layered obsidian tones:
     - Base canvas: `#09090b` (Zinc-950) or `#030712` (Gray-950).
     - Raised card surface: `#121215` with `backdrop-blur-md` and `bg-white/[0.03]`.
     - Hovered state: `bg-white/[0.06]`.
2. **Subtle 1px Borders**:
   - Use hairline translucent borders: `border border-white/10` or `border-zinc-800/80`.
   - Never use harsh, opaque solid light borders in dark mode.

## 2. Lighting, Glows & Accents
- **Radial Spotlights**: Add ambient glows behind hero elements or under mouse hovers using `bg-[radial-gradient(ellipse_at_top,_var(--tw-gradient-stops))] from-indigo-500/15 via-transparent to-transparent`.
- **Accent Philosophy**: Single high-vibrancy accent color (Electric Violet, Emerald Neon, or Cyan) reserved strictly for primary CTA buttons and status pings.
- **Glassmorphism**: `backdrop-blur-xl bg-black/40 border border-white/10 shadow-[0_8px_32px_0_rgba(0,0,0,0.36)]`.
