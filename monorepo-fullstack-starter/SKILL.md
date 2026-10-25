---
name: monorepo-fullstack-starter
description: Orchestrates full-stack monorepos with Turborepo, pnpm workspaces, shared TypeScript types, shared UI component packages, and shared configs.
---

# Full-Stack Monorepo Unified Blueprint

This skill structures multi-package enterprise repositories containing web applications, mobile apps, backend services, and shared libraries under a single Turborepo / pnpm workspace.

## 1. Monorepo Directory Architecture

```text
├── apps/
│   ├── web/          # Next.js customer-facing web application
│   ├── admin/        # React/Vite internal administrative dashboard
│   ├── api/          # FastAPI / NestJS backend service
│   └── mobile/       # React Native / Expo mobile application
├── packages/
│   ├── ui/           # Shared Tailwind CSS UI component design system
│   ├── types/        # Shared TypeScript interfaces, DTOs, and Zod schemas
│   ├── config/       # Shared ESLint, Prettier, and TypeScript configurations
│   └── database/     # Prisma / Drizzle schema, migrations, and shared client
├── package.json      # Root workspace configuration
└── turbo.json        # Build pipeline execution graph and caching rules
```

## 2. Shared Type Synchronization & Zero-Duplication
- Any update to `packages/types` or `packages/database` triggers instant type-checking errors across `apps/web` and `apps/mobile` during development.
- Turborepo caches task outputs (`build`, `lint`, `test`) based on file content hashes, reducing CI/CD build runtimes by up to 85%.
