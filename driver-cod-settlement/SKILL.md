---
name: driver-cod-settlement
description: Reconciles daily Cash-on-Delivery collections with delivery riders, calculating net payouts, fuel deductions, and cash drawer handovers.
---

# Delivery Driver COD & Cash Settlement Engine

This skill guides the end-of-shift reconciliation of cash collected by delivery riders against dispatched order totals.

## 1. Settlement Math & Reconciliation

```text
Net Driver Cash Due = Total Cash Orders Delivered - Authorized Fuel Allowance - Return Vouchers
```

1. **Shift Balancing Workflow**:
   - Query all orders marked `status = 'delivered'` and `payment_method = 'COD'` assigned to `driver_id`.
   - Calculate itemized order amounts, tips collected, and cash handed over to shift manager.
2. **Discrepancy Resolution**:
   - Flag shortages (`Cash Handed In < System Recorded Cash`) or overages with manager override reasons.
   - Print thermal settlement receipt signed by driver and store manager.
