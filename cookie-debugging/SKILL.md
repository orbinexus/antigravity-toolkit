---
name: cookie-debugging
description: Diagnoses cookie expiration, SameSite attribute policies, cross-origin auth failures, partition state (CHIPS), and secure flag misconfigurations.
---

# Cookie & Session Storage Debugger

This skill diagnoses cross-site authentication drops, Third-Party Cookie Deprecation issues, and session persistence flaws.

## 1. Cookie Policy & Flags Audit

1. **Security Flags**:
   - `HttpOnly`: Mandatory on session IDs and auth tokens to prevent XSS theft.
   - `Secure`: Mandatory on all production cookies to ensure transmission over HTTPS only.
2. **SameSite Behavior**:
   - `SameSite=Strict`: Protects sensitive actions against CSRF; cookies not sent on cross-site link clicks.
   - `SameSite=Lax`: Default modern behavior; permits top-level cross-site navigations (e.g. following links).
   - `SameSite=None; Secure`: Required for embedded iframes and cross-origin APIs.
3. **Partitioned Cookies (CHIPS)**:
   - For third-party embeds, ensure the `Partitioned` attribute is present to survive modern cookie partitioning.
