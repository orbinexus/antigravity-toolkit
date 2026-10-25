---
name: stealth-scraper-playwright
description: High-reliability web scraping and data extraction using Playwright stealth configurations, fingerprint evasion, bot-detection bypass, infinite scroll handling, and structured data output.
---

# Stealth Web Scraping & Automated Data Extraction

This skill provides robust methodologies for extracting structured datasets from complex SPAs, JavaScript-heavy sites, and bot-protected web destinations.

## 1. Anti-Bot Evasion & Stealth Configurations

When initializing headless browser contexts:
1. **Mask Navigator Attributes**:
   - Overwrite `navigator.webdriver` to `undefined`.
   - Mimic authentic browser headers, platform architecture, languages (`navigator.languages`), and hardware concurrency (`navigator.hardwareConcurrency`).
   - Mock WebGL vendor/renderer hashes to avoid generic headless fingerprint flags.
2. **Humanized Cursor & Interaction Physics**:
   - Avoid instant clicks on exact element centers; use randomized curve trajectories (Bezier curves) and variable inter-keystroke intervals (50ms - 150ms).
3. **Viewport & Screen Properties**:
   - Set standard desktop resolutions (e.g. 1920x1080) with consistent `window.devicePixelRatio = 1`.

## 2. Dynamic Content & Infinite Scroll Handling

- Intercept background XHR/fetch traffic directly via `page.on('response', ...)` instead of parsing DOM nodes whenever the site fetches JSON endpoints under the hood.
- Implement exponential backoff for rate limiting and network timeouts.
- Use explicit element waiting (`waitForSelector`, `waitForResponse`) rather than arbitrary sleeps.

## 3. Output Formats

- Stream scraped entities directly into structured formats:
  - Streaming JSON Lines (`.jsonl`) for large datasets.
  - CSV / Pandas DataFrame export.
  - Clean Markdown format for AI synthesis and ingestion.
