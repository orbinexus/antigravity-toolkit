---
name: pos-offline-first-sqlite
description: Architects resilient offline-first POS systems using embedded SQLite, optimistic local transactions, and background cloud synchronization.
---

# 100% Offline-First POS Engine

This skill guides the construction of indestructible POS terminals that continue ringing sales and printing receipts during extended internet blackouts.

## 1. Local Persistence & Synchronization

1. **Local SQLite Primary**:
   - Write all order transactions and receipts to local SQLite database first.
   - Attach a monotonic local counter and UUID v7 (timestamp-ordered) to every transaction.
2. **Idempotent Cloud Ingestion**:
   - Queue completed orders in a local outbox table.
   - When network connectivity is restored, push batches with deduplication tokens to prevent double-charging or duplicate sales records.
