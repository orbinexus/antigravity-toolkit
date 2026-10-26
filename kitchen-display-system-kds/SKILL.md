---
name: kitchen-display-system-kds
description: Architects real-time Kitchen Display System (KDS) dashboards with WebSockets, audio alerts, color-coded preparation timers, and station routing.
---

# Real-Time Kitchen Display System (KDS) Architect

This skill directs the development of touch-screen Kitchen Display Systems (KDS) deployed on tablets, commercial touch monitors, and overhead TV displays.

## 1. Station Routing & Ticket Lifecycle

1. **Station Routing**:
   - Route order line items to specific kitchen prep stations based on category tags:
     - Grill Station: Burgers, Steaks.
     - Fryer Station: French Fries, Wings.
     - Bar / Beverage Station: Shakes, Sodas.
2. **Ticket Status Columns**:
   - `NEW` (Flashing green + audio chime).
   - `PREPARING` (Elapsed timer counting up).
   - `READY` (Triggers notification to waitstaff or dispatch rider).
   - `BUMPED / COMPLETED` (Archived with total prep latency metrics).

## 2. Dynamic Visual Urgency & Audio Cues
- Color-coded tickets based on target prep duration (e.g. Target: 12 mins):
  - Green: 0 - 8 mins.
  - Yellow: 8 - 12 mins.
  - Red + Pulsing Border: > 12 mins (Overdue).
