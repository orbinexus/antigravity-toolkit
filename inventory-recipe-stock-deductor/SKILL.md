---
name: inventory-recipe-stock-deductor
description: Links menu items to Bill of Materials (BOM) recipes, automating ingredient inventory depletion upon order completion and issuing low-stock alerts.
---

# Recipe-Level Inventory Depletion & Stock Guardian

This skill models menu item recipes (Bill of Materials / BOM) and executes real-time stock deductions to maintain live food cost control and prevent 86'd item orders.

## 1. Bill of Materials (BOM) Recipe Modeling

```text
Double Cheeseburger:
  ├── Brioche Bun: 1 unit
  ├── Beef Patty (4oz): 2 units
  ├── Cheddar Slice: 2 units
  ├── Secret Sauce: 30 ml
  └── Packaging Box: 1 unit
```

1. **Atomic Stock Depletion**:
   - Deduct ingredient quantities upon order completion (`status = 'completed'` or `'preparing'`).
   - Support fractional units (grams, milliliters, kilograms).

## 2. Low-Stock Thresholds & Automated 86
- Define reorder levels per ingredient (e.g. Patty stock < 20 units ➔ warning alert).
- If key mandatory ingredient reaches 0, automatically issue an "86" command, disabling all dependent dishes across POS, Web, and WhatsApp catalogs.
