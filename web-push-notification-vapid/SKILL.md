---
name: web-push-notification-vapid
description: Implements zero-cost browser push notifications using VAPID protocol, web-push encryption, and Service Worker background push event handlers.
---

# Web Push Notifications (VAPID) Engine

This skill guides the implementation of native browser web push notifications without external paid third-party services.

## 1. VAPID Key Generation & Subscription Workflow

1. **VAPID Key Pair**:
   - Generate application server keys (Public/Private NIST P-256 elliptic curve keys).
2. **Client Permission & Subscription**:
   - Request permission via `Notification.requestPermission()`.
   - Subscribe via `registration.pushManager.subscribe({ userVisibleOnly: true, applicationServerKey: urlB64ToUint8Array(VAPID_PUBLIC_KEY) })`.
   - Send `PushSubscription` object (`endpoint`, `keys.p256dh`, `keys.auth`) to backend database.

## 2. Server Payload Encryption & Service Worker
- Encrypt notification payloads on backend using RFC 8291 standards (`web-push` library).
- In Service Worker, listen for `push` event:
  `self.addEventListener('push', event => { event.waitUntil(self.registration.showNotification(title, options)); });`
- Handle `notificationclick` events: focus existing open tabs or navigate to target deep links.
