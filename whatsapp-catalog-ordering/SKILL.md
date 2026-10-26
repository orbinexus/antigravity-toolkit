---
name: whatsapp-catalog-ordering
description: Integrates WhatsApp Cloud API Product Catalogs, interactive list messages, location sharing, and conversational cart checkout for restaurants.
---

# WhatsApp Catalog & Conversational Food Ordering

This skill guides the implementation of WhatsApp Cloud API food ordering with native product catalogs, quick replies, and location-based delivery dispatch.

## 1. Native WhatsApp Catalog & Messages

1. **Catalog Sync**:
   - Synchronize restaurant menu items with Meta Commerce Manager catalog via Graph API.
2. **Interactive Ordering Components**:
   - **Catalog Message**: Sends complete browsable menu inside WhatsApp chat.
   - **Order Message**: When customer clicks "Send Cart to Business", parse `order` webhook payload containing selected items, quantities, and prices.
3. **Location Pin Capture**:
   - Send prompt: *"Please share your live location or delivery pin on WhatsApp"*.
   - Parse `location` message (`latitude`, `longitude`) to calculate exact distance and routing.

## 2. Order Status Push Updates
- Send automated WhatsApp template updates:
  - *"🍕 Your order #1042 has been confirmed by the kitchen! Prep time: ~20 mins."*
  - *"🛵 Rider Ahmed is on the way with your food! Track: [Link]"*
