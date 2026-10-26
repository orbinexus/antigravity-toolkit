---
name: automated-dine-in-split-check
description: Calculates dining check splits (even split, seat-by-seat itemized split, and multi-tender split payments) with tax and tip balancing.
---

# Dine-In Split-The-Check & Multi-Pay Engine

This skill guides the mathematical calculation and state management of complex restaurant bill splits and multi-tender payments.

## 1. Splitting Modalities

1. **Even Split (N-Ways)**:
   - Divide total bill by N diners. Round cents mathematically so `Sum(Split Shares) == Total Bill` (allocate rounding remainder to first share).
2. **Itemized Seat-by-Seat Split**:
   - Assign order lines to specific seats (`seat_id`).
   - Split shared appetizers evenly across selected seats.
   - Allocate taxes, service charges, and discounts proportionally to each seat's subtotal.
3. **Multi-Tender Payments**:
   - Allow a single bill to settle across mixed tenders (e.g. $40 Cash + $35 Visa Card + $10 Loyalty Voucher).
