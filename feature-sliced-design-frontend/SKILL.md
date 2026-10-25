---
name: feature-sliced-design-frontend
description: Architects scalable frontend codebases using Feature-Sliced Design (FSD), isolating app, pages, widgets, features, entities, and shared layers.
---

# Feature-Sliced Design (FSD) Frontend Architect

This skill organizes complex React, Next.js, and Vue codebases using Feature-Sliced Design methodology to maintain modularity, testability, and zero spaghetti coupling.

## 1. Architectural Layers & Hierarchy

Organize the frontend source tree into strict, top-to-bottom layers (lower layers cannot import from upper layers):

```text
src/
├── app/        # App routing, global providers, and entry points
├── pages/      # Route pages composed of widgets and features
├── widgets/    # Self-contained compositional UI blocks (e.g. Header, FeedList)
├── features/   # User interactions that bring business value (e.g. auth-by-phone, add-to-cart)
├── entities/   # Business entities and models (e.g. User, Product, Order)
└── shared/     # Reusable UI kit, API clients, helpers, and configurations
```

## 2. Slice & Segment Discipline
- Each layer is divided into **Slices** (e.g. `entities/user`, `features/checkout`).
- Each slice is divided into **Segments**:
  - `ui/`: Visual React components.
  - `model/`: State machines, stores (Zustand/Redux), and business logic.
  - `api/`: Backend query hooks and endpoints.
  - `lib/`: Slice-specific helpers.
- **Public API Rule**: Every slice must expose an `index.ts` public gateway. Cross-slice imports must only import from the public API (`import { UserCard } from '@/entities/user'`), never internal implementation paths.
