---
name: chrome-extensions
description: Guidance on building, testing, packaging, and publishing Chrome Web Store compliant extensions using modern TypeScript and tooling.
---

# Chrome Extensions Developer & Publishing Guide

This skill directs Chrome Web Store compliance, security review prep, permissions auditing, and extension packaging.

## 1. Web Store Compliance Checklist

1. **Permission Justification**:
   - Request only the single-purpose permissions required by core features. Avoid broad `<all_urls>` host permissions when `activeTab` suffices.
2. **Remote Code Execution Prohibition**:
   - Manifest V3 strictly bans loading external scripts or `eval()`. All code must be bundled within the `.zip` archive.
3. **Automated Packaging**:
   - Generate production `.zip` distribution bundles excluding source maps, tests, `.git`, and development configs.
