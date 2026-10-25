---
name: skills-arsenal-loader
description: Manages, syncs, updates, and verifies local and global Antigravity skills across workspace and user configurations.
---

# Antigravity Skills Arsenal Loader & Manager

This skill manages the lifecycle, discovery checks, Git version-control sync, and verification of local and global Antigravity skills.

## 1. Skill Discovery & Health Checks

1. **Frontmatter Integrity**:
   - Ensure every `SKILL.md` contains valid YAML frontmatter with lowercase, hyphenated `name` and action-oriented `description`.
2. **Git Synchronization**:
   - Track additions and updates to `~/.gemini/config/skills/`.
   - Maintain clean Git status on the dedicated backup branch (`skills-arsenal`), pushing changes to GitHub automatically upon new skill registrations.
