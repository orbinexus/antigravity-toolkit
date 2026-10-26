---
name: dynamic-tax-calculator
description: Computes localized sales tax, GST, and VAT rules dynamically by jurisdiction, item exemption classification, and customer exemption status.
---

# Dynamic Invoice Sales Tax, GST & VAT Calculator

This skill guides the automated calculation of multi-jurisdictional indirect taxes, sales taxes, and regional GST rates.

## 1. Tax Jurisdiction Hierarchy

1. **Nexus & Destination Sourcing**:
   - Determine applicable jurisdiction using delivery destination (State/Province + Postal Code).
   - Support composite taxes (e.g. Canada GST + PST / HST; US State + County + City tax).
2. **Product Exemption Categories**:
   - Tag items with standard tax codes (e.g. Raw Groceries = 0% Exempt; Prepared Hot Food = Full Standard Tax; Digital Software = SaaS Tax Rate).
3. **B2B Reverse Charge & Exemption Certificates**:
   - Validate customer Tax ID / VAT Number via official registry APIs (e.g. EU VIES) to apply zero-rated reverse charge on intra-state B2B transactions.
