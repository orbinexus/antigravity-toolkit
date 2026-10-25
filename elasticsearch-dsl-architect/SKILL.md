---
name: elasticsearch-dsl-architect
description: Crafts advanced Elasticsearch DSL queries, BM25 relevance tuning, fuzzy search, multi-match filters, and analytical aggregations.
---

# Elasticsearch Query DSL & Search Architect

This skill directs the authoring and tuning of complex Elasticsearch / OpenSearch Query DSL, full-text tokenizers, and multi-bucket aggregations.

## 1. Relevance Tuning & Query Composition

1. **Compound Queries (`bool`)**:
   - `must`: Contributes directly to relevance score (`_score`) for full-text matches (`multi_match` with cross-fields).
   - `filter`: Exact matches (`term`, `terms`, `range`) cached in bitsets for high-throughput sub-millisecond execution without scoring overhead.
   - `should`: Boosts matching documents without excluding non-matches (unless `minimum_should_match: 1`).
2. **Fuzzy & Autocomplete Search**:
   - Use `match_phrase_prefix` or edge n-gram analyzers for search-as-you-type autocomplete.
   - Tune fuzziness (`fuzziness: "AUTO"`) with `prefix_length: 2` to prevent CPU exhaustion on short query prefixes.

## 2. Aggregations & Performance
- Structure multi-level nested aggregations (`terms` -> `avg` / `date_histogram`) efficiently with `size: 0` when document hits are not needed.
- Avoid wildcard queries with leading asterisks (`*search`); leverage custom reverse or n-gram tokenizers instead.
