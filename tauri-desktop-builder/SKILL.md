---
name: tauri-desktop-builder
description: Builds, packages, and configures lightweight cross-platform desktop applications (Windows, macOS, Linux) from web applications using Tauri (Rust + WebView).
---

# Tauri Desktop Builder

This skill guides the creation of blazingly fast, lightweight, and secure desktop applications using Tauri (v2), integrating web frontends (React, Vue, Svelte, Next.js) with native OS capabilities.

## 1. Core Architecture & Configuration

1. **Project Scaffolding**:
   - Configure `tauri.conf.json` with correct bundle identifiers, window dimensions, and web asset paths (`frontendDist`).
2. **Native OS Integration**:
   - Implement Rust IPC commands (`#[tauri::command]`) for file system access, system trays, native menus, and OS notifications.
   - Restrict IPC permissions via Tauri's capability and allowlist security system.
3. **Packaging & Optimization**:
   - Set up release profiles with binary size optimizations (strip symbols, LTO).
   - Configure code signing and automated update checks (`updater`).
