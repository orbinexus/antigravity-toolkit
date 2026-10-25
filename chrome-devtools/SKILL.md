---
name: chrome-devtools
description: Automates browser inspection, console log interception, network waterfall diagnostics, and DOM tree debugging via Chrome DevTools Protocol (CDP).
---

# Chrome DevTools & CDP Automation

This skill guides deep browser runtime diagnostics, network request throttling, and console exception inspection via Chrome DevTools Protocol.

## 1. Runtime Diagnostics & Tracing

1. **Console & Exception Tracking**:
   - Intercept uncaught JavaScript exceptions, unhandled Promise rejections, and CSP violation reports.
2. **Network Waterfall Analysis**:
   - Inspect request timings: DNS lookup, Initial connection, SSL handshake, TTFB (Time to First Byte), and Content Download.
   - Simulate network conditions: Slow 3G / Fast 3G to identify bandwidth-choking payloads.
3. **DOM & CSS Computed Rules**:
   - Audit layout recalculations and forced synchronous layouts (layout thrashing) triggered by accessing `offsetHeight` / `getBoundingClientRect` inside loops.
