---
name: doc-intelligence-rag
description: Extracts, parses, and synthesizes structured data, tables, key metrics, and insights from complex PDFs, technical manuals, contracts, and documents.
---

# Document Intelligence & Deep Data Extraction

This skill equips the agent to accurately process, extract, and synthesize critical information from long or complex documents, PDFs, specifications, and reports.

## 1. Extraction Strategy

1. **Document Structure Mapping**:
   - Identify headers, sections, appendices, tables, and footers.
   - For multi-column or formatted PDFs, preserve the logical reading order.
2. **Tabular Data Recovery**:
   - Extract raw tables and convert them into structured Markdown tables, CSV, or typed JSON schemas.
   - Ensure numerical accuracy (currencies, percentages, totals, dates).
3. **Cross-Referenced Querying**:
   - Map relationships between disparate sections (e.g. definitions in Section 1 matching usage in Section 8).
   - Flag conflicting clauses, ambiguities, or missing information explicitly.

## 2. Output Formatting
- Provide clean, reproducible summaries with exact page/section citations.
- When generating structured data, output validated JSON matching explicit schema definitions.
