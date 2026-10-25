---
name: clickhouse-analytics-engine
description: Designs high-performance analytical schemas, MergeTree engines, materialized views, and sub-millisecond aggregations on ClickHouse.
---

# ClickHouse Real-Time Analytics Engine

This skill directs schema modeling, table engine selection, and query optimization for high-volume time-series, event telemetry, and financial analytics on ClickHouse.

## 1. Schema & Engine Selection

1. **MergeTree Family**:
   - Use `ReplacingMergeTree` for deduplicating event logs by primary key.
   - Use `SummingMergeTree` or `AggregatingMergeTree` for pre-computed numerical counters and financial ledgers.
2. **Primary Key & Sorting Key Discipline**:
   - Primary key must strictly follow query filtering hierarchy (e.g. `ORDER BY (tenant_id, event_date, user_id)`).
   - Partition sparingly: partition by month (`toYYYYMM(event_date)`) rather than by day to avoid excessive data parts.

## 2. Ingestion & Materialized Views
- Batch write events in blocks of 10,000 to 100,000 rows rather than row-by-row single inserts.
- Create Materialized Views targeting `AggregatingMergeTree` tables for instant dashboard aggregations.
