---
name: marketplace-escrow-split
description: Manages multi-vendor marketplace split payments, platform commission calculations, merchant payouts, and escrow holdbacks via Stripe Connect.
---

# Multi-Vendor Marketplace Split Payouts & Escrow

This skill directs payment splitting, platform fee deductions, and vendor payout schedules across multi-seller e-commerce marketplaces.

## 1. Split Payment Topology (Stripe Connect)

1. **Cart Multi-Vendor Breakdown**:
   - Deconstruct multi-vendor cart into seller-specific line item sub-orders:
     ```text
     Customer Pays: $100.00
       ├── Platform Commission (10%): $10.00 retained
       ├── Vendor A Share ($60 - 10% fee): $54.00 routed to Connected Account A
       └── Vendor B Share ($40 - 10% fee): $36.00 routed to Connected Account B
     ```
2. **Escrow Holdback & Release**:
   - Hold vendor payouts in escrow until delivery confirmation or past the return window (e.g. 7-day dispute buffer).
   - Handle chargebacks and partial refunds by debiting the specific vendor's pending payout ledger.
