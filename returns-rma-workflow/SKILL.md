---
name: returns-rma-workflow
description: Manages customer return authorizations (RMA), return shipping labels, warehouse inspection workflows, and automated refund/store credit issuances.
---

# Automated E-Commerce Returns & RMA Engine

This skill guides customer return requests, return eligibility validation, return shipping label generation, and warehouse inspection refunds.

## 1. Return Merchandise Authorization (RMA) Lifecycle

```text
[RETURN_REQUESTED] (Reason: Damaged / Wrong Size / Changed Mind)
       │
       ▼ (Check Return Policy: within 14 days & non-final sale)
[RMA_APPROVED] ──► Generate Prepaid Reverse Shipping Label (PDF/QR)
                          │
                          ▼
                  [PARCEL_IN_TRANSIT] (Track return tracking #)
                          │
                          ▼
                  [WAREHOUSE_INSPECTED]
                    ├── Accepted: Trigger automated Stripe/Bank refund or issue Store Credit
                    └── Rejected: Notify customer with photographic evidence
```

## 2. Restocking & Inventory Reverse Logic
- Upon warehouse inspection sign-off, increment saleable stock automatically or route to "Damaged/Refurbished" quarantine inventory.
