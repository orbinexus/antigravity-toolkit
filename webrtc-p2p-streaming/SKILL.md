---
name: webrtc-p2p-streaming
description: Builds real-time peer-to-peer audio/video streaming, screen sharing, STUN/TURN traversal, and WebRTC data channels without dedicated media servers.
---

# WebRTC Peer-to-Peer Calling & Streaming Architect

This skill guides the design of ultra-low latency browser-to-browser audio/video calls, screen sharing, and peer data channels.

## 1. Peer Connection & Signaling Protocol

1. **Signaling Exchange**:
   - Exchange SDP offers, answers, and ICE candidates via WebSockets or SSE.
   - State machine: Handle signaling state transitions (`stable`, `have-local-offer`, `have-remote-offer`) deterministically to prevent collision glare.
2. **NAT Traversal & ICE Candidates**:
   - Configure public STUN servers for address discovery.
   - Mandate TURN server credentials (`coturn` over TLS on port 443) for symmetric NAT traversal and restrictive corporate firewalls.

## 2. Media Stream Management
- Adaptive bitrate constraints: dynamically adjust video sender track parameters (`maxBitrate`, `scaleResolutionDownBy`) based on RTCP receiver feedback (`getStats()`).
- Handle hardware device changes (`devicechange` event) for microphone/camera switching mid-call.
