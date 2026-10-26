---
name: seo-schema-rich-snippets
description: Crafts valid, Google-compliant JSON-LD structured data schemas (Product, FAQ, Breadcrumbs, Organization) to capture SERP rich snippets and boost click-through rates.
---

# SEO JSON-LD Structured Data & Rich Snippets Architect

This skill directs the generation and validation of schema.org structured data to capture enhanced Google Search results (Rich Snippets, Knowledge Panels, FAQ accordions).

## 1. High-Impact Schema Patterns

1. **Product & Pricing Schema**:
   - Provide `@type: "Product"` with embedded `offers: { "@type": "Offer", "price": "...", "priceCurrency": "...", "availability": "https://schema.org/InStock" }`.
   - Embed verified review ratings (`aggregateRating`).
2. **FAQPage Schema**:
   - Structure common user questions with `@type: "FAQPage"` and `mainEntity: [...]` containing `Question` and accepted `Answer` objects for interactive SERP dropdowns.
3. **BreadcrumbList Schema**:
   - Deliver hierarchical page trails (`itemListElement` with monotonic position indices) to replace raw URLs with clean visual site hierarchy in search snippets.

## 2. Dynamic Injection & Validation
- Render schemas inside `<script type="application/ld+json">` tags in server-rendered head elements.
- Validate JSON structures against Google's Rich Results Test requirements before production deployment.
