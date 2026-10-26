---
name: local-first-crdt-architect
description: Architects local-first, zero-latency applications using IndexedDB, Conflict-Free Replicated Data Types (CRDTs), and background peer synchronization.
---

# Local-First & CRDT Architecture (Linear / Notion Style)

This skill directs the development of zero-latency, offline-first applications where all user writes resolve immediately in local memory/IndexedDB before syncing to the cloud.

## 1. Local-First Tenets

1. **Zero-Latency Mutation**:
   - Write operations execute synchronously against local storage (RxDB, ElectricSQL, or Yjs/Automerge); never display blocking spinners for standard user inputs.
2. **Conflict-Free Replicated Data Types (CRDTs)**:
   - Use state-based or operation-based CRDTs (Yjs / Automerge) for collaborative text, arrays, and maps to merge concurrent edits deterministically without server-side locking.
3. **Optimistic Offline Sync Engine**:
   - Queue mutations in a persistent local append-only log.
   - Sync bidirectional state with WebSocket relays upon network reconnection using vector clocks.

## 2. Storage Quota & Compaction
- Periodically compact local CRDT change histories into state snapshots to keep IndexedDB storage usage under 50MB.
