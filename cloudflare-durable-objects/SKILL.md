---
name: cloudflare-durable-objects
description: Architects stateful edge applications, collaborative rooms, and distributed coordination using Cloudflare Workers and Durable Objects.
---

# Cloudflare Durable Objects & Stateful Edge Architect

This skill guides the design of globally distributed, strongly consistent stateful edge actors using Cloudflare Workers and Durable Objects.

## 1. Actor Model & Concurrency

1. **Single-Point-of-Coordination**:
   - Each Durable Object instance represents a unique entity (e.g. chat room, document session, multiplayer lobby) with guaranteed single-threaded execution.
   - Use `env.MY_DO.idFromName(roomName)` for deterministic routing to the nearest edge instance.
2. **WebSocket Hibernation**:
   - Leverage `state.acceptWebSocket(ws)` to sleep memory when connections are idle, slashing edge compute billing.

## 2. Transactional Edge Storage
- Use `state.storage.get()` and `state.storage.put()` with atomic transactional guarantees.
- Synchronize memory state to disk using write-coalescing to avoid disk I/O bottlenecks.
