---
name: a11y-debugging
description: Audits web accessibility (WCAG 2.1), ARIA roles, color contrast ratios, screen reader compatibility, and keyboard navigation flows.
---

# Web Accessibility (a11y) & WCAG Auditing

This skill guides accessibility testing, WCAG 2.1 AA/AAA compliance auditing, and keyboard/screen reader navigation debugging.

## 1. Automated & Manual a11y Checklist

1. **Semantic HTML & ARIA Landmarks**:
   - Prefer native semantic tags (`<nav>`, `<main>`, `<article>`, `<button>`) over `<div role="...">`.
   - Ensure dynamic state changes announce correctly via `aria-live="polite"` or `aria-atomic="true"`.
2. **Keyboard Navigation & Focus Traps**:
   - Every interactive element must be focusable via `Tab` key with a visible outline (`:focus-visible`).
   - Modal dialogs must trap focus inside the modal and restore focus to trigger element upon closing with `Escape`.
3. **Color Contrast & Readability**:
   - Normal text: Minimum 4.5:1 contrast ratio against background.
   - Large text (18pt+ or 14pt bold): Minimum 3:1 contrast ratio.
