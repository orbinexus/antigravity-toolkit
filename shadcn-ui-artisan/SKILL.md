---
name: shadcn-ui-artisan
description: Masters Shadcn UI and Radix primitives component composition, semantic token usage, accessible keyboard states, and clean design system architecture.
---

# Shadcn UI & Modern Component System Artisan

This skill directs the structuring, customization, and composition of modern component design systems built on Shadcn UI, Radix Primitives, and Tailwind CSS.

## 1. Component Philosophy & Composition

1. **Copy-and-Own Model**:
   - Favor composed headless primitives (Radix UI) styled with Tailwind over bloated monolithic CSS frameworks.
2. **Semantic Token Mapping**:
   - Strictly leverage CSS variable tokens:
     - `bg-background`, `text-foreground`
     - `bg-card`, `text-card-foreground`
     - `bg-primary`, `text-primary-foreground`
     - `bg-muted`, `text-muted-foreground`
     - `border-border`, `ring-ring`
   - Guarantees seamless light/dark mode switching without hardcoded hex codes.

## 2. Interactive Primitives Standards
- **Command Palette (`Cmd+K`)**: Use `cmdk` for instant, keyboard-driven navigation across tools and settings.
- **Dropdowns & Popovers**: Smooth exit/enter transitions with `animate-in fade-in-0 zoom-in-95 data-[state=closed]:animate-out data-[state=closed]:fade-out-0 data-[state=closed]:zoom-out-95`.
- **Badges & Status**: Subtle pill tags with dot indicators (`inline-flex items-center gap-1.5 px-2.5 py-0.5 rounded-full text-xs font-medium bg-emerald-500/10 text-emerald-400 border border-emerald-500/20`).
