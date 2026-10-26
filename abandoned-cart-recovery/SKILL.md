---
name: abandoned-cart-recovery
description: Recovers abandoned checkouts via scheduled multi-channel messages (WhatsApp, SMS, Email) with dynamic discount incentives and click attribution tracking.
---

# Abandoned Cart WhatsApp & Multi-Channel Recovery

This skill guides automated detection, timing triggers, and incentive strategies to recover abandoned e-commerce carts.

## 1. Trigger Timeline & Attribution

1. **Abandonment Detection**:
   - Flag cart as abandoned when customer completes contact info (Email or WhatsApp phone) but does not complete checkout within 30 minutes.
2. **Multi-Stage Recovery Sequence**:
   - **Stage 1 (30 Mins)**: Helpful reminder on WhatsApp/Email: *"Did you leave something behind? Your cart is saved."*
   - **Stage 2 (24 Hours)**: Value proposition + Social Proof: *"These popular items are selling out fast! [Customer Reviews]"*
   - **Stage 3 (48 Hours)**: Dynamic discount incentive: *"Complete your purchase in the next 12 hours and get 10% off with code RECOVER10"*.

## 2. One-Click Deep-Link Cart Restoration
- Generate signed, short-lived restoration URLs (`/cart/restore?token=...`) that automatically rebuild the customer's cart, prefill address, and apply coupon codes in 1 click.
