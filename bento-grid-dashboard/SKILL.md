---
name: bento-grid-dashboard
description: Structures Apple and Linear style asymmetric Bento Grid layouts, multi-metric analytical cards, and balanced dashboard viewports with zero clutter.
---

# Bento Grid Dashboard & Product Architecture

This skill guides the construction of asymmetric, visually captivating Bento Grid layouts popularized by Apple, Linear, and Supabase marketing and dashboard pages.

## 1. Bento Grid Geometry & Rhythms

1. **Asymmetric Grid Spans**:
   - Never arrange dashboards in repetitive, monotonous 4x4 squares.
   - Combine disparate card spans:
     - Feature Hero Card: `col-span-12 md:col-span-8 row-span-2` (Large interactive preview or chart).
     - Metric Stat Cards: `col-span-12 md:col-span-4` (Quick KPI counters, sparklines, or status tags).
     - Micro Utility Cards: `col-span-6 md:col-span-4` (Live avatars, quick toggles, or recent activity list).
2. **Card Internal Composition**:
   - Header: Small icon container + title + subtle action button.
   - Body: Graphic focus (interactive SVG, miniature chart, or illustrative widget).
   - Footer: Concise 1-line caption with contextual badge.

## 2. Responsive Reflow
- Mobile: Flattens gracefully to single-column vertical cards with consistent gap (`gap-4`).
- Desktop: Expands to rich 12-column grid layout with uniform padding (`p-6`).
