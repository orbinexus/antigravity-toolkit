---
name: troubleshooting
description: Systematic troubleshooting runbook for DevTools disconnects, headless browser timeouts, proxy stalls, and local runtime crashes.
---

# Web & Local Runtime Troubleshooting Runbook

This skill directs root-cause diagnosis when dev servers, local tunnels, browser debug ports, or background processes hang or fail unexpectedly.

## 1. Port & Process Contention

1. **Port Conflicts**:
   - Identify conflicting PIDs occupying required ports (`netstat -ano | findstr :<port>` on Windows, `lsof -i :<port>` on Unix).
   - Kill dangling orphaned background instances gracefully before force-killing.
2. **Zombie Chrome / Headless Processes**:
   - Check Task Manager for orphaned `chrome.exe` processes holding lockfiles in User Data directories.
3. **Environment & Cache Corruption**:
   - Clear corrupted local bundler caches (`.next/cache`, `node_modules/.cache`, Vite temp dirs) when encountering unexplained module build panics.
