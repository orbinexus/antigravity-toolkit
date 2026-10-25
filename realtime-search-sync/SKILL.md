---
name: realtime-search-sync
description: Synchronizes relational databases with full-text search engines (Elasticsearch, Meilisearch, Typesense) using Change Data Capture (CDC) and batch indexers.
---

# Real-Time Search Engine Synchronization

This skill guides the design and implementation of real-time search engine sync pipelines between primary transactional databases and dedicated full-text search clusters.

## 1. Synchronization Architecture

1. **Change Data Capture (CDC) / Event Sinks**:
   - Stream row modifications (`INSERT`, `UPDATE`, `DELETE`) via transactional outbox patterns, database triggers, or WAL streams (Debezium / Logical Replication).
   - Maintain index atomicity: handle schema field transformations before indexing.
2. **Typo-Tolerant Search Tuning**:
   - Configure index settings with custom analyzers, n-gram tokenizers, and phonetic filters.
   - Configure ranking rules (exact match > typo tolerance > attribute weight > sort criteria).

## 2. Reindexing & Zero-Downtime Swaps
- Implement zero-downtime index swaps using search aliases (`search_alias -> search_v2` after full backfill).
- Guard against split-brain index states during network partitions.
