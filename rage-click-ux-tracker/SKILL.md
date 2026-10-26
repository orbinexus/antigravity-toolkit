---
name: rage-click-ux-tracker
description: Instruments privacy-friendly, lightweight browser UX telemetry to detect rage-clicks, dead clicks, form abandonment, and friction funnels without heavy analytics bloat.
---

# Privacy-Friendly Rage-Click & UX Friction Tracker

This skill guides the implementation of client-side UX friction detection (rage clicks, dead clicks, rapid re-submits) without invasive cookies or heavy third-party tracking scripts.

## 1. Friction Detection Algorithms

1. **Rage Click Detection**:
   - Detect 3 or more mouse clicks within a 500ms window on the same target element within a 30px bounding radius.
   - Signal: Broken links, unresponsive buttons, slow network handlers without loading spinners.
2. **Dead Click Detection**:
   - Click registered on a non-interactive element (e.g. static image or styled heading) where user expects a link or action.
3. **Form Abandonment & Input Hesitation**:
   - Track fields where users spend >10s without typing or repeatedly backspace/clear inputs.

## 2. Zero-PII Telemetry Emission
- Redact all form input values before sending telemetry payloads.
- Transmit batched events via `navigator.sendBeacon` upon page unload to ensure zero impact on user navigation speed.
