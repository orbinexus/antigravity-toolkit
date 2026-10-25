---
name: gemini-live-api-dev
description: Implements bidirectional, real-time audio and video streaming using Gemini Multimodal Live API over WebSockets for low-latency conversational agents.
---

# Gemini Multimodal Live API Developer Guide

This skill guides the construction of real-time conversational agents, bidirectional audio streaming, and webcam screen inspection using the Gemini Multimodal Live API over WebSockets.

## 1. WebSocket Protocol & Session Setup

1. **Bidirectional Stream Handshake**:
   - Establish secure WebSocket connection to Gemini Live endpoint with API key and session configuration (`response_modalities: ["AUDIO"]`).
2. **Audio Input & Output Format**:
   - Stream user microphone audio as raw PCM 16-bit, 16kHz or 24kHz little-endian audio chunks (`audio/pcm`).
   - Receive server audio chunks and play back via Web Audio API `AudioContext` with continuous buffer queuing.
3. **Turn-Taking & Interruption Handling**:
   - Handle server `interrupted` event messages: immediately mute active audio output buffers when user starts speaking.
