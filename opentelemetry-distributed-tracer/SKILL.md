---
name: opentelemetry-distributed-tracer
description: Instruments distributed tracing, context propagation, span metrics, and Jaeger/Zipkin exporters across heterogeneous microservices using OpenTelemetry.
---

# OpenTelemetry Distributed Tracing Architect

This skill directs the end-to-end instrumentation of distributed traces, cross-service context propagation, and span lifecycle tracking across microservices.

## 1. Context Propagation Standards

1. **W3C Trace Context Standard**:
   - Propagate `traceparent` (`version-trace_id-parent_id-trace_flags`) and `tracestate` across HTTP headers and message queue payloads.
   - Maintain unbroken trace continuity when switching between sync HTTP and async messaging (RabbitMQ/Kafka).
2. **Span Creation & Hierarchy**:
   - Wrap internal domain use cases, heavy database queries, and external HTTP calls in discrete child spans.
   - Record exceptions as span events (`span.record_exception(e)`) with `StatusCode.ERROR`.

## 2. Sampling Strategies & Exporters
- Use Tail-Based Sampling or Adaptive Head-Based Sampling (e.g. 5-10% of successful requests, 100% of error/slow requests) to manage telemetry storage costs.
- Export traces via OTLP gRPC (`OTEL_EXPORTER_OTLP_ENDPOINT`) to Jaeger, Grafana Tempo, or Datadog.
