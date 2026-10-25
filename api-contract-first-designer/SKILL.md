---
name: api-contract-first-designer
description: Designs contract-first API schemas, JSON schemas, OpenAPI specifications, and mock data contracts to decouple frontend and backend development.
---

# API Contract-First Designer

This skill enforces strict contract-first API design, establishing immutable request/response schemas before writing server or client implementations.

## 1. Contract Design Methodology

1. **RESTful & Pragmatic Resource Naming**:
   - Use plural nouns for resource paths (`/api/v1/orders`, `/api/v1/users/{id}/invoices`).
   - Use HTTP verbs semantically: `GET` (idempotent read), `POST` (create), `PUT` (full replace), `PATCH` (partial update), `DELETE` (remove).
2. **Standardized Response Envelope**:
   - Success envelope: `{ "data": T, "meta": { "page": 1, "total": 100 } }`
   - Error envelope: `{ "error": { "code": "VALIDATION_FAILED", "message": "...", "details": [...] } }`
3. **HTTP Status Code Discipline**:
   - Use correct status codes: `200 OK`, `201 Created`, `204 No Content`, `400 Bad Request`, `401 Unauthorized`, `403 Forbidden`, `404 Not Found`, `409 Conflict`, `422 Unprocessable Entity`.

## 2. Decoupled Mock Servers
- Author standalone contract specs (OpenAPI 3.1 YAML / JSON) that compile directly into live mock servers via MSW or Prism.
