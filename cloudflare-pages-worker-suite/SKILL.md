---
name: cloudflare-pages-worker-suite
description: Masters Cloudflare Pages Functions, edge workers, D1 SQL databases, KV caching, R2 asset storage, and zero-downtime Wrangler deployments.
---

# Cloudflare Pages & Workers Full-Stack Suite

This skill directs the development, debugging, and deployment of serverless applications running on Cloudflare Pages Functions and edge Workers.

## 1. Edge Architecture Patterns

1. **Pages Functions Routing (`functions/`)**:
   - Structure dynamic endpoints: `functions/api/orders/[id].js`.
   - Extract parameters via `context.params.id`.
   - Access bindings directly via `context.env` (`context.env.DB`, `context.env.KV`, `context.env.MY_SECRET`).
2. **CORS & Response Envelopes**:
   - Handle preflight `OPTIONS` requests uniformly across all edge endpoints:
     ```javascript
     export async function onRequestOptions() {
       return new Response(null, {
         status: 204,
         headers: {
           "Access-Control-Allow-Origin": "*",
           "Access-Control-Allow-Methods": "GET, POST, PUT, DELETE, OPTIONS",
           "Access-Control-Allow-Headers": "Content-Type, Authorization"
         }
       });
     }
     ```

## 2. D1 SQL & KV Caching Discipline
- Use parameterized queries with Cloudflare D1 (`env.DB.prepare('SELECT * FROM users WHERE id = ?').bind(userId).first()`).
- Leverage edge KV storage with `cacheTtl` for read-heavy public settings and product catalogs.
