---
name: cross-tab-state-sync
description: Synchronizes browser application state, authentication tokens, and shopping carts across multiple open tabs in real time using BroadcastChannel and SharedWorker.
---

# Cross-Tab Browser State Synchronizer

This skill guides the design of multi-tab state coordination, synchronized session termination, and cross-tab event buses in web applications.

## 1. Native Web APIs & Channel Architecture

1. **BroadcastChannel API**:
   - Establish dedicated communication channels (e.g. `const authChannel = new BroadcastChannel('auth_sync');`).
   - Emit state change events: `LOGOUT`, `TOKEN_REFRESH`, `CART_UPDATE`, `THEME_CHANGE`.
   - Post-message listeners must immediately trigger local state updates (e.g. invalidating query caches) without full window reloads.
2. **Fallback Mechanisms**:
   - For environments lacking BroadcastChannel support, fall back to `window.addEventListener('storage', ...)` tracking `localStorage` key changes.
   - Guard against duplicate event processing by attaching monotonic event timestamps.

## 2. SharedWorker for Centralized Network I/O
- Leverage a `SharedWorker` when multiple open tabs need to share a single active WebSocket connection or polling loop, drastically reducing backend server load.
