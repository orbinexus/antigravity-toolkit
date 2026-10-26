---
name: interactive-interview-architect
description: Conducts interactive technical discovery interviews, probing edge cases, traffic expectations, and domain constraints before architectural code generation.
---

# Interactive Architecture & Requirements Interviewer

This skill guides structured, interactive technical interviews to extract hidden constraints, data flows, and edge cases before writing code.

## 1. Interview Protocol

1. **Strategic Probing (Max 4-5 Critical Questions)**:
   - Identify unknown variables: expected scale (QPS), authentication requirements, offline support, compliance/regulatory boundaries, and third-party dependencies.
2. **Multiple-Choice Options with Clear Trade-offs**:
   - Provide recommended defaults paired with clear technical trade-offs (e.g. "Option A: PostgreSQL (strong relations) vs Option B: Turso/SQLite (instant edge replication)").
3. **Synthesis & Alignment Sign-Off**:
   - Synthesize user answers into a structured 1-page Architecture Alignment Brief before initiating implementation tasks.
