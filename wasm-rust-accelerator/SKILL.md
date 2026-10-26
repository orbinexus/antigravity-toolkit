---
name: wasm-rust-accelerator
description: Accelerates compute-heavy web browser operations using WebAssembly (Wasm) compiled from Rust with zero-copy memory buffers.
---

# WebAssembly & Rust In-Browser Accelerator

This skill guides compiling Rust algorithms to WebAssembly (`wasm-pack`, `wasm-bindgen`) to execute compute-intensive tasks at near-native CPU speeds inside browser tabs.

## 1. Rust to Wasm Architecture

1. **When to Offload to Wasm**:
   - Heavy image/video frame processing, cryptographic hashing, compression algorithms, spatial physics simulations, and audio DSP.
2. **Zero-Copy Memory Transfers**:
   - Pass shared `Uint8Array` views directly into Wasm linear memory (`WebAssembly.Memory`) to avoid expensive serialization/deserialization across the JS-Wasm boundary.
3. **Web Worker Offloading**:
   - Instantiate Wasm modules inside dedicated Web Workers (`new Worker(...)`) to keep the browser main thread and UI responsive at a steady 60fps/120fps.
