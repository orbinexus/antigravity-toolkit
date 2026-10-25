---
name: pwa-offline-architect
description: Architects Progressive Web Apps (PWAs) with Workbox service workers, offline cache strategies, background sync, install prompts, and app manifest standards.
---

# Progressive Web App (PWA) & Offline Caching Architect

This skill guides the transformation of responsive web applications into installable, offline-capable Progressive Web Apps.

## 1. Web App Manifest & Installation

1. **Manifest Configuration (`manifest.webmanifest`)**:
   - Provide standard display modes (`"display": "standalone"`), theme colors, and icons (including maskable `192x192` and `512x512` PNGs).
2. **Install Prompts**:
   - Intercept the `beforeinstallprompt` event and trigger custom in-app install buttons at high-intent moments rather than intrusive auto-popups.

## 2. Service Worker Caching Strategies (Workbox)

- **Static Assets (HTML/CSS/JS/Fonts)**: Cache-First or Stale-While-Revalidate with immutable version hashes.
- **Dynamic API Responses**: Network-First with fallback to IndexedDB or CacheStorage.
- **Offline Mutations (Background Sync)**:
  - Queue failed POST/PUT mutations in IndexedDB.
  - Register a `sync` event to replay queued requests automatically when network connectivity is restored.
