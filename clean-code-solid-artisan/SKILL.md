---
name: clean-code-solid-artisan
description: Refactors code to adhere strictly to SOLID principles, DRY, KISS, cognitive complexity limits, and self-documenting clean code standards.
---

# Clean Code & SOLID Principles Artisan

This skill directs the systematic refactoring of code into clean, highly readable, modular, and maintainable software following industry best practices.

## 1. SOLID Engineering Principles

1. **Single Responsibility Principle (SRP)**:
   - Each function, class, or module must have exactly one reason to change.
   - Limit functions to at most 20-30 lines of focused logic; extract auxiliary tasks (logging, validation, formatting) into separate helpers.
2. **Open/Closed Principle (OCP)**:
   - Software entities should be open for extension, but closed for modification.
   - Utilize strategy patterns, polymorphism, or dependency injection rather than cascading `switch` / `if-else` ladders.
3. **Liskov Substitution Principle (LSP)**:
   - Subtypes must be substitutable for their base types without altering program correctness.
4. **Interface Segregation Principle (ISP)**:
   - Clients should not be forced to depend upon interfaces they do not use. Prefer small, cohesive interfaces.
5. **Dependency Inversion Principle (DIP)**:
   - High-level modules must not depend on low-level modules; both must depend on abstractions (interfaces).

## 2. Clean Code Discipline
- **Cognitive Complexity**: Keep cyclomatic complexity under 8 per function. Flatten nested logic using early returns / guard clauses.
- **Descriptive Naming**: Variables and functions must reveal intent without requiring explanatory comments.
