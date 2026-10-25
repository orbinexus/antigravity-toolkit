---
name: redis-cache-mastery
description: Implements high-throughput Redis caching architectures, cache-aside patterns, cache invalidation, and protection against cache stampedes and penetration.
---

# Redis Caching Mastery & Stampede Protection

This skill designs resilient, high-throughput caching layers in Redis/Valkey to protect backend databases from traffic surges and cache-related outages.

## 1. Resilient Caching Patterns

1. **Cache Stampede (Thundering Herd) Mitigation**:
   - **Mutex Locking**: When a cache miss occurs, acquire a temporary lock so only one thread/process computes and repopulates the value while other callers wait or receive stale data.
   - **Probabilistic Early Expiration (XFetch algorithm)**: As a key nears expiration, probabilistically recompute it in the background before it completely expires.
2. **Cache Penetration & Null Object Pattern**:
   - Cache non-existent database lookups with a short TTL (e.g. 60s) to prevent attackers from querying random IDs to exhaust database connections.
   - Use Bloom Filters for massive datasets to instantly reject keys that definitely do not exist.

## 2. Invalidation & Data Structures
- Prefer Cache-Aside (Lazy Loading) for reads and Write-Through / Invalidate-On-Write for mutations.
- Leverage Redis Hashes (`HSET`/`HGETALL`), Sorted Sets (`ZADD`/`ZRANGEBYSCORE`) for leaderboards and range queries rather than serializing giant JSON blobs into raw strings.
