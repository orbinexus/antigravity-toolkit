---
name: codebase-architect-mapper
description: Analyzes unfamiliar or large codebases, mapping dependencies, data flows, entry points, architecture patterns, and generating Mermaid visualization diagrams.
---

# Codebase Architect & System Mapper

This skill conducts rapid forensic mapping of complex, legacy, or unfamiliar repositories to reveal architecture topology, data flow routes, and module boundaries.

## 1. Discovery & Topological Mapping

1. **Entry Point Identification**:
   - Locate runtime bootstraps (`main()`, server startup, route indexers, background workers, event consumers).
2. **Layer & Dependency Auditing**:
   - Map dependencies across UI/Controllers -> Service/Domain Logic -> Data Access/Repositories -> External Integrations.
   - Detect circular dependencies and leaky abstractions.
3. **Data Flow & State Propagation**:
   - Trace representative transactions end-to-end (e.g. HTTP Request -> Middleware -> Controller -> ORM Query -> Database -> Response).

## 2. Visual Architecture Output
- Deliver clear, high-level **Mermaid.js** diagrams (`flowchart TD` or `sequenceDiagram`) representing module coupling and request lifecycles.
- Produce a quick-start cheat sheet for developers joining the codebase (environment variables, core configs, database entities).
