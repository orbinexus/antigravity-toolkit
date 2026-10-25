---
name: terraform-iac-architect
description: Authors modular, production-grade Terraform (IaC) configurations, remote S3 state backends with DynamoDB locking, and zero-drift cloud environments.
---

# Terraform Infrastructure as Code (IaC) Architect

This skill directs the design of maintainable, secure, and modular Terraform infrastructure configurations across cloud providers (AWS, GCP, Cloudflare).

## 1. State Management & Backend Standards

1. **Remote State & State Locking**:
   - Strictly configure remote state storage (e.g. AWS S3 with KMS encryption and versioning enabled).
   - Enforce distributed state locking (e.g. AWS DynamoDB table `LockID`) to prevent concurrent applying and state corruption.
2. **Directory & Workspace Strategy**:
   - Isolate environments by directory (`environments/dev`, `environments/staging`, `environments/prod`) rather than relying solely on fragile workspace toggles.

## 2. Module Reusability & Drift Control
- Encapsulate repetitive cloud components into versioned modules (`modules/networking`, `modules/database`, `modules/compute`).
- Declare strict input variable validations (`validation { condition = ... error_message = ... }`) and explicit provider version constraints.
- Implement automated `terraform plan` checks in CI/CD before any manual or automated `apply`.
