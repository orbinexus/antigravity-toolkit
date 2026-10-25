---
name: pdf-report-generator
description: Generates pixel-perfect, print-ready multi-page PDF reports, dynamic certificates, and branded invoices using headless browsers or HTML/CSS templates with exact page breaks.
---

# Pixel-Perfect Dynamic PDF Report Engine

This skill guides the design and procedural generation of high-resolution, multi-page vector PDF documents, analytical statements, and verifiable certificates.

## 1. Print CSS & Layout Standards

1. **Page Geometry & Margins**:
   - Explicitly define `@page` CSS rules (`size: A4 portrait` or `letter`, margins `15mm 20mm`).
2. **Page-Break Control**:
   - Prevent ugly element slicing:
     - `break-inside: avoid` / `page-break-inside: avoid` on table rows, signature blocks, and summary cards.
     - `break-before: page` for major section headers.
3. **Running Headers & Footers**:
   - Utilize CSS paged media counters: `content: "Page " counter(page) " of " counter(pages);`
   - Maintain fixed header and footer margins so table bodies flow between them without overlap.

## 2. Rendering Engines & Vector Quality
- Use headless Chromium (`playwright-pdf`, `puppeteer`) or `weasyprint` with SVG vector charts rather than raster screenshots.
- Ensure embedded fonts are subsetted and all colors match CMYK or high-contrast sRGB specs.
