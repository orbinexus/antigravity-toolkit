---
name: nextjs-app-router-architect
description: Architects modern Next.js applications using Server Components, Server Actions, streaming suspense, parallel routes, and route handlers.
---

# Next.js Full-Stack App Router Architect

This skill directs the optimal architectural patterns, data-fetching strategies, and directory layouts for modern Next.js applications.

## 1. Server vs Client Component Discipline

1. **Server Components by Default**:
   - Fetch data directly inside async Server Components (direct DB queries or cached `fetch()`).
   - Zero JavaScript bundle shipped to the client for purely presentational and static sections.
2. **Client Components at the Leaves**:
   - Push `'use client'` to the outermost leaf nodes requiring browser events (`onClick`, `onChange`, `useEffect`, `useState`).
   - Pass Server Components as `children` into Client Component wrappers to maintain server rendering performance.

## 2. Server Actions & Mutations
- Co-locate Server Actions with domain features (`'use server'`).
- Validate action inputs with Zod schemas.
- Trigger cache revalidation on demand via `revalidatePath()` or `revalidateTag()`.
- Use `useOptimistic` and `useTransition` for instantaneous, zero-latency UI updates while network mutations resolve.
