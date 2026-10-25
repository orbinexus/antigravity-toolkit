---
name: google-maps-platform
description: Integrates Google Maps Platform APIs including Dynamic Maps, Directions, Places Autocomplete, Geocoding, and Distance Matrix with quota optimization.
---

# Google Maps Platform Integration & Quota Optimization

This skill guides the implementation of interactive maps, route optimization, and address autocomplete while minimizing API quota billing.

## 1. Maps Javascript API & Places Autocomplete

1. **Session Tokens for Billing Reduction**:
   - Always initialize `AutocompleteSessionToken` when binding search inputs to Places Autocomplete. Group keystroke queries into a single billable Places Details call on user selection.
2. **Field Masking (`fields: [...]`)**:
   - Explicitly define requested fields (e.g. `['geometry.location', 'formatted_address', 'place_id']`) to avoid being billed for expensive Contact and Atmosphere data tiers.
3. **Dynamic Vector vs Static Maps**:
   - Use Static Maps (`maps.googleapis.com/maps/api/staticmap`) for non-interactive list views and email receipts to cut costs by 80%.
