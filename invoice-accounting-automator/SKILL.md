---
name: invoice-accounting-automator
description: Extracts, reconciles, and tabulates data from batch invoices, receipts, and bills (PDF/images) into validated Excel workbooks, CSV ledger reports, and accounting summaries.
---

# Invoice & Accounting Pipeline Automator

This skill processes unstructured financial documents (invoices, expense receipts, vendor bills) into reconciled accounting ledgers and automated financial reports.

## 1. Batch Extraction Workflow

1. **Document Tokenization**:
   - Extract key financial fields: Vendor/Issuer Name, Tax ID / NTN / VAT, Invoice Number, Issue Date, Due Date, Payment Terms.
   - Extract itemized line items: Description, Quantity, Unit Price, Line Total.
   - Extract totals: Subtotal, Discounts, Sales Tax / GST / VAT, Total Payable, Currency.
2. **Mathematical Reconciliation & Validation**:
   - Verify arithmetic integrity: `Sum(Line Items) - Discounts + Tax == Total Payable`.
   - Flag calculation discrepancies or missing line totals immediately.

## 2. Ledger Export Standards
- Generate standardized multi-column spreadsheets (`.xlsx` via Python `openpyxl` or Pandas) formatted with accounting styles (currency symbols, comma grouping, 2 decimal places).
- Categorize expenses automatically into chart-of-accounts buckets (Software, Hosting, Office, Travel, Contractor).
