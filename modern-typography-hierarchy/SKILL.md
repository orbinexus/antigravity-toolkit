---
name: modern-typography-hierarchy
description: Establishes high-end typographical hierarchy, variable font pairings (Geist, Inter, Outfit), optical kerning, letter-spacing tracking, and multi-tier text contrast.
---

# Modern Typographical Hierarchy & Premium Styling

This skill directs typographic scale, contrast ratios, and layout rhythm to make text interfaces look editorial, clean, and expensive.

## 1. Font Selection & Variable Pairings

1. **Modern Font Families**:
   - Primary Sans: `Geist Sans`, `Inter Variable`, or `Plus Jakarta Sans`.
   - Code/Monospace: `Geist Mono` or `JetBrains Mono`.
   - Editorial Serif accents (where appropriate): `Instrument Serif` or `Newsreader`.
2. **Optical Kerning & Tight Tracking**:
   - Large Headings (24px+): Always apply `tracking-tight` (`-0.02em` to `-0.03em`) and `leading-[1.15]` to eliminate clumsy loose spacing.
   - Tiny Labels (10px - 12px): Always apply `uppercase tracking-widest font-semibold` for crisp, structured caption badges.

## 2. Multi-Tier Text Contrast
- Avoid monochromatic text walls. Always establish 3 distinct visual tiers:
  - **Primary**: `text-zinc-100` (White/high-contrast, for titles and critical values).
  - **Secondary**: `text-zinc-400` (Balanced gray, for body descriptions).
  - **Muted/Tertiary**: `text-zinc-500` or `text-zinc-600` (Subtle gray, for timestamps, metadata, and breadcrumbs).
