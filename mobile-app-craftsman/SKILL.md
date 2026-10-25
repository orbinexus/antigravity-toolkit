---
name: mobile-app-craftsman
description: Architect, build, and optimize high-performance cross-platform mobile apps using Flutter or React Native with clean architecture, offline-first sync, and native OS integrations.
---

# Cross-Platform Mobile App Craftsman

This skill enforces production-grade mobile architecture, responsive multi-device layouts, smooth 60fps/120fps UI rendering, and robust local persistence.

## 1. Core Architecture Patterns

1. **State Management & Decoupling**:
   - For Flutter: BLoC / Cubit or Riverpod with immutable state models.
   - For React Native: Zustand or Redux Toolkit with React Query for server-state caching.
   - Strictly separate presentation UI from domain business logic and data repositories.
2. **Offline-First Persistence**:
   - Implement local database caching (Isar / Hive for Flutter, WatermelonDB / SQLite for React Native).
   - Queue outbound network mutations when offline and replay with conflict resolution upon reconnection.
3. **Native OS Integrations**:
   - Secure token storage via Keychain / KeyStore (e.g., `flutter_secure_storage` or `expo-secure-store`).
   - Native hardware APIs: Biometric authentication (FaceID/Fingerprint), background push notifications, and camera permissions.
