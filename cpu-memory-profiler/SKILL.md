---
name: cpu-memory-profiler
description: Diagnoses 100% CPU spikes, event loop lags, and memory heap bloat in Node.js, Python, and Go using sampling profilers and flamegraphs.
---

# CPU & Memory Profiling Specialist

This skill guides forensic bottleneck investigation when services experience runaway CPU utilization, frozen event loops, or high memory pressure.

## 1. Profiling Protocol & Flamegraph Analysis

1. **CPU Profiling & Flamegraph Inspection**:
   - Capture CPU sample traces (Node.js `--cpu-prof`, Python `cProfile` / `py-spy`, Go `pprof`).
   - Identify "wide plateaus" in flamegraphs indicating synchronous blocking operations (e.g. JSON stringify on massive arrays, synchronous regex matching, un-indexed sorting).
2. **Event Loop Lag Detection**:
   - Monitor event loop delay (`perf_hooks.monitorEventLoopDelay`).
   - Offload synchronous CPU-intensive tasks from the main event loop to worker threads (`worker_threads` / `multiprocessing`).

## 2. Memory Footprint Triage
- Measure RSS (Resident Set Size) vs Heap Used.
- Track allocation rates and garbage collection (GC) pause durations to eliminate allocation hotspots in high-frequency loops.
