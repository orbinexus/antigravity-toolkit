---
name: websocket-realtime-engine
description: Builds real-time WebSocket and SSE architectures, multiplexed rooms, pub-sub backbones, connection resilience, and live presence/cursor synchronization.
---

# Real-Time WebSockets & Live Presence Engine

This skill directs the development of low-latency, bidirectional real-time communication systems, interactive multiplayer state sync, and connection-resilient chat architectures.

## 1. Connection Lifecycle & Resilience

1. **Heartbeat & Zombie Pruning**:
   - Implement client/server ping-pong intervals (e.g. 30s ping, 10s pong timeout) to terminate dead TCP connections cleanly.
2. **Exponential Reconnection with Jitter**:
   - Client reconnection loops must implement backoff with randomized jitter to prevent thundering herd spikes when the server restarts.
3. **Message Ordering & Idempotency**:
   - Attach monotonic sequence IDs or UUIDs to messages.
   - Queue client mutations during brief disconnections and replay them upon socket restoration.

## 2. Pub-Sub & Room Multiplexing
- Decouple multi-node WebSocket clusters using a Redis / Valkey pub-sub adapter.
- Implement channel/room authorization tokens during the initial upgrade handshake (`onUpgrade`).
