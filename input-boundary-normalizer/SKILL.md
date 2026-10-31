---
name: input-boundary-normalizer
description: Sanitizes, coerces, and normalizes incoming API payload values (numbers, strings, dates, booleans) at route entry to prevent NaN and undefined pollution.
---

# API Input Boundary Normalizer & Coercion Engine

This skill ensures incoming request parameters, query filters, and form values are coerced into valid primitive types before reaching calculation logic or database queries.

## 1. Coercive Normalization at the Gateway

1. **Numeric Coercion (Eliminate `NaN`)**:
   - Query strings arrive as strings (`"42"`). Convert with guarded parse:
     `const page = Math.max(1, parseInt(req.query.page, 10) || 1);`
     `const amount = Number.isFinite(Number(req.body.amount)) ? Number(req.body.amount) : 0;`
2. **Boolean Normalization**:
   - Accurately parse truthy/falsy query parameters:
     `const isLive = String(req.query.live).toLowerCase() === 'true' || req.query.live === '1';`
3. **Phone & Identifier Normalization**:
   - Strip whitespace, dashes, and invalid symbols from phone numbers (`val.replace(/[^0-9+]/g, '')`).
   - Validate UUID and slug formats before embedding into database statements.

## 2. Fail-Fast Early Return
- If mandatory primary fields cannot be normalized into valid types, reject immediately with HTTP `422 Unprocessable Entity` describing the exact field anomaly.
