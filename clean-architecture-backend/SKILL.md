---
name: clean-architecture-backend
description: Implements Clean/Hexagonal Architecture and Domain-Driven Design (DDD), decoupling domain entities, use cases, repositories, and presentation controllers.
---

# Clean & Hexagonal Backend Architecture

This skill guides the construction of enterprise-grade backend services with decoupled business logic, testable use cases, and interchangeable database/framework adapters.

## 1. Concentric Onion Layers

```text
src/
├── domain/       # Core enterprise business rules, entities, and value objects (No external dependencies)
├── usecases/     # Application business logic (interactors coordinating domain entities)
├── ports/        # Interface contracts (Repository interfaces, Notification interfaces)
└── adapters/     # Implementation adapters (Database ORM, HTTP Controllers, CLI, External APIs)
```

## 2. Dependency Inversion Rules
- The **Domain** and **Use Cases** must NEVER import from database drivers (Prisma, SQLAlchemy, Mongoose) or web frameworks (Express, FastAPI, Gin).
- Define ports as interfaces:
  `interface OrderRepository { save(order: Order): Promise<void>; }`
- Implement adapters in the outer layer:
  `class PostgresOrderRepository implements OrderRepository { ... }`
- Inject dependencies at application bootstrap (Dependency Injection container).
