---
name: api-reverse-engineering
description: Inspects, intercepts, and reverse-engineers undocumented private web and mobile APIs from network traffic, HAR archives, or cURL requests into robust client SDKs, scripts, or automation tools.
---

# API Reverse Engineering & Private Endpoint Extraction

This skill guides the agent in decoding internal/private endpoints, authentication mechanisms, token rotation, signature algorithms, and request signing from raw network captures.

## 1. Input Analysis Workflow

When given a network trace, HAR export, or cURL snippet:
1. **Header Deconstruction**:
   - Identify session tokens, bearer authorization, cookie state, anti-CSRF headers, and vendor-specific headers (e.g., `X-Signature`, `X-Client-Hash`, `User-Agent`).
   - Distinguish required headers from non-essential tracking headers.
2. **Payload & Parameter Mapping**:
   - Inspect query parameters, JSON payload structures, multipart form-data, or protobuf/binary encodings.
   - Trace dynamic values (timestamps, nonces, device IDs, HMAC signatures).
3. **Response Structure Decoding**:
   - Map nested data structures, pagination cursors, rate-limit headers (`X-RateLimit-*`, `Retry-After`).

## 2. Token & Signature Reverse Engineering

If requests fail with `401 Unauthorized` or `403 Forbidden`:
- Check for dynamic signatures generated via JavaScript on the frontend.
- Look for timestamp-based HMAC generation or client-side secret obfuscation.
- Recreate the exact hashing logic in Python/Node.js.

## 3. Script Generation Standards

- Produce standalone Python (`httpx` or `requests`) or TypeScript (`fetch` / `axios`) scripts.
- Include session persistence (cookie jar), automatic token refresh handling, backoff retries, and rate limit throttling.
- Format extracted data into clean Pydantic models or TypeScript interfaces.
