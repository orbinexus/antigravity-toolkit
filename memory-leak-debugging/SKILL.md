---
name: memory-leak-debugging
description: Tracks down client and Node.js memory leaks, retained DOM elements, unclosed event listeners, and closure retainers using Chrome Heap Snapshots.
---

# JavaScript & Node.js Memory Leak Debugger

This skill guides forensic investigation of monotonic heap growth, zombie DOM nodes, and dangling event listeners.

## 1. Heap Snapshot Comparison Protocol

1. **Three-Snapshot Technique**:
   - Snapshot 1: Baseline before user action.
   - Snapshot 2: Execute target flow (e.g. open/close heavy modal or dashboard).
   - Snapshot 3: Execute flow again and force Garbage Collection (GC).
   - Filter Snapshot 3 by "Objects allocated between Snapshot 1 and 2".
2. **Common Leak Culprits**:
   - **Detached DOM Trees**: Elements removed from DOM but still referenced in JavaScript variables or arrays.
   - **Forgotten Event Listeners**: `window.addEventListener` or `element.on(...)` without corresponding cleanup on unmount (`useEffect` return cleanup).
   - **Uncleared Timers**: `setInterval` holding references to outer scope closures.
