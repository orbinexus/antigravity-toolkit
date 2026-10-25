---
name: k8s-manifest-architect
description: Authors production-grade Kubernetes YAML manifests, Helm charts, and Kustomize overlays with autoscaling, ingress, and robust health probes.
---

# Production Kubernetes & Cluster Architect

This skill guides the construction of resilient, cloud-agnostic Kubernetes manifests, Helm charts, and deployment configurations for production workloads.

## 1. Production Resource Best Practices

1. **Resource Requests & Limits**:
   - Always declare explicit `requests` and `limits` for CPU and memory to prevent OOM kills and pod eviction cascades.
2. **Health Probes**:
   - `startupProbe`: Allows slow-booting applications grace time before health evaluations.
   - `livenessProbe`: Restarts deadlocked containers.
   - `readinessProbe`: Removes pods from the service endpoint pool until they are genuinely ready to accept incoming traffic.
3. **Resilience & Rolling Updates**:
   - Configure `Deployment.spec.strategy.rollingUpdate` (`maxSurge: 25%`, `maxUnavailable: 0`) for zero downtime.
   - Set up `HorizontalPodAutoscaler` (HPA) targeting CPU and memory thresholds.
   - Define `PodDisruptionBudget` (PDB) to ensure minimum available replicas during node drains and cluster upgrades.
