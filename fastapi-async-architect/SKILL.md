---
name: fastapi-async-architect
description: Architects ultra-fast asynchronous Python microservices using FastAPI, Pydantic v2, async database drivers (asyncpg/SQLAlchemy), and background task queues.
---

# FastAPI Asynchronous Microservice Architect

This skill guides the design of high-throughput, low-latency asynchronous microservices and RESTful APIs in modern Python (3.11+).

## 1. Asynchronous Architecture & Non-Blocking I/O

1. **Async Discipline**:
   - Every I/O operation (database queries, network requests, file access) must use native `async`/`await` drivers (`asyncpg`, `httpx`, `aiofiles`).
   - Never run blocking synchronous calls (e.g. `requests.get()`, `time.sleep()`) in an `async def` route; offload CPU-bound tasks via `asyncio.to_thread` or Celery/Arq workers.
2. **Pydantic v2 Validation**:
   - Utilize strict typing, field validators, computed fields, and annotated validators for zero-overhead serialization and schema generation.
3. **Dependency Injection**:
   - Leverage `fastapi.Depends` for database session lifecycles, user authentication contexts, and rate limiting.

## 2. Lifespan & Connection Pooling
- Use `lifespan` context managers on `FastAPI(lifespan=...)` for startup/shutdown of database connection pools and Redis caches.
- Handle global exceptions via custom `@app.exception_handler` returning uniform JSON error bodies.
