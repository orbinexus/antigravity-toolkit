---
name: multi-carrier-shipping-sync
description: Orchestrates shipping rate shopping, shipping label generation (ZPL/PDF), and unified package tracking across couriers (DHL, FedEx, TCS, Leopards).
---

# Multi-Carrier Shipping & Label Dispatch Engine

This skill guides integrating multiple courier APIs (DHL, FedEx, UPS, TCS, Leopards, Trax) to compare real-time shipping rates and generate printable waybills.

## 1. Rate Shopping & Label Creation

1. **Cheapest / Fastest Courier Selection**:
   - Query rates across couriers matching parcel weight, dimensions, and destination zone.
   - Select optimal courier based on business rules (e.g. lowest cost for standard orders; fastest courier for express).
2. **Waybill & Barcode Generation**:
   - Generate thermal 4x6 inch shipping labels in ZPL (Zebra) or PDF format with courier-specific 1D/2D barcodes.
3. **Unified Tracking Polling & Webhooks**:
   - Normalize tracking milestones (`Picked Up`, `In Transit`, `Out for Delivery`, `Failed Attempt`, `Delivered`) into standardized event webhooks.
