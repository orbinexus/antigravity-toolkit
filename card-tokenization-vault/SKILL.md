---
name: card-tokenization-vault
description: Implements PCI-DSS compliant credit card tokenization, client-side encryption, and iframe payment fields to achieve zero PCI audit liability.
---

# PCI-DSS Credit Card Tokenization & Zero-Liability Vault

This skill guides collecting and tokenizing credit card information client-side to achieve SAQ-A compliance, ensuring raw cardholder data never touches application servers.

## 1. Zero-Liability Tokenization Architecture

1. **Hosted Fields / Iframe Sandboxing**:
   - Render credit card number, expiry, and CVV fields inside sandboxed iframes hosted directly by the payment processor (Stripe Elements, Braintree, Adyen).
   - Parent application never receives raw PAN (Primary Account Number) characters; receives only an opaque single-use token (`tok_1Nxxxx`).
2. **Backend Token Storage**:
   - Backend stores strictly:
     - `payment_method_id` (token).
     - Card Brand (`visa`, `mastercard`).
     - Last 4 Digits (`**** 4242`).
     - Expiry Month / Year for customer wallet displays.
   - Strictly prohibit logging or storing 3-digit CVV / CVC codes under any circumstance.
