---
name: postgres-deadlock-hunter
description: Diagnoses, mitigates, and resolves PostgreSQL row locking contention, long-running transaction blocks, and deadlocks in high-concurrency systems.
---

# PostgreSQL Deadlock & Row Lock Hunter

This skill diagnoses and eliminates database deadlocks, lock contention cascades, and blocking queries in high-concurrency PostgreSQL environments.

## 1. Lock Diagnosis & Active Contention Analysis

1. **Identifying Blocking Trees**:
   - Query `pg_stat_activity` and `pg_locks` to map the exact dependency chain of blocked PIDs vs blocking PIDs.
2. **Lock Types**:
   - Distinguish RowExclusiveLock, AccessExclusiveLock (DDL), and ShareLock.
   - Detect unindexed foreign keys causing table-wide share locks during parent deletions.

## 2. Deadlock Mitigation Patterns
- **Deterministic Acquisition Order**: Enforce strict sorting of primary keys (`ORDER BY id ASC`) before executing multi-row `UPDATE` or `SELECT FOR UPDATE` statements.
- **Skip Locked Pattern**: Use `SELECT ... FOR UPDATE SKIP LOCKED` for task queues and concurrent order processing to completely eliminate lock waiting.
- Set aggressive `lock_timeout` (e.g. `set lock_timeout = '2s';`) on migration scripts to avoid blocking application traffic.
