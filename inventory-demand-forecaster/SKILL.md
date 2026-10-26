---
name: inventory-demand-forecaster
description: Forecasts inventory demand using historical sales trends, seasonal patterns, and lead times to calculate safety stock thresholds and avoid stockouts.
---

# Inventory Demand Forecasting & Safety Stock AI

This skill guides predictive inventory modeling, stockout probability analysis, and automated replenishment recommendations for e-commerce and retail warehouses.

## 1. Safety Stock & Reorder Point Formulas

1. **Reorder Point (ROP)**:
   ```text
   ROP = (Average Daily Sales * Lead Time in Days) + Safety Stock
   ```
2. **Safety Stock Formula**:
   - `Safety Stock = Z-Score * Standard Deviation of Lead Time Demand`.
   - Use $Z = 1.65$ for 95% service level; $Z = 2.33$ for 99% critical items.
3. **Seasonality & Trend Smoothing**:
   - Apply exponential smoothing (Holt-Winters method) across historical sales data to account for seasonal spikes (holidays, promotion events, paydays).
