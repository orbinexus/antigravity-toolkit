---
name: product-gamification-engine
description: Designs habit-forming product mechanics, daily streak engines, progress milestones, unlockable badges, and micro-celebrations to maximize user retention.
---

# Product Gamification & Retention Engine

This skill guides the design of psychological hook loops, streak mechanisms, unlockable tiers, and dynamic reward celebrations in web and mobile applications.

## 1. Core Retention Loops

1. **Daily Streak Engine**:
   - Track `current_streak`, `longest_streak`, and `last_activity_date` with timezone-aware grace periods (e.g. 36-hour freeze window) to avoid punishing users across timezones.
   - Implement streak recovery / freeze tokens to prevent demotivation upon accidental misses.
2. **Variable Reward Milestones**:
   - Progressive XP / levels with decaying acceleration (early levels feel rapid; later levels feel prestigious).
   - Achievement badges tied to meaningful milestones (e.g. "First 10 Orders", "Power User 30 Days").

## 2. Micro-Interactions & Celebrations
- Trigger contextual canvas confetti explosions (`canvas-confetti`) upon milestone completion.
- Provide dynamic SVG progress circles and animated numeric counter rollups (`0 -> 100%`).
