---
name: multi-branch-franchise-sync
description: Orchestrates central menu distribution, branch price overrides, inventory transfers, and consolidated multi-location restaurant analytics.
---

# Multi-Branch Franchise & Chain Management

This skill directs the synchronization of menus, local pricing variations, and consolidated sales telemetry across multiple restaurant locations.

## 1. Global vs Local Configuration

1. **Master Catalog Inheritance**:
   - Master Catalog defines universal items, recipes, and brand assets.
   - Branch overrides: Allow specific branches to set custom local pricing or localized tax rates (e.g. Airport branch charges 15% premium).
2. **Real-Time Fleet Distribution**:
   - Push menu updates to all branch POS terminals via WebSocket / MQTT message bursts with automatic acknowledge receipts.

## 2. Inter-Branch Stock Transfers & Comparative Analytics
- Track ingredient transfers between central commissary kitchen and retail branches.
- Generate comparative location performance matrices (Sales, Average Ticket Size, Labor Cost %).
