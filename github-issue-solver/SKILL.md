---
name: github-issue-solver
description: Analyzes repository bug reports and feature requests from GitHub issues, reproduces root causes, implements minimal regression-free fixes, and crafts comprehensive pull requests.
---

# GitHub Issue Auto-Solver & PR Specialist

This skill directs the methodical reproduction, resolution, and contribution workflow for open-source and team repository issues.

## 1. Issue Deconstruction & Triage

1. **Reproduction Test**:
   - Extract reproduction steps, expected vs actual behavior, environment specs (OS, node/python versions).
   - Author a failing test case that mirrors the reported defect before changing any implementation files.
2. **Targeted Resolution**:
   - Keep changes scoped strictly to the issue at hand; avoid unrelated refactors or formatting changes that bloat PR diffs.
   - Run linter, typecheck, and existing test suites to guarantee zero regression.
3. **Pull Request Protocol**:
   - Link the target issue with closing keywords (`Fixes #123` or `Closes #123`).
   - Provide a clear before/after explanation and manual testing checklist in the PR body.
