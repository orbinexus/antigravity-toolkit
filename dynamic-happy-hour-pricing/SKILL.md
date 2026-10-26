---
name: dynamic-happy-hour-pricing
description: Automates time-based dynamic pricing rules, happy hour discounts, weekend surcharges, and scheduled menu promotions.
---

# Happy Hour & Time-Based Dynamic Pricing Engine

This skill guides the automated evaluation of scheduled price adjustments, promotional discounts, and surge pricing across digital ordering channels.

## 1. Schedule & Rule Evaluation

1. **Time Window Matching**:
   - Check local branch timezone: `IF current_time BETWEEN '15:00' AND '18:00' AND day_of_week IN ('Mon', 'Tue', 'Wed', 'Thu') THEN apply_rule('happy_hour')`.
2. **Pricing Actions**:
   - Fixed discount (e.g. $2.00 off on all Specialty Mocktails).
   - Percentage discount (e.g. 25% off Appetizers category).
   - "Buy One Get One" (BOGO) bundle evaluation.

## 2. Order Checkout Safeguards
- Calculate dynamic pricing strictly on backend during cart checkout to prevent client-side price tampering.
- Display clear countdown timers on digital menus: *"Happy hour ends in 24 minutes!"*.
