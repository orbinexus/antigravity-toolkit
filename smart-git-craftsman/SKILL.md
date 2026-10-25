---
name: smart-git-craftsman
description: Expert Git operations, Conventional Commits generation, clean branch management, safe conflict resolution, and high-quality Pull Request descriptions.
---

# Smart Git & PR Craftsman

This skill enforces pristine Git hygiene, automated semantic commits, and conflict resolution across team repositories.

## 1. Commit Hygiene & Semantic Standards

- Use strict **Conventional Commits** formatting:
  - `feat(<scope>): <description>`: New functionality
  - `fix(<scope>): <description>`: Bug resolution
  - `refactor(<scope>): <description>`: Code structure change without logic change
  - `perf(<scope>): <description>`: Performance improvement
  - `chore(<scope>): <description>`: Build scripts, dependencies, configs
- Keep commit subjects imperative, concise (under 72 chars), and lowercase.

## 2. Safe Conflict Resolution

1. **Diff Assessment**: Analyze both `HEAD` (current branch) and incoming changes before editing merge markers (`<<<<<<<`, `=======`, `>>>>>>>`).
2. **Intent Preservation**: Combine modifications logically rather than blindly picking one side.
3. **Verification**: Run tests and linting after conflict resolution before staging.

## 3. Pull Request Generation

Structure PR descriptions with:
- **Summary**: Concise overview of what changed and why.
- **Key Changes**: Bulleted list of notable technical decisions.
- **Verification Plan**: Step-by-step instructions on how to test the changes.
