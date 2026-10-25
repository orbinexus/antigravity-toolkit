---
name: turso-libsql-edge-db
description: Architect, configure, and query globally distributed, low-latency SQLite databases at the edge using Turso and LibSQL with embedded replicas.
---

# Turso & LibSQL Distributed Edge Database Architect

This skill guides the design, replication strategies, and query workflows for distributed SQLite databases running on Turso and LibSQL.

## 1. Edge Replication & Embedded Replicas

1. **Embedded Replicas**:
   - Store local SQLite files inside the edge container / server process for zero-latency local reads (microsecond response times).
   - Sync writes automatically to the primary Turso database in the background.
2. **Schema Modeling with Drizzle ORM / Prisma**:
   - Design strict SQLite schemas leveraging native types, foreign key cascades, and composite indexes.
   - Run declarative migrations seamlessly across primary and edge replicas.

## 2. Serverless & Multi-Tenant Database Architecture
- Multi-database tenancy: Provision separate lightweight SQLite databases per organization (`turso db create ...`) for complete tenant isolation at scale.
- Configure auth tokens with granular database permissions (read-only vs read-write).
