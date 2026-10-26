---
name: session-replay-privacy-engine
description: Implements lightweight, privacy-preserving in-browser session replay telemetry (rrweb style) with automated DOM masking and zero PII leakage.
---

# Privacy-Preserving In-Browser Session Replay

This skill directs client-side user session recording using DOM mutation events (rrweb architecture) while enforcing strict privacy masking for confidential data.

## 1. DOM Mutation Recording

1. **MutationObserver Capture**:
   - Record initial DOM snapshot followed by incremental DOM mutation events, mouse movements, clicks, and viewport resizes.
   - Throttling: Throttle mouse move telemetry to 50ms intervals to keep bandwidth usage minimal.
2. **Automated PII & Input Masking**:
   - Mask all `<input>`, `<textarea>`, and `<select>` values by default (replace with `***`).
   - Add `.mask-private` CSS class handlers to blur sensitive customer balance, health, or personal details on the DOM node before serialization.

## 2. Event Compression & Streaming Sinks
- Compress batched JSON mutation events using Gzip / Deflate via `CompressionStream` in the browser before transmission.
- Stream chunks asynchronously to object storage (Cloudflare R2 / S3) via background workers.
