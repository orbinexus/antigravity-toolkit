---
name: digital-stamp-wallet-pass
description: Generates signed Apple Wallet (.pkpass) and Google Wallet digital passes for customer loyalty cards, stamp rewards, and VIP memberships.
---

# Apple & Google Wallet Digital Pass Generator

This skill guides the cryptographic compilation, signing, and dynamic update of digital passes (`.pkpass` and Google Wallet JSON passes).

## 1. Apple Wallet (.pkpass) Architecture

1. **Pass Bundle Structure**:
   - `pass.json`: Fields, colors, barcode/QR payload, serial number.
   - `icon.png`, `logo.png`, `strip.png`.
   - `manifest.json`: SHA-1 hashes of all bundle files.
   - `signature`: Cryptographic PKCS#7 detached signature signed with Apple Pass Certificate.
2. **Dynamic Push Updates**:
   - Push silent APNs notifications to Apple device when customer points balance changes, dynamically updating the wallet card on the customer's lock screen.
