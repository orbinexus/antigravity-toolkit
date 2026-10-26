---
name: multi-agent-dev-team
description: Orchestrates autonomous multi-agent software swarms, separating specialized roles into Designer, Backend Implementer, and Security/QA Reviewer.
---

# Multi-Agent Autonomous Development Swarm

This skill guides the decomposition of complex software initiatives across specialized, autonomous AI subagents working concurrently.

## 1. Tri-Agent Swarm Topology

1. **Role 1: Architecture & UI Designer**:
   - Focuses on user journey, component state boundaries, Tailwind CSS layouts, and UX feedback.
2. **Role 2: Backend & Systems Engineer**:
   - Focuses on database schema design, transactional integrity, async APIs, and query optimization.
3. **Role 3: Security & Quality Auditor**:
   - Reviews the work of Agents 1 & 2 for OWASP vulnerabilities, edge-case boundary failures, and race conditions before code lands.

## 2. Collaborative Handshake & Peer Review
- Agents exchange structured JSON artifacts rather than conversational chatter.
- Implementation passes to merge only when the Security & Quality Auditor emits a clean review passing all unit and regression checks.
