---
name: redis-event-mesh-master
description: Builds microsecond-latency event-driven meshes, Streams consumer groups, and Redis Pub/Sub topologies for high-throughput distributed systems.
---

# Redis Event Mesh & Streams Architect

This skill directs the design of low-latency, distributed event streaming pipelines and consumer groups leveraging Redis Streams (`XADD`, `XREADGROUP`) and Pub/Sub.

## 1. Redis Streams & Consumer Groups

1. **Persistent Message Streams (`XADD`)**:
   - Append events to streams with capped length to prevent memory leaks (`XADD stream_name MAXLEN ~ 100000 * payload ...`).
2. **Consumer Group Partitioning**:
   - Scale horizontally across multiple worker instances reading from the same consumer group (`XREADGROUP GROUP my_group worker_1 STREAMS stream_name >`).
   - Acknowledge processed messages explicitly (`XACK`) to ensure at-least-once delivery.
3. **Pending Entries List (PEL) & Recovery**:
   - Query unacknowledged messages stalled due to worker crashes (`XPENDING`).
   - Claim orphan messages via `XCLAIM` or `XAUTOCLAIM` after a timeout window.

## 2. High-Throughput Pub/Sub Channels
- Use ephemeral Pub/Sub (`PUBLISH` / `SUBSCRIBE` / `PSUBSCRIBE`) for non-critical broadcast events (e.g. live presence indicators, cache invalidation notifications).
