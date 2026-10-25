---
name: graphql-schema-architect
description: Designs scalable GraphQL schemas, resolvers, and Federation architectures while solving N+1 query bottlenecks using DataLoader batching.
---

# GraphQL Schema & DataLoader Architect

This skill guides the design of ergonomic, high-throughput GraphQL schemas, strongly typed resolvers, and query performance optimizations.

## 1. Schema Design Principles

1. **Consumer-Centric SDL**:
   - Design schemas based on client UI access patterns rather than mirroring raw database table columns.
   - Use strict custom scalars (`DateTime`, `EmailAddress`, `JSON`) and non-nullable bang operators (`!`) where null values are invalid.
2. **Cursor-Based Pagination**:
   - Implement Relay-style cursor connections (`edges`, `node`, `pageInfo: { hasNextPage, endCursor }`) for infinite scrolling lists.

## 2. N+1 Problem Prevention & Batching

- Strictly enforce `DataLoader` patterns in resolver contexts:
  - Batch individual database queries into a single SQL `WHERE id IN (...)` lookup per tick of the event loop.
  - Implement per-request caching to eliminate duplicate reads within a single GraphQL query resolution.
- Set query depth limits and query complexity analysis to protect the server from abusive nested queries.
