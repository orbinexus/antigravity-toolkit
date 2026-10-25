---
name: cron-scheduler-watchdog
description: Designs distributed cron jobs, background schedulers, leader election, and distributed locks using Redis/Redlock to prevent duplicate task execution.
---

# Distributed Cron Scheduler & Watchdog

This skill guides the design of reliable, horizontally scalable scheduled background tasks, cron execution pipelines, and distributed concurrency guards.

## 1. Concurrency Guard & Distributed Locks

1. **Redis Redlock / Mutex Protocol**:
   - Acquire an atomic distributed lock before executing any scheduled job:
     `SET job_lock:<job_id> <random_token> NX PX <timeout_ms>`
   - Release the lock via Lua script only if the current holder matches the `<random_token>`.
2. **Horizontal Scaling Safety**:
   - Ensure jobs run exactly once across multi-container or serverless deployments (no duplicate execution across replicas).
3. **Heartbeat & Deadlock Prevention**:
   - Refresh active locks periodically for long-running jobs.
   - If a worker crashes mid-execution, allow locks to expire via TTL without deadlocking subsequent runs.

## 2. Job Retries & Dead-Letter Queues (DLQ)
- Implement exponential backoff for transient failures with max retry limits (e.g. 3 attempts).
- Automatically route permanently failed jobs to a Dead-Letter Queue with alerting (Slack/Telegram/PagerDuty).
