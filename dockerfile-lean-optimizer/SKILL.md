---
name: dockerfile-lean-optimizer
description: Optimizes and shrinks Docker containers using multi-stage builds, minimal base images (Alpine/Distroless), build cache layers, and non-root security standards.
---

# Dockerfile Lean Optimizer

This skill ensures Docker containers are minimal, secure, and blazingly fast to build and transfer.

## 1. Container Shrinking Rules

1. **Multi-Stage Builds**:
   - Separate build-time dependencies (SDKs, compilers, dev packages) from runtime artifacts.
   - Final stage must contain only compiled binaries or production node_modules/wheels.
2. **Minimal Base Images**:
   - Use `alpine`, `distroless` (GoogleContainerTools), or `slim` base images.
   - Never leave full Ubuntu or Debian developer images in production.
3. **Layer Caching Hygiene**:
   - Copy dependency manifests (`package.json`, `requirements.txt`, `go.mod`) and run installs *before* copying source code.
   - Chain `RUN` statements with `&&` and clean cache in the same layer (`rm -rf /var/lib/apt/lists/*` or `--no-cache`).
4. **Security Enforcement**:
   - Define and switch to a non-root user (`USER nonroot` or `USER node`).
   - Use `.dockerignore` to exclude `.git`, `node_modules`, `.env`, and documentation.
