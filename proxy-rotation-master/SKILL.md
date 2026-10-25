---
name: proxy-rotation-master
description: Manages high-throughput proxy rotation, IP health scoring, session sticky proxies, and automatic failover pools for distributed web scraping.
---

# Proxy Rotation & IP Pool Orchestration

This skill guides the design and integration of resilient proxy routing layers, sticky IP pools, and anti-ban network strategies for high-volume data harvesting.

## 1. Proxy Pool Architecture

1. **Proxy Classification & Selection**:
   - Datacenter proxies for low-latency, high-volume public endpoints.
   - Residential / Mobile proxies for bot-protected and geo-restricted domains.
2. **Session Stickiness vs Pure Rotation**:
   - Maintain IP stickiness across multi-step session lifecycles (e.g. login -> search -> checkout) using session tags (`proxy.vendor.com:port:user:session-12345`).
   - Rotate IP on every discrete stateless GET request.

## 2. Health Monitoring & Automatic Failover
- Score proxies based on response latency, HTTP status codes (`403 Forbidden`, `429 Too Many Requests`), and connection timeouts.
- Automatically quarantine unhealthy proxies for a cooldown window (e.g. 15 minutes) before re-evaluating.
