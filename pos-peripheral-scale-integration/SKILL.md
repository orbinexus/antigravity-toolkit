---
name: pos-peripheral-scale-integration
description: Connects digital weighing scales via Serial / USB (Web Serial API & RS232), reading real-time weights for per-gram and per-kilogram billing.
---

# POS Weighing Scale Serial Integration

This skill guides connecting digital checkout weighing scales via Web Serial API and USB-to-RS232 adapters.

## 1. Web Serial Communication

1. **Serial Port Connection**:
   ```javascript
   const port = await navigator.serial.requestPort();
   await port.open({ baudRate: 9600, dataBits: 8, stopBits: 1, parity: 'none' });
   ```
2. **Weight Parsing (Continuous vs Polled)**:
   - Parse standardized scale output strings (e.g. `ST,GS,+  0.450kg`).
   - Extract stable weight flag (`ST`) to ensure scale is not oscillating before locking price in cart.
3. **Price Calculation**:
   - `Line Item Total = Stable Net Weight * Unit Price per Kg`.
