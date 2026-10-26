---
name: table-qr-ordering-engine
description: Builds zero-app QR code dine-in table ordering web apps with table session locking, split billing, and digital waiter buzzers.
---

# QR Code Dine-In Table Ordering Engine

This skill guides the construction of zero-install, browser-based web applications for dine-in restaurant customers scanning QR codes on dining tables.

## 1. Table Session Architecture

1. **Signed QR Token Routing**:
   - Encode table number and cryptographic HMAC into QR code URL: `/menu?branch=dha&table=14&token=a8f...`
   - Binds all cart additions strictly to Table 14 without requiring customer registration or phone input.
2. **Shared Table Cart & Split-Billing**:
   - Multiple diners at Table 14 can join the same active WebSocket table session.
   - Support split payments: Diner A pays for their burger, Diner B pays for their pasta.

## 2. In-App Waiter Call & Bill Request
- "Call Waiter" buzzer emits instant audible alert to waitstaff smartwatch or POS counter.
- "Request Paper Bill" or "Pay with Card / Cash" button prints counter bill automatically.
