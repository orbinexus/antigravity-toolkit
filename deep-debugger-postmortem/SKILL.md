---
name: deep-debugger-postmortem
description: Diagnoses cryptic runtime errors, complex stack traces, race conditions, memory leaks, and silent failures to identify root causes and generate zero-regression postmortem fixes.
---

# Deep Debugger & Root Cause Postmortem

This skill directs systematic, forensic software debugging across complex distributed systems, backend services, and asynchronous client applications.

## 1. Forensic Debugging Protocol

1. **Failure Signature & Stack Deconstruction**:
   - Trace the exact line of execution, unwinding asynchronous call stacks and promise rejections.
   - Separate symptoms (the thrown exception) from the originating defect (faulty state mutation 5 steps earlier).
2. **State & Invariant Verification**:
   - Inspect variable types, nullable fields, out-of-order execution, race conditions, and unhandled edge conditions.
   - Check resource exhaustion (file descriptors, database connection pools, memory leaks).
3. **Minimal Reproducible Reproduction**:
   - Isolate the failing logic into the smallest possible test case or isolated function call before editing production code.

## 2. Postmortem Report & Remediation Standard

When presenting fixes, deliver them in this structured format:

```markdown
### 🐛 Defect Postmortem
- **Symptom**: What failed visibly (error message/behavior).
- **Root Cause**: The underlying flaw that triggered the cascade.
- **Why It Happened**: Edge case, state mutation, or missing guard.
- **Fix (Zero Regression)**: Concrete code patch.
- **Regression Guard**: Unit test or defensive assertion to prevent reoccurrence.
```
