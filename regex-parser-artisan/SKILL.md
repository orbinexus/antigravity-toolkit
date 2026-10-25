---
name: regex-parser-artisan
description: Crafts, optimizes, and debugs complex Regular Expressions (lookarounds, atomic groups, catastrophic backtracking prevention) for unstructured log parsing and high-throughput text extraction.
---

# Regex & Text Parsing Artisan

This skill specializes in authoring mathematically sound, high-performance regular expressions and parser state machines for high-throughput log ingestion and unstructured data mining.

## 1. Safety & Performance Principles

1. **ReDoS (Catastrophic Backtracking) Prevention**:
   - Strictly prohibit nested quantifiers (e.g. `(a+)+` or `([a-zA-Z]+)*`).
   - Use atomic groups or possessive quantifiers where supported, or anchor patterns to definite delimiters.
2. **Advanced Lookaround Constructs**:
   - Positive/Negative Lookaheads (`(?=...)`, `(?!...)`) for conditional matching without consuming characters.
   - Lookbehinds (`(?<=...)`, `(?<!...)`) for prefix extraction.
3. **Named Capture Groups**:
   - Always use named groups (`(?<fieldName>...)`) rather than numerical indexes for maintainable code.

## 2. Ingestion & Log Formatting
- Provide pre-compiled regex objects (`re.compile()` in Python, `RegExp` in JS) outside critical execution loops.
- Deliver automated unit tests testing both matching strings and negative false-positive boundaries.
