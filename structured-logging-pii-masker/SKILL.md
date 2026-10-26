---
name: structured-logging-pii-masker
description: Formats standardized JSON structured logs with automated PII masking (passwords, credit cards, emails, tokens) and high-throughput log aggregation readiness.
---

# Structured JSON Logging & PII Masking Engine

This skill guides the implementation of production-grade JSON logging, context correlation, and automatic redaction of Personally Identifiable Information (PII).

## 1. Automated PII Redaction & Masking

1. **Sensitive Key Detection & Masking**:
   - Recursively traverse log payloads and mask values for keys matching sensitive patterns:
     `password`, `token`, `secret`, `authorization`, `credit_card`, `cvv`, `ssn`, `api_key`.
   - Replace sensitive strings with `[REDACTED]` or partial masks (e.g. credit card `**** **** **** 1234`).
2. **Regex Pattern Scanners**:
   - Scan unstructured log strings for email addresses, JWT signatures (`ey...`), and 16-digit credit card numbers before emission.

## 2. Standardized JSON Schema
- Emit logs matching structured format:
  `{ "timestamp": "...", "level": "INFO|WARN|ERROR", "trace_id": "...", "service": "...", "message": "...", "context": { ... } }`
- Deliver asynchronous log streaming sinks to avoid blocking the main event loop during high-throughput I/O.
