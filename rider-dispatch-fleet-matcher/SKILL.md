---
name: rider-dispatch-fleet-matcher
description: Automates delivery driver assignment, batching multiple orders along similar routes, and real-time GPS telemetry updates for customers.
---

# Delivery Driver Fleet Dispatch & Route Optimizer

This skill directs the real-time matching and dispatch of in-house and third-party delivery drivers to pending kitchen orders.

## 1. Dispatch Logic & Order Batching

1. **Auto-Assignment Timing**:
   - Trigger driver search 3 to 5 minutes *before* kitchen ticket completion based on target prep duration.
2. **Proximity & State Filtering**:
   - Filter active drivers by status (`idle`), vehicle type (Bike vs Car for catering orders), and distance to branch (`< 2.5 KM`).
3. **Smart Batching (Multiple Orders)**:
   - Allow a single driver to pick up 2 orders simultaneously if customer delivery addresses share a bearing within 25 degrees and distance within 1.5 KM.

## 2. Real-Time Tracking Link
- Generate signed, short-lived web tracking URLs for customers (`/track/ord_9871?sig=...`).
- Stream live driver GPS coordinates over WebSockets to client map view without leaking driver's personal phone number.
