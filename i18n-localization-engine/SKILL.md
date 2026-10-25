---
name: i18n-localization-engine
description: Implements end-to-end internationalization (i18n), Right-to-Left (RTL) layout adaptation for Urdu/Arabic, pluralization rules, and localized formatting.
---

# Internationalization (i18n) & RTL Localization Engine

This skill guides the implementation of multilingual support, bidirectional layouts (LTR/RTL), and locale-aware number/currency/date formatting.

## 1. Bidirectional UI Architecture (RTL for Urdu / Arabic)

1. **CSS Logical Properties**:
   - Replace physical directions (`margin-left`, `padding-right`, `left`, `right`) with CSS logical properties:
     - `margin-inline-start`, `margin-inline-end`
     - `padding-inline-start`, `padding-inline-end`
     - `inset-inline-start`, `inset-inline-end`
2. **Direction Toggling**:
   - Set `dir="rtl"` on the root `<html>` tag dynamically based on the active locale.
   - Flip directional icons (arrows, chevrons, navigation chevrons) while keeping media controls (play/pause) unaffected.

## 2. Dynamic Translation & Formatting Standards
- Externalize all hardcoded UI strings into translation catalogs (JSON/PO).
- Support ICU message format for pluralization and gender-specific grammar.
- Use `Intl.NumberFormat` and `Intl.DateTimeFormat` for automated locale-specific currency and calendar renderings.
