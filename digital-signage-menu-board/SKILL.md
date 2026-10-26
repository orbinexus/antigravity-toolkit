---
name: digital-signage-menu-board
description: Synchronizes overhead TV digital menu boards in real time via WebSockets, rendering animated menu cards, video promos, and instant price updates.
---

# Real-Time Overhead TV Digital Menu Board Sync

This skill directs the development of fullscreen digital signage menu boards for restaurant counters and drive-thru TV monitors.

## 1. Real-Time Display Architecture

1. **WebSocket Synchronization**:
   - TV browser connects to `/ws/display?branch=clifton&screen=board_1`.
   - Listens for `PRICE_UPDATE`, `ITEM_OUT_OF_STOCK`, and `PROMO_TAKEOVER` events to re-render without browser refresh.
2. **Offline Resilience & Local Caching**:
   - Cache video assets and menu data in IndexedDB/CacheStorage so screens remain fully functional even during internet outages.

## 2. Dynamic Layout & Visual Pacing
- Grid layouts optimized for 4K / 1080p landscape and portrait orientation.
- Scheduled daytime takeovers (Breakfast menu 7:00 AM - 11:00 AM ➔ Lunch/Dinner menu 11:01 AM onwards).
