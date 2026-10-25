---
name: legacy-code-refactorer
description: Modernizes legacy, messy, or monolithic codebases into modular, typed, and performant architectures without breaking existing functionality or introducing regressions.
---

# Legacy Code Refactoring & Modernization

This skill guides the safe transformation of legacy, monolithic, or unstructured code into clean, modular, maintainable, and strictly typed modern software.

## 1. Safety-First Refactoring Workflow

1. **Behavior Preservation (Regression Guard)**:
   - Identify existing behavior, edge cases, and side effects before modifying any logic.
   - Run existing test suites or write characterization tests first if coverage is missing.
2. **Modular Decomposition**:
   - Break large monolithic files (500+ lines) into focused, single-responsibility modules.
   - Separate business logic from I/O, UI, and database queries.
3. **Typing & Modern Idioms**:
   - Replace untyped JavaScript with TypeScript (`strict: true`).
   - Replace callbacks and promise chains with structured `async/await` and robust `try/catch/finally`.
   - Replace deprecated APIs, globals, and mutation patterns with immutable state and pure functions where possible.
4. **Step-by-Step Verification**:
   - Refactor in small, discrete steps rather than one massive rewrite.
