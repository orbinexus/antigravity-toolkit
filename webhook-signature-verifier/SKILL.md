---
name: webhook-signature-verifier
description: Validates and cryptographically verifies incoming webhook signatures (Stripe, GitHub, Shopify, PayPal) preventing spoofing and replay attacks.
---

# Inbound Webhook Cryptographic Verifier

This skill enforces cryptographic signature validation and replay-attack mitigation for inbound webhooks from payment gateways and SaaS platforms.

## 1. Signature Verification Protocol

1. **Raw Body Integrity**:
   - Always verify signatures against the raw, unmodified byte buffer of the HTTP request body *before* parsing JSON.
   - Parsing JSON changes whitespace and key order, invalidating HMAC hashes.
2. **Timestamp Replay Guard**:
   - Extract the timestamp header (e.g. Stripe `t=...`, GitHub timestamp).
   - Reject any webhook where `abs(currentTime - webhookTimestamp) > 300` (5 minutes) to defeat replay attacks.
3. **Timing-Safe Comparison**:
   - Strictly use constant-time comparisons (`crypto.timingSafeEqual` in Node.js, `hmac.compare_digest` in Python) to prevent side-channel timing attacks.

## 2. Idempotency & Processing Sinks
- Store processed webhook event IDs in Redis or database with a 24-hour TTL to ignore duplicate deliveries.
- Return HTTP `200 OK` immediately after queuing the payload to an asynchronous worker.
