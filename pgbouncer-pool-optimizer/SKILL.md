---
name: pgbouncer-pool-optimizer
description: Configures, tunes, and optimizes PgBouncer connection pooling for PostgreSQL, maximizing throughput and preventing connection exhaustion under heavy concurrent spikes.
---

# PgBouncer Connection Pool Optimizer

This skill provides production configuration templates, pooling mode selections, and capacity tuning rules for PgBouncer in front of high-traffic PostgreSQL instances.

## 1. Pooling Modes & Architectural Constraints

1. **Transaction Pooling (`pool_mode = transaction`) [Recommended]**:
   - Assigns a server connection only for the duration of a transaction block (`BEGIN` ... `COMMIT`).
   - Maximizes throughput for web apps and microservices.
   - Guard against features incompatible with transaction pooling: session-level prepared statements, `LISTEN`/`NOTIFY`, and temporary tables.
2. **Session Pooling (`pool_mode = session`)**:
   - Holds connection for the lifetime of the client session. Use strictly when session state or legacy prepared statements are mandatory.

## 2. Capacity Sizing & Config Formulas
- **Database Server Pool**:
  `default_pool_size = (Total Available Postgres Max Connections - Reserved Superuser) / Number of Databases`
- Set `max_client_conn` high (e.g. 5,000 - 10,000) while keeping PostgreSQL `max_connections` modest (100 - 300) to prevent CPU context switching degradation.
- Configure `reserve_pool_size` and `reserve_pool_timeout` to absorb emergency traffic bursts.
