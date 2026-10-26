---
name: kitchen-printer-load-balancer
description: Manages multi-printer kitchen routing, automatic paper-out failovers, and parallel station printing across ESC/POS networks.
---

# Kitchen Printer Failover & Routing Engine

This skill directs automated ticket routing, station splitting, and paper-out failover mechanics across multiple network thermal printers.

## 1. Station Routing & Splitting

1. **Category Mapping**:
   - Route line items to specific printers:
     - `Printer_Grill`: Burgers, Steaks.
     - `Printer_Bar`: Juices, Mocktails.
2. **Automatic Failover Handling**:
   - Query printer status via ESC/POS real-time status byte (`DLE EOT 1`).
   - If a printer reports paper-out or network timeout, automatically reroute tickets to a designated backup printer and emit a sound alarm at the cashier terminal.
