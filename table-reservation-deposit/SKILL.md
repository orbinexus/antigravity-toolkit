---
name: table-reservation-deposit
description: Manages table reservations, party size constraints, time-slot allocation, and automated advance deposits to prevent no-shows.
---

# Restaurant Table Reservation & No-Show Deposit Engine

This skill directs the management of dining room floor plans, table booking slots, and upfront reservation token payments.

## 1. Capacity & Slot Allocation

1. **Floor Plan & Table Combining**:
   - Model table capacities (e.g. Table 4 = 2 seats, Table 5 = 4 seats). Allow dynamic combinations (Table 4 + 5 = 6 seats).
   - Standard booking duration: 90 minutes for casual dining; 120 minutes for fine dining.
2. **No-Show Mitigation via Advance Deposit**:
   - For parties of 6 or more, require a nominal per-head deposit ($10/seat) via Stripe / credit card.
   - Automatically refund deposit to bill total upon customer check-in at the restaurant.

## 2. Automated WhatsApp Reminders
- Send automated WhatsApp confirmation:
  - 24 hours before: *"Confirm your table for 6 tomorrow at 8:00 PM: [Reply 1 to Confirm / Reply 2 to Reschedule]"*.
  - 2 hours before: *"Your table is being prepared! See you soon."*
