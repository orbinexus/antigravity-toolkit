---
name: api-gateway-kong-envoy
description: Configures cloud-native API Gateways (Kong, Envoy) for edge authentication, centralized rate limiting, TLS termination, and service routing.
---

# API Gateway & Edge Architecture (Kong & Envoy)

This skill directs the setup, plugin configuration, and request routing for modern API Gateways deployed in front of distributed microservice architectures.

## 1. Edge Authentication & Request Routing

1. **Centralized JWT & Key Verification**:
   - Verify JWT signatures and claims at the gateway boundary; strip client tokens and inject trusted internal identity headers (`X-User-Id`, `X-User-Roles`) to upstream services.
2. **Path & Host Routing Rules**:
   - Route incoming traffic by domain hostnames and URI prefixes (`/api/v1/billing/*` -> Billing Service cluster).
   - Enforce global CORS policies uniformly at the edge.

## 2. Distributed Rate Limiting & Circuit Breaking
- Implement Redis-backed rate limiting plugins across multi-node gateway clusters.
- Configure Envoy outlier detection and circuit breaking (e.g. ejecting unhealthy upstream instances after 3 consecutive 5xx errors).
