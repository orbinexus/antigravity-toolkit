---
name: feature-flag-manager
description: Implements dynamic feature flags, percentage rollouts, kill-switches, and A/B testing configurations without redeploying code.
---

# Dynamic Feature Flags & Remote Configuration Manager

This skill guides the implementation of low-overhead feature flag evaluation engines, progressive rollout rings, and emergency kill-switches.

## 1. Flag Architecture & Evaluation

1. **In-Memory Caching with Background Sync**:
   - Cache flag states in application memory (process-local or Redis) to evaluate flags in sub-millisecond time.
   - Synchronize flag rule updates via WebSockets or polling without blocking runtime request paths.
2. **Deterministic Percentage Rollouts**:
   - Hash the target user identifier (e.g. `userId` or `deviceId`) combined with the feature key:
     `hash(userId + featureKey) % 100 < rolloutPercentage`
   - Guarantees deterministic bucket assignment: a user in the 10% bucket stays in the bucket across sessions.

## 2. Emergency Kill-Switches & Flag Hygiene
- Implement instant override kill-switches (`force_off: true`) that take precedence over all target rules.
- Maintain flag lifecycle tracking: mark flags as temporary (to be cleaned up within 30 days) or permanent operational toggles.
