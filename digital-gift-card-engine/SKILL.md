---
name: digital-gift-card-engine
description: Issues, redeems, and audits digital gift cards with cryptographic codes, PIN verification, partial redemption balances, and expiration tracking.
---

# Digital Gift Cards & Store Credit Engine

This skill guides generating, redeeming, and securing digital gift cards and prepaid customer store credit balances.

## 1. Code Generation & Security Architecture

1. **Card Code & Secret PIN**:
   - Issue alphanumeric codes with Luhn-algorithm check digits: `XXXX-XXXX-XXXX-XXXX`.
   - Store hashed PINs (bcrypt/Argon2) separately to prevent unauthorized redemption through simple card number guessing.
2. **Partial Redemption & Balance Tracking**:
   - Support partial balance consumption:
     `If Order Total = $35 and Card Balance = $50, deduct $35 and retain $15 remaining balance`.
   - Atomic balance deduction using database row locks (`SELECT balance FROM gift_cards WHERE id = $1 FOR UPDATE`) to prevent race-condition double spending.

## 2. Ledger Audit Trail
- Every redemption and credit issuance must record an immutable ledger entry with `order_id`, `amount`, and `remaining_balance`.
