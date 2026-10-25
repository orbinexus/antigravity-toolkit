---
name: google-antigravity-sdk
description: Builds multi-agent autonomous coding systems, custom agent tools, hooks, and sidecars using the Google Antigravity SDK.
---

# Google Antigravity SDK & Multi-Agent Architecture

This skill guides the construction, customization, and orchestration of autonomous agent swarms, lifecycle hooks, and tool integrations using the Antigravity SDK.

## 1. Multi-Agent Delegation

1. **Subagent Orchestration**:
   - Define domain-focused subagent roles (`define_subagent`) with scoped tool access (read-only research vs full write/exec).
   - Dispatch autonomous subtasks asynchronously without blocking the parent coordinator's decision loop.
2. **Lifecycle Hooks**:
   - Register event listeners in `hooks.json` to execute pre-commit validations, automated tests, or telemetry before and after agent tool invocations.
