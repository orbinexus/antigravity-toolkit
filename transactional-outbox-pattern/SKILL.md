---
name: transactional-outbox-pattern
description: Implements the Transactional Outbox pattern to guarantee 100% atomic state updates and asynchronous event emissions across microservices without dual-write failures.
---

# Transactional Outbox & Event Reliability Pattern

This skill guides the elimination of dual-write discrepancies in event-driven systems, ensuring database state and event bus messages stay 100% synchronized.

## 1. Outbox Table & Atomic Commits

1. **The Outbox Table**:
   ```sql
   CREATE TABLE outbox_events (
     id UUID PRIMARY KEY DEFAULT gen_random_uuid(),
     aggregate_type VARCHAR(64) NOT NULL,
     aggregate_id VARCHAR(64) NOT NULL,
     event_type VARCHAR(64) NOT NULL,
     payload JSONB NOT NULL,
     created_at TIMESTAMPTZ NOT NULL DEFAULT NOW()
   );
   ```
2. **Single Transaction Boundary**:
   - Write domain mutations and outbox event records inside the exact same database transaction:
     ```sql
     BEGIN;
     INSERT INTO orders (id, user_id, total) VALUES (...);
     INSERT INTO outbox_events (aggregate_type, aggregate_id, event_type, payload) VALUES ('order', '123', 'OrderPlaced', '{...}');
     COMMIT;
     ```

## 2. Event Relay & Idempotent Consumer
- Forward outbox records to Kafka, RabbitMQ, or SNS using Change Data Capture (Debezium WAL reader) or a polling relay worker.
- Consumers must deduplicate events using `outbox_events.id` to guarantee at-least-once delivery safety.
