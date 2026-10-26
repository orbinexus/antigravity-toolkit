---
name: cash-drawer-reconciliation
description: Manages shift-end cash drawer balancing, float counting, drop envelopes, and variance tracking against registered POS transactions.
---

# Shift-End Cash Drawer Balancing & Audit

This skill directs cash drawer reconciliation at the close of cashier shifts to audit physical currency against POS ledger records.

## 1. Shift Counting & Discrepancy Math

1. **Denomination Tally**:
   - Record currency counts by denomination ($100, $50, $20, $10, $5, coins).
   - `Total Counted Cash = Sum(Denominations)`.
2. **Variance Calculation**:
   - `Expected Cash = Opening Float + Cash Sales - Paid Out Expenses - Cash Drops`.
   - `Variance = Total Counted Cash - Expected Cash`.
   - Balanced ($0), Overage (> $0), Shortage (< $0).

## 2. Manager Audit & ESC/POS Printout
- Flag variances exceeding tolerance threshold (e.g. ±$5.00) for mandatory managerial sign-off.
- Print official "Z-Report" summary on thermal receipt printer detailing total gross sales, tax collected, cash, card, and delivery platform splits.
