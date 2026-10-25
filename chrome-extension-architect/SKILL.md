---
name: chrome-extension-architect
description: Architects, develops, and packages modern Chrome and Edge browser extensions using Manifest V3, service workers, content scripts, storage sync, and side panels.
---

# Chrome & Edge Extension Architect (Manifest V3)

This skill guides the end-to-end development of modern, performant, and store-compliant browser extensions for Chrome and Chromium-based browsers.

## 1. Manifest V3 Architecture

1. **Declarative Configuration (`manifest.json`)**:
   - Strictly follow Manifest V3 schema (`"manifest_version": 3`).
   - Request the absolute minimum required permissions (e.g. `storage`, `activeTab`, `scripting`).
   - Define service workers (`"background": { "service_worker": "background.js" }`) without persistent background pages.
2. **Component Separation**:
   - **Service Worker**: Handles lifecycle events, alarm scheduling, and cross-tab communication. Never relies on in-memory global state (use `chrome.storage.local` / `chrome.storage.session`).
   - **Content Scripts**: Injected into web pages for DOM inspection, event listeners, and UI overlays. Communicate with background worker via message passing (`chrome.runtime.sendMessage`).
   - **Popups & Side Panels**: Build clean, modern UIs using Tailwind CSS or lightweight vanilla HTML/JS without external script dependencies (CSP compliance).

## 2. Message Passing & Storage Sync

- Implement typed action-based message routers between content scripts and background workers:
  `chrome.runtime.onMessage.addListener((request, sender, sendResponse) => { ... return true; });`
- Use `chrome.storage.sync` for user settings (synced across signed-in browsers) and `chrome.storage.local` for large cached datasets.
