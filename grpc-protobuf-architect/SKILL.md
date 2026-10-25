---
name: grpc-protobuf-architect
description: Architects high-throughput gRPC services and Protocol Buffers schemas with bidirectional streaming, interceptors, and strict contract definitions.
---

# gRPC & Protocol Buffers Microservices Architect

This skill guides the design of low-latency, binary RPC services and strongly typed Protocol Buffers (Proto3) contracts across microservice architectures.

## 1. Proto3 Schema Standards

1. **Contract Design**:
   - Use strict field numbering (1-15 for high-frequency fields to optimize binary serialization).
   - Never renumber or reuse retired field tags (use `reserved` keyword).
   - Model request-response pairs explicitly: `<MethodName>Request` and `<MethodName>Response`.
2. **Streaming Semantics**:
   - Explicitly identify streaming patterns: Unary RPC, Server Streaming (e.g. event feeds), Client Streaming (e.g. bulk uploads), or Bidirectional Streaming (e.g. real-time sync).

## 2. Production Service Resilience
- Implement client and server interceptors for distributed tracing (OpenTelemetry context propagation), deadlines/timeouts, and authentication metadata.
- Gracefully handle gRPC status codes (`DEADLINE_EXCEEDED`, `UNAVAILABLE`, `NOT_FOUND`) with standardized error details.
