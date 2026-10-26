---
name: jwt-revocation-denylist
description: Implements instant, sub-millisecond JWT token revocation using Redis Bloom filters and short-lived JTI denylists without database bottlenecks.
---

# Instant JWT Revocation & Denylist Architecture

This skill provides patterns for revoking stateless JWTs on user logout, password reset, or account compromise without sacrificing the speed of stateless tokens.

## 1. High-Performance Denylist Patterns

1. **JTI (JWT ID) Denylist with TTL**:
   - Issue each JWT with a unique `jti` claim (UUID v4).
   - Upon revocation, store the `jti` in Redis with an expiration time equal to the token's remaining lifetime:
     `SET jti:<jti_value> "revoked" EX <remaining_seconds>`
   - Memory footprint automatically cleans itself up when the original token expires.
2. **Redis Bloom Filters (Ultra-High Throughput)**:
   - For systems with millions of users, check token `jti` against a Bloom filter (`BF.EXISTS`). If false, the token is guaranteed not revoked (0 DB read cost).

## 2. Epoch / Password-Changed Timestamp Validation
- Include a `token_version` or `issued_at` (`iat`) claim.
- Reject any token where `iat < user.password_changed_at` without requiring per-token denylist checks.
