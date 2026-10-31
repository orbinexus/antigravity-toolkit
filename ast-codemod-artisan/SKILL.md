---
name: ast-codemod-artisan
description: Automates large-scale syntax-safe refactoring, API migrations, and codebase transformations using Abstract Syntax Trees (AST) and jscodeshift.
---

# Abstract Syntax Tree (AST) & Codemod Artisan

This skill directs syntax-safe, automated code refactoring across massive repositories using Abstract Syntax Tree (AST) manipulations rather than fragile string regex replacements.

## 1. AST Parsing & Safe Transformation

1. **AST Representation**:
   - Parse source files into structured AST nodes (Babel / TypeScript / Python AST parsers).
   - Manipulate precise syntactic nodes (`ImportDeclaration`, `CallExpression`, `JSXElement`, `FunctionDeclaration`) while preserving surrounding comments, whitespace, and formatting.
2. **Deterministic Code Transformations**:
   - Rename deprecated library imports across hundreds of files in seconds.
   - Inject required wrapper props, hooks, or error handlers without risk of broken closing tags or syntax corruptions.

## 2. Codemod Execution & Verification
- Execute transformations dry-run first (`--dry`) to audit AST diffs across affected files.
- Run typecheck and automated test suites immediately following AST codemod execution.
