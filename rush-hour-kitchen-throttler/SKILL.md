---
name: rush-hour-kitchen-throttler
description: Dynamically throttles order intake, calculates real-time estimated preparation times, and manages order pacing based on active kitchen load.
---

# Rush-Hour Kitchen Throttling & Order Pacing

This skill calculates dynamic kitchen preparation latencies, prevents order ticket overflows during lunch/dinner rushes, and paces incoming customer demand.

## 1. Kitchen Load Score Calculation

1. **Active Workload Metric**:
   - `KitchenLoadScore = Sum(Active Preparing Orders * Item Prep Complexity Weight)`
   - Fast item (Soda / Ice cream): Weight = 0.5.
   - Standard item (Single Burger / Fries): Weight = 1.0.
   - Slow item (Large Pizza / Well-done Steak): Weight = 3.0.
2. **Dynamic Delivery/Pickup ETA Adjustments**:
   - Score < 15: Standard ETA (20 - 25 mins).
   - Score 15 - 30: Elevated ETA (35 - 45 mins).
   - Score > 30: Rush ETA (55 - 65 mins) with warning banner in app/chat.

## 2. Emergency Order Pacing (Circuit Breaker)
- If active ticket backlog exceeds chef capacity, temporarily place new online delivery orders in a 10-minute waiting queue or display: *"Kitchen is currently at peak capacity. Next ordering window opens in 12 minutes."*
