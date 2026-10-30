---
name: mobile-first-thumb-ux
description: Architects ergonomic mobile-first web and app interfaces featuring bottom sheets, thumb-friendly navigation docks, fluid gesture sheets, and native feel.
---

# Mobile-First Ergonomic & Thumb Zone UX

This skill directs the structuring of mobile web and progressive web apps optimized for one-handed thumb interaction and fluid mobile gesture ergonomics.

## 1. Natural Thumb Zone Mapping

1. **Bottom-Aligned Control Anchor**:
   - Place primary actions (checkout, submit, filter trigger, search) within the lower third of the mobile screen (`bottom-4 left-4 right-4` or floating action dock).
   - Reserve top navigation strictly for title and non-critical profile avatars.
2. **Bottom Sheets over Center Modals**:
   - On mobile viewports (`< 768px`), never pop up intrusive center modals.
   - Use swipeable, spring-animated Bottom Sheets (`vaul` style) that open from the bottom with a drag handle bar.

## 2. Touch Target Standards & Safe Areas
- Minimum tap target: `48px x 48px` with adequate margin to prevent fat-finger misclicks.
- Safe Area Insets: Strictly respect `pb-[env(safe-area-inset-bottom)]` on iPhones to prevent navigation bars from clipping beneath the iOS home indicator bar.
