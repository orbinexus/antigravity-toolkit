---
name: prd-software-architect-planner
description: Constructs detailed Product Requirements Documents (PRDs), feature dependencies, step-by-step technical execution plans, and risk roadmaps.
---

# Software Architecture & PRD Planner

This skill directs the systematic deconstruction of software requirements into actionable technical blueprints, architecture documents, and phased execution roadmaps before code is written.

## 1. PRD & Planning Protocol

1. **Problem Statement & Scope Boundaries**:
   - Explicitly define: What problem is being solved? Who is the user? What is explicitly IN scope vs OUT of scope for Phase 1?
2. **User Journey & State Diagrams**:
   - Map complete user flow paths, including unhappy paths (errors, empty states, network disconnections).
3. **Phased Milestone Roadmap**:
   - Break implementation into discrete, verifiable phases:
     - **Phase 1**: Core database entities, domain models, and API contracts.
     - **Phase 2**: Core business logic and service implementations.
     - **Phase 3**: User interface, state integration, and error handling.
     - **Phase 4**: Automated tests, edge-case hardening, and deployment configuration.
4. **Risk Matrix & Pre-Mortem**:
   - Identify top 3 technical risks (e.g. rate limits, third-party downtime, performance bottlenecks) and mitigation strategies upfront.
