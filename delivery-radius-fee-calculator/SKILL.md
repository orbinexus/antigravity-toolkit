---
name: delivery-radius-fee-calculator
description: Calculates geofenced delivery tiers, distance fees, minimum order thresholds, and rider dispatch zones using PostGIS and haversine calculations.
---

# Delivery Zone & Radius Fee Calculator

This skill directs the spatial calculation of delivery eligibility, tier-based delivery charges, and minimum order limits based on restaurant branch coordinates.

## 1. Radial Tiers & Polygon Zones

1. **Distance-Tier Formulas**:
   ```sql
   -- Distance in meters from Branch
   SELECT ST_Distance(branch_location, customer_location) as distance_meters;
   ```
   - Tier 1 (0 to 3,000m): Delivery Fee = Free, Min Order = $10.
   - Tier 2 (3,001 to 6,000m): Delivery Fee = $2.50, Min Order = $15.
   - Tier 3 (6,001 to 10,000m): Delivery Fee = $4.50, Min Order = $25.
   - > 10,000m: Reject with out-of-delivery-zone message.
2. **Custom Polygon Geofences**:
   - Define exact neighborhood delivery boundaries using GeoJSON polygons (`ST_Contains(delivery_polygon, customer_point)`).
   - Exclude unserviceable areas (rivers, bridges, congested zones) regardless of circular radius.
