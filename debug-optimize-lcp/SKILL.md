---
name: debug-optimize-lcp
description: Diagnoses and optimizes Largest Contentful Paint (LCP), eliminating render-blocking resources, preloading hero assets, and reducing server TTFB.
---

# LCP & Core Web Vitals Optimization

This skill guides the detection, profiling, and remediation of slow Largest Contentful Paint (LCP) times to meet Google's < 2.5s good threshold.

## 1. LCP Element Breakdown

1. **Element Identification**:
   - Inspect Chrome Performance panel for the `LCP` timing flag (hero image, video poster, large text block, background image).
2. **Sub-Part Timing Diagnosis**:
   - **TTFB (Time to First Byte)**: Target < 800ms via edge caching and database query optimization.
   - **Resource Load Delay**: Time between page start and browser requesting the hero asset. Eliminate lazy loading on hero images (`loading="eager"`, `fetchpriority="high"`).
   - **Resource Load Time**: Compress hero images with AVIF/WebP, responsive `srcset`, and modern CDN delivery.
   - **Element Render Delay**: Remove render-blocking stylesheets and un-inlined critical CSS.
