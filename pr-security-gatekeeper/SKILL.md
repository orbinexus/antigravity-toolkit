---
name: pr-security-gatekeeper
description: Automates CI/CD security gating on Pull Requests, scanning for leaked secrets, high-severity CVEs, license compliance violations, and unsafe dependencies.
---

# Automated PR Security & License Gatekeeper

This skill configures automated security gating in CI/CD pipelines (GitHub Actions) to intercept vulnerabilities, secret leaks, and license violations before merging.

## 1. Automated Security Checks

1. **Secret & Key Leak Detection**:
   - Run automated regex and entropy scans (TruffleHog / Gitleaks) across all incoming commit diffs.
   - Automatically fail builds if unencrypted API keys, AWS secrets, or private certificates are detected.
2. **Dependency Vulnerability Audits**:
   - Run automated dependency vulnerability audits (`npm audit --audit-level=high`, `pip-audit`, `cargo audit`).
   - Block merges if any dependencies contain exploitable Critical or High CVEs without an approved waiver.
3. **Copyleft License Compliance**:
   - Reject PRs introducing viral copyleft dependencies (GPL/AGPL) into proprietary commercial code repositories.

## 2. Bot Comments & PR Status Checks
- Post clear markdown summaries as PR comments detailing offending lines, CVE numbers, and recommended version upgrades.
- Set strict GitHub Branch Protection Rules requiring the security gatekeeper status check to pass before merge.
