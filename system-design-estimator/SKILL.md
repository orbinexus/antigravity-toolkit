---
name: system-design-estimator
description: Formulates high-level system designs, back-of-the-envelope capacity calculations, load distribution, and microservice vs monolith architecture trade-offs.
---

# System Design & Capacity Estimator

This skill directs high-level architectural design, throughput capacity estimations, and scaling blueprints from initial launch to millions of concurrent users.

## 1. Back-of-the-Envelope Capacity Estimations

1. **Traffic & QPS**:
   - `Daily Active Users (DAU) * Actions per User / 86,400 = Average QPS`
   - `Peak QPS = Average QPS * Peak Factor (typically 2x - 3x)`
2. **Storage & Bandwidth**:
   - Calculate storage consumption per day/year including replication factors (typically 3x) and index overhead (+20%).
   - Determine ingress/egress network bandwidth requirements.

## 2. Architectural Blueprint & Component Topology
- Deliver comprehensive Mermaid diagrams outlining:
  - DNS Anycast -> Global CDN -> Layer 7 Load Balancer.
  - Stateless Application Cluster -> Distributed In-Memory Cache (Redis).
  - Primary Relational Database (Master-Replica with read replicas).
  - Asynchronous Message Bus (Kafka/RabbitMQ) -> Background Worker Consumers.
- Identify single points of failure (SPOF) and state explicit disaster recovery failover mechanics.
