---
name: openapi-sdk-generator
description: Generates typed, production-ready TypeScript or Python client SDKs from OpenAPI/Swagger specifications with token handling, retry policies, and autocompletion.
---

# OpenAPI & Swagger Client SDK Generator

This skill converts raw OpenAPI 3.x or Swagger 2.0 specifications (JSON/YAML) into fully typed, ergonomic, and production-tested API client libraries.

## 1. SDK Generation Protocol

1. **Schema & Model Synthesis**:
   - Generate strict TypeScript interfaces or Python Pydantic v2 models representing all request payloads, path parameters, query filters, and response bodies.
   - Enforce enum types and nullable/optional properties matching the specification.
2. **Client Ergonomics**:
   - Organize endpoints logically into resource namespaces (e.g. `client.users.getById()`, `client.billing.invoices.list()`).
   - Integrate built-in authentication injection (Bearer tokens, API keys, basic auth).
3. **Resilience & Production Hardening**:
   - Provide automatic exponential backoff for transient HTTP errors (`429 Too Many Requests`, `502`, `503`, `504`).
   - Handle token expiration and automatic refresh token rotation flows seamlessly.
