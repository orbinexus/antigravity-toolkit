---
name: business-messaging-bot
description: Builds automated WhatsApp Cloud API and Telegram bot integrations for customer support, order tracking, real-time alerts, and interactive menus.
---

# Business Messaging Bot & Notification Engine

This skill guides the implementation of production-grade WhatsApp Cloud API and Telegram bot architectures with webhook verification, stateful conversation flows, and CRM integration.

## 1. Webhook Infrastructure & Verification

1. **Verification & Idempotency**:
   - Correctly implement webhook challenge handshakes (e.g. Meta `hub.challenge` verification token).
   - Use message IDs (`mid` / `message_id`) with Redis or database deduplication to prevent processing duplicate webhook deliveries.
2. **Interactive Elements**:
   - Deliver rich interactive menus: quick reply buttons, list pickers, and media cards rather than raw plain-text walls.
3. **Session & State Machine**:
   - Manage user conversation state with a lightweight finite state machine (FSM) or Redis session cache.
   - Route complex queries to human-agent handoff fallback.
