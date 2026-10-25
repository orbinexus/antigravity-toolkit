---
name: browser-automation-bot
description: Automates complex web interactions, multi-step portal workflows, headless form completions, and recurring file downloads using Playwright and Puppeteer.
---

# Headless Browser Task Automator

This skill directs the creation of resilient, multi-step browser automations for websites lacking public APIs (portals, government sites, banking interfaces, administrative dashboards).

## 1. Robust Automation Best Practices

1. **Deterministic Selectors**:
   - Prioritize semantic user-facing locators (`getByRole`, `getByLabel`, `getByText`) over brittle, dynamic CSS/XPath selectors.
2. **State & Session Persistence**:
   - Save authenticated browser storage state (`storageState.json`) to reuse cookies and local storage tokens across runs, avoiding redundant login flows.
3. **Download & Upload Pipelines**:
   - Intercept file download promises explicitly (`page.waitForEvent('download')`), save files to designated directories, and verify file integrity.

## 2. Error Recovery & Visual Debugging
- Automatically capture screenshots and full DOM snapshots upon unhandled locator timeouts or navigation failures.
- Implement explicit wait states (`waitForURL`, `waitForLoadState('networkidle')`) rather than hardcoded delays.
