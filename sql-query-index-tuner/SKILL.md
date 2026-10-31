---
name: sql-query-index-tuner
description: Analyzes PostgreSQL and MySQL EXPLAIN ANALYZE execution plans, eliminates sequential scans, and architects optimal B-Tree, GIN, and BRIN composite indexes.
---

# SQL Query Execution Plan & Index Tuner

This skill guides deep database query profiling, cost estimation, and composite index design to eliminate slow table scans and high disk I/O.

## 1. Execution Plan Forensic Protocol (`EXPLAIN ANALYZE`)

1. **Critical Warning Metrics**:
   - `Seq Scan` on tables with > 50,000 rows.
   - High `Buffers: shared read` (disk I/O) vs `shared hit` (RAM buffer cache).
   - Massive disparity between estimated rows (`rows=...`) and actual rows (`actual rows=...`) indicating stale table statistics (run `ANALYZE <table>`).
2. **Index Type Selection**:
   - **B-Tree**: High-cardinality equality and range searches (`=`, `<`, `>`, `BETWEEN`).
   - **Composite B-Tree**: Strict leftmost-prefix order (`INDEX (tenant_id, status, created_at)`). Place equality filters first, range filters last.
   - **GIN**: JSONB nested attributes (`payload @> '{"status": "active"}'`), full-text search vectors (`tsvector`), and array lookups (`?|`).
   - **BRIN (Block Range Index)**: Append-only time-series tables physically sorted on disk by date/timestamp (takes 99% less RAM than B-Tree).
   - **Partial Indexes**: Index only active subsets (`WHERE deleted_at IS NULL AND status = 'pending'`).

## 2. Zero-Downtime Index Creation
- Always run `CREATE INDEX CONCURRENTLY` in PostgreSQL to avoid exclusive table read/write locks.
