---
name: currency-exchange-engine
description: Manages real-time multi-currency pricing, exchange rate caching, markup buffers, and checkout currency lock periods.
---

# Multi-Currency Real-Time Exchange & Pricing Engine

This skill guides localized currency conversions, rate caching, foreign exchange risk buffers, and multi-currency checkout locks.

## 1. Rate Ingestion & Caching

1. **Scheduled Rate Synchronization**:
   - Ingest live Forex rates hourly from central bank APIs (e.g. Open Exchange Rates / European Central Bank).
   - Cache currency pairs in Redis with a 1-hour TTL to prevent third-party rate limit exhaustion.
2. **Forex Margin & Psychological Rounding**:
   - Apply a small risk buffer (e.g. +1.5% to +2.0%) to absorb intra-day currency volatility.
   - Apply psychological price formatting: Round converted prices to ending in `.99` or `.00` matching regional consumer norms.

## 2. Checkout Currency Locking
- Lock conversion rate for active checkout sessions for 30 minutes to prevent price changes mid-payment.
