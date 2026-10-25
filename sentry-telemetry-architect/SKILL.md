---
name: sentry-telemetry-architect
description: Configures production error tracking, performance tracing, user breadcrumb contexts, and alert noise filtering with Sentry and OpenTelemetry.
---

# Production Error Monitoring & Sentry Telemetry Architect

This skill directs the setup, tuning, and forensic triage of application exceptions, unhandled rejections, and performance bottlenecks across client and server environments.

## 1. SDK Configuration & Noise Reduction

1. **Intelligent Exception Filtering**:
   - Filter out benign browser errors (network dropouts, canceled requests, extension script injections, `ResizeObserver loop limit exceeded`).
   - Configure `beforeSend` hooks to scrub sensitive data (passwords, credit cards, auth tokens, PII) before telemetry payloads leave the server.
2. **Context Enrichment & Breadcrumbs**:
   - Attach user IDs, organization IDs, and subscription tiers to error events.
   - Capture custom breadcrumbs for significant user actions (e.g. clicked checkout, loaded cart) to reconstruct user journeys preceding exceptions.

## 2. Release & Source Map Management
- Automate source map uploading during CI/CD builds so production minified stack traces map directly to original TypeScript/source lines.
- Track regressions tied to specific git commit SHAs and release versions.
