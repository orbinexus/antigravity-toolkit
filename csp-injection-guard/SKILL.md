---
name: csp-injection-guard
description: Generates strict Content-Security-Policy (CSP) headers, dynamic cryptographic nonces, and Subresource Integrity (SRI) hashes to eliminate XSS and script injection.
---

# Strict CSP & Nonce-Based Injection Guard

This skill directs the design and enforcement of strict Content-Security-Policy (CSP Level 3) architectures and Subresource Integrity (SRI) pipelines to eliminate XSS.

## 1. Strict Nonce-Based Policy Architecture

1. **Per-Request Dynamic Nonce**:
   - Generate a cryptographically secure random 128-bit base64 nonce per HTTP response (`crypto.randomBytes(16).toString('base64')`).
   - Inject the nonce into response headers and inline script tags: `<script nonce="...">`.
2. **Standard CSP Directives**:
   - `script-src 'strict-dynamic' 'nonce-{NONCE}' 'unsafe-inline' http: https:;`
   - `object-src 'none';`
   - `base-uri 'none';`
   - `frame-ancestors 'none';`

## 2. Subresource Integrity (SRI) Generation
- Compute SHA-384 or SHA-512 hashes for all external CDN assets during build time:
  `<script src="..." integrity="sha384-..." crossorigin="anonymous"></script>`
- Automatically fail asset loading if external CDN scripts are tampered with or poisoned.
