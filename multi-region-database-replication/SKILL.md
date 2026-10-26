---
name: multi-region-database-replication
description: Architects active-active multi-region database architectures, replication conflict resolution (CRDTs), and cross-continent read replica topologies.
---

# Multi-Region Database Replication Architect

This skill guides the design of globally distributed, multi-region database topologies, replication conflict mitigation, and disaster-recovery topologies.

## 1. Topologies & Replication Modes

1. **Active-Passive (Read Replicas Worldwide)**:
   - Single primary region for writes; read replicas stationed across continents (US, EU, Asia).
   - Route reads to the nearest geographical replica; route writes over dedicated cloud interconnects to primary.
2. **Active-Active (Multi-Primary)**:
   - Segment writes by customer geography or tenant partition to eliminate cross-region conflict.
   - For shared counters and collaborative states, implement Conflict-Free Replicated Data Types (CRDTs) or Last-Write-Wins (LWW) with synchronized NTP/TrueTime clocks.

## 2. Replication Lag & Read-Your-Own-Writes
- Mitigate replication lag anomalies: after a mutation, pin that specific client session to the primary database for a brief grace window (e.g. 5 seconds) before falling back to read replicas.
