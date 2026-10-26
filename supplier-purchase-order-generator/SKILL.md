---
name: supplier-purchase-order-generator
description: Generates automated supplier Purchase Orders (PO) based on ingredient reorder thresholds, supplier price books, and delivery schedules.
---

# Automated Vendor Purchase Order (PO) Generator

This skill directs the generation and dispatch of supplier purchase orders when inventory levels dip below safety stock thresholds.

## 1. PO Generation Rules

1. **Reorder Math**:
   - `Order Quantity = Max Target Stock - (Current Stock + Pending On-Order)`.
   - Match ingredients to approved primary and secondary suppliers with minimum order quantity (MOQ) constraints.
2. **Standard PO Document**:
   - Generate standardized PO PDF with PO Number, Supplier Tax ID, Delivery Address, Itemized Line Items, Unit Costs, and Payment Terms (e.g. Net 30).
3. **Dispatch Sinks**:
   - Transmit PO automatically via WhatsApp or email to vendor rep with confirmation webhook link.
