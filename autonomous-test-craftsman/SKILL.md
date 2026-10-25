---
name: autonomous-test-craftsman
description: Generates exhaustive unit, integration, and property-based test suites, hunting hidden edge cases, boundary failures, concurrency races, and error states.
---

# Autonomous Test Craftsman & Edge-Case Hunter

This skill constructs robust, zero-flakiness automated test suites designed to catch silent regressions, null-pointer dereferences, and boundary failures before release.

## 1. Test Suite Generation Strategy

1. **Boundary & Malformed Input Testing**:
   - Empty collections, massive strings (overflow/truncation), negative integers, zero values, extreme floating-point precision, leap years, timezone offsets, special Unicode characters (emojis, RTL, null bytes).
2. **State & Concurrency Verification**:
   - Double-clicks, out-of-order responses, network timeouts, duplicate event payloads, optimistic lock conflicts.
3. **Mocking & Isolation**:
   - Mock external I/O (payment gateways, third-party APIs, disk writes) cleanly using deterministic test doubles.
   - Never mock internal domain models or core business validation logic.

## 2. Test Execution & Reporting
- Use standard test runners: Jest / Vitest for JavaScript/TypeScript, PyTest for Python, Go testing for Go.
- Structure tests with clear **Arrange - Act - Assert** (AAA) or **Given - When - Then** blocks.
- Generate assertion messages that state exactly what failed and why.
