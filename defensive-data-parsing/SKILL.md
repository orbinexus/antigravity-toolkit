---
name: defensive-data-parsing
description: Enforces self-healing JSON parsing, mandatory safe fallbacks, nullable object access guards, and zero-crash schema decoders.
---

# Defensive Data Parsing & Self-Healing Schemas

This skill eliminates fatal runtime errors (`Cannot read property of undefined`, `slice is not a function`, `map is not a function`) across data ingestion boundaries.

## 1. Zero-Crash Data Access Standards

1. **Mandatory Safe Defaults**:
   - Arrays: Always default with `(data?.items || [])` before iterating (`.map()`, `.forEach()`, `.filter()`).
   - Strings: Always default with `String(val || '')` before calling string methods (`.slice()`, `.trim()`, `.toLowerCase()`).
   - Objects: Always destructure with fallbacks: `const { user = {}, settings = {} } = response || {};`
2. **Safe JSON Parsing**:
   - Never call bare `JSON.parse(str)`.
   - Wrap in self-healing helper:
     ```javascript
     function safeJsonParse(raw, fallback = {}) {
       try { return typeof raw === 'string' ? JSON.parse(raw) : (raw || fallback); }
       catch { return fallback; }
     }
     ```

## 2. Defensive Date Formatting
- Never perform direct `.slice(5, 16)` on unverified date inputs.
- Parse through a resilient date handler that validates `!isNaN(new Date(val).getTime())` before returning formatted strings, falling back to a clean placeholder (`"-"`).
