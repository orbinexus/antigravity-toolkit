---
name: owasp-security-audit
description: Comprehensive security auditing, OWASP Top 10 vulnerability scanning, secret detection, and code refactoring for secure coding standards. Use this skill when reviewing code for security risks, sanitizing inputs, auditing authentication/authorization logic, or securing APIs.
---

# OWASP Security Audit & Secure Code Review

This skill equips the agent to perform in-depth security audits, vulnerability scanning, and secure code refactoring across web applications, APIs, and microservices.

## 1. Core Audit Methodology

When auditing any codebase or pull request:
1. **Threat Modeling & Attack Surface Identification**: Map all public endpoints, file uploads, authentication handlers, external API calls, and raw database queries.
2. **Automated Static Scanning**: Search for known insecure patterns (e.g., hardcoded credentials, unparameterized queries, permissive CORS, weak cryptography).
3. **OWASP Top 10 Alignment**: Cross-reference findings against the OWASP Top 10 vulnerabilities.
4. **Actionable Remediation**: Provide concrete, drop-in replacement code for identified vulnerabilities rather than theoretical advice.

---

## 2. OWASP Top 10 Vulnerability Checklist

### A01: Broken Access Control
- [ ] Ensure role-based access control (RBAC/ABAC) is enforced on every endpoint, not just hidden in the frontend UI.
- [ ] Prevent Insecure Direct Object References (IDOR): Always verify the current authenticated user owns or has rights to the requested resource ID.
- [ ] Disallow directory traversal (`../` path traversal in file handling).

### A02: Cryptographic Failures
- [ ] No hardcoded passwords, private keys, API secrets, or JWT secret strings in version control.
- [ ] Use modern hashing algorithms with salt (e.g., Argon2, bcrypt, PBKDF2) for passwords; never MD5 or SHA-1.
- [ ] Enforce TLS 1.3/HTTPS, secure cookie flags (`HttpOnly`, `Secure`, `SameSite=Strict/Lax`).

### A03: Injection (SQL, NoSQL, Command, LDAP)
- [ ] Mandatory parameterized queries / prepared statements for all database interactions.
- [ ] Never concatenate user inputs directly into shell commands (`exec`, `system`, `child_process.exec`, `os.system`).
- [ ] Context-aware output encoding to eliminate Cross-Site Scripting (XSS).

### A04: Insecure Design & Business Logic Flaws
- [ ] Implement rate limiting, throttling, and anti-abuse mechanisms on login, registration, and reset password endpoints.
- [ ] Prevent race conditions (e.g., double-spending, inventory decrement) using atomic database transactions.

### A05: Security Misconfiguration
- [ ] Debug mode (`DEBUG=True`) and verbose stack traces must be disabled in staging/production.
- [ ] Set strict HTTP security headers:
  - `Content-Security-Policy` (CSP)
  - `X-Frame-Options: DENY`
  - `X-Content-Type-Options: nosniff`
  - `Strict-Transport-Security` (HSTS)
- [ ] Avoid wildcard CORS (`Access-Control-Allow-Origin: *`) on authenticated endpoints.

### A06: Vulnerable and Outdated Components
- [ ] Check dependency trees (`npm audit`, `pip audit`, `cargo audit`) for known CVEs.
- [ ] Pin exact versions or lockfiles (`package-lock.json`, `poetry.lock`, etc.).

### A07: Identification and Authentication Failures
- [ ] Implement multi-factor authentication (MFA) where feasible.
- [ ] Invalidate sessions on password change or logout.
- [ ] Use constant-time comparisons (`crypto.timingSafeEqual`, `hmac.compare_digest`) for token/signature checks to avoid timing attacks.

### A08: Software and Data Integrity Failures
- [ ] Reject untrusted deserialization (e.g., Python `pickle.loads`, unsafe YAML loaders like `yaml.load` without `SafeLoader`).
- [ ] Validate integrity hashes on external scripts and webhooks.

### A09: Security Logging and Monitoring Failures
- [ ] Log critical security events (login failures, privilege escalation, suspicious requests).
- [ ] **Sanitize logs**: Never log passwords, access tokens, PAN/credit card details, or PII.

### A10: Server-Side Request Forgery (SSRF)
- [ ] Validate and allowlist external URLs before fetching resources from internal network or user-supplied endpoints.
- [ ] Block requests targeting loopback addresses (`127.0.0.1`, `localhost`) or internal metadata endpoints (`169.254.169.254`).

---

## 3. Standard Audit Output Template

When reporting findings, present them in this clear format:

```markdown
### 🚨 Finding: [Vulnerability Name] ([Severity: Critical | High | Medium | Low])
- **File**: `path/to/file.ext` (Line XX)
- **Vulnerability**: Clear explanation of the flaw and exploit scenario.
- **OWASP Category**: [e.g., A03: Injection]
- **Vulnerable Code**:
```code
...
```
- **Remediated Code**:
```code
...
```
```
