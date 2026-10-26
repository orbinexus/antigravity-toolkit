---
name: circuit-breaker-resilience
description: Implements circuit breakers, fallback degradations, and bulkhead isolation to protect distributed systems from cascading upstream service failures.
---

# Circuit Breaker & Graceful Degradation Pattern

This skill guides the implementation of circuit breaker state machines (Closed, Open, Half-Open) and fallback degradation strategies for external network calls.

## 1. Circuit Breaker State Machine

```text
       ┌──────────┐
       │  CLOSED  │ (Normal: All requests pass through)
       └────┬─────┘
            │ Failure rate > 50% in 10s window
            ▼
       ┌──────────┐
       │   OPEN   │ (Tripped: Immediately fail-fast or return cached fallback)
       └────┬─────┘
            │ After 30s reset cooldown timer
            ▼
     ┌─────────────┐
     │  HALF-OPEN  │ (Probe: Permit 3 trial requests to upstream)
     └──────┬──────┘
            ├── Success: Reset to CLOSED
            └── Failure: Trip back to OPEN for 60s
```

## 2. Graceful Degradation & Fallbacks
- Provide graceful fallbacks:
  - Payment Gateway fails ➔ Queue payment attempt for automatic retry and display: *"Payment received, confirming with your bank..."*.
  - Recommendation Engine fails ➔ Fall back to static cached Top-10 popular items instead of crashing the product page.
- Bulkhead Isolation: Isolate connection pools and thread pools so a slow third-party service cannot exhaust server threads.
