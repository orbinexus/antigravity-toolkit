---
name: zero-downtime-db-migrator
description: Designs zero-downtime database migrations, backward-compatible schema evolutions, online table rewrites, and instant rollback strategies using expand-and-contract patterns.
---

# Zero-Downtime Database Migration Specialist

This skill directs schema migrations across production relational databases (PostgreSQL, MySQL) without locking active tables, dropping user connections, or taking the service offline.

## 1. Safe Schema Evolution (Expand and Contract Pattern)

1. **Phase 1: Expand (Additive Changes Only)**:
   - Always add new columns as nullable or with a default value that doesn't trigger table rewrites (e.g. Postgres 11+ instant defaults).
   - Never rename or drop existing active columns directly.
2. **Phase 2: Dual Writing**:
   - Update application code or database triggers to write simultaneously to both the old and new columns.
   - Run background backfill scripts in batches (e.g. 1,000 rows at a time) to populate legacy data without long-running transaction locks.
3. **Phase 3: Dual Reading -> Switch**:
   - Switch application reads to the new column once backfill verification is 100% complete.
4. **Phase 4: Contract**:
   - Safely deprecate and drop the old unused column in a subsequent deployment after confirming no legacy clients rely on it.

## 2. Index & Constraint Operations
- Always create indexes concurrently (`CREATE INDEX CONCURRENTLY` in Postgres) to avoid exclusive table locks.
- Add constraints as `NOT VALID` first, then validate separately in a lightweight pass.
