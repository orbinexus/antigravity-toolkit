---
name: escpos-thermal-printer-engine
description: Generates raw ESC/POS binary commands for automated 80mm/58mm thermal receipt printers (LAN, USB, Bluetooth) for Kitchen Order Tickets (KOT) and customer receipts.
---

# ESC/POS Thermal Receipt & Kitchen Order Ticket (KOT) Engine

This skill guides generating raw ESC/POS byte sequences for instant receipt and kitchen ticket printing over Network (TCP/IP), USB, or Serial ports.

## 1. ESC/POS Command Standards (80mm Width)

1. **Ticket Layout Standards**:
   - `ESC @`: Initialize printer hardware.
   - `ESC a 1`: Center alignment for Restaurant Name and Header.
   - `ESC ! 0x30`: Double-height & double-width text for Table Number / Order ID.
   - `GS V 66 0`: Perform full/partial paper cut.
   - `ESC p 0 25 250`: Pulse cash drawer kick-out pin.
2. **KOT (Kitchen Order Ticket) Formatting**:
   - Prominently highlight special dietary requests (e.g. `*** NO ONIONS ***`, `*** ALLERGY: PEANUT ***`) in emphasized inverted text (`GS B 1`).

## 2. Network (LAN / Wi-Fi) Socket Printing
- Send raw byte buffers directly to printer IP address on standard port `9100` (`net.connect({ host: '192.168.1.200', port: 9100 })`).
- Handle offline buffer retries and out-of-paper status sensor queries (`DLE EOT 1`).
