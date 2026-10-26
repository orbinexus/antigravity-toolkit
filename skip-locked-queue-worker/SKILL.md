---
name: skip-locked-queue-worker
description: Implements zero-deadlock, high-throughput job queues directly inside PostgreSQL using SELECT FOR UPDATE SKIP LOCKED without external message brokers.
---

# PostgreSQL SKIP LOCKED Job Queue Worker

This skill guides the design of resilient, ACID-compliant background job queues directly inside PostgreSQL without introducing Redis, RabbitMQ, or external dependencies.

## 1. Queue Schema & Concurrency Pattern

1. **Job Queue Schema**:
   ```sql
   CREATE TABLE job_queue (
     id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
     queue_name VARCHAR(64) NOT NULL,
     payload JSONB NOT NULL,
     status VARCHAR(20) NOT NULL DEFAULT 'pending', -- pending, processing, completed, failed
     attempts INT NOT NULL DEFAULT 0,
     max_attempts INT NOT NULL DEFAULT 3,
     scheduled_at TIMESTAMPTZ NOT NULL DEFAULT NOW(),
     created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
   );
   CREATE INDEX idx_job_queue_fetch ON job_queue (queue_name, scheduled_at) WHERE status = 'pending';
   ```
2. **Atomic Dequeue (`SKIP LOCKED`)**:
   - Fetch and lock jobs across multiple concurrent workers with zero contention:
     ```sql
     WITH next_job AS (
       SELECT id FROM job_queue
       WHERE queue_name = $1 AND status = 'pending' AND scheduled_at <= NOW()
       ORDER BY scheduled_at ASC
       FOR UPDATE SKIP LOCKED
       LIMIT 1
     )
     UPDATE job_queue
     SET status = 'processing', attempts = attempts + 1
     WHERE id = (SELECT id FROM next_job)
     RETURNING *;
     ```

## 2. Crash Recovery & Poison Pill Mitigation
- Periodically reset jobs stranded in `processing` status past a heartbeat threshold (e.g. 5 minutes) back to `pending`.
- Move permanently failed jobs (`attempts >= max_attempts`) to `failed` state with detailed error stacks.
