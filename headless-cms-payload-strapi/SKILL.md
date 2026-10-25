---
name: headless-cms-payload-strapi
description: Rapidly scaffolds, configures, and deploys self-hosted TypeScript Headless CMS backends (Payload CMS, Strapi) with tailored collections, access control, and auto-generated REST/GraphQL APIs.
---

# Self-Hosted TypeScript Headless CMS Architect

This skill directs the rapid scaffolding, collection schema design, and deployment of self-hosted headless CMS solutions (Payload CMS v3 / Strapi v5).

## 1. Schema Modeling & Access Control

1. **Collection & Field Definitions**:
   - Model entities with typed relationship fields, localized content, rich text blocks, and media uploads.
   - Separate public content from private operational data using field-level access functions (`access: { read: isPublicOrAdmin, update: isAdmin }`).
2. **Hooks & Lifecycle Events**:
   - Utilize `beforeChange` and `afterChange` collection hooks for data sanitization, slug auto-generation, and search index synchronization.

## 2. API Distribution & Next.js Integration
- Deliver native Next.js App Router integrations leveraging Payload's local API (zero HTTP overhead when co-located in the same Next.js project).
- Secure auto-generated REST and GraphQL endpoints with API keys and role-based permissions.
