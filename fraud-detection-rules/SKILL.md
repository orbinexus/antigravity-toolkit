---
name: fraud-detection-rules
description: Implements rule engines, carding attack mitigation, velocity checks, and anomaly scoring for e-commerce checkout and authentication endpoints.
---

# E-Commerce Anti-Fraud & Risk Engine

This skill directs the implementation of velocity checks, device fingerprinting, carding mitigation, and transactional anomaly scoring for online checkouts and authentication flows.

## 1. Velocity Checking & Carding Mitigation

1. **Carding Defense**:
   - Track failed payment attempt velocity by IP, subnet, device hash, and BIN (Bank Identification Number).
   - Enforce progressive delays or step-up challenges (e.g. 3D Secure / CAPTCHA) upon consecutive payment authorization declines.
2. **Checkout Velocity Checks**:
   - Limit checkout attempts per credit card token per hour (`max 3 attempts / hour`).
   - Flag disparate billing vs shipping countries, disposable email domains, and mismatched card issuance geography.

## 2. Risk Scoring & Decision State
- Aggregate signals into a weighted risk score (0 to 100):
  - `0 - 30`: Allow transaction automatically.
  - `31 - 70`: Challenge with 3DS or SMS verification.
  - `71 - 100`: Hard decline and quarantine user account for manual review.
