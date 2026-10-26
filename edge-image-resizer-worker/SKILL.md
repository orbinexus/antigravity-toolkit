---
name: edge-image-resizer-worker
description: Builds real-time on-the-fly image resizing, format negotiation (WebP/AVIF), and edge caching using Cloudflare Workers without dedicated backend infrastructure.
---

# Cloudflare Edge Dynamic Image Resizer

This skill guides the construction of zero-infrastructure, on-the-fly image transformation and optimization pipelines running entirely at the edge.

## 1. Edge Transformation Pipeline

1. **Request Interception & Query Parsing**:
   - Intercept requests matching `/cdn-cgi/image/w={width},q={quality},f={format}/*` or custom query parameters (`?w=400&q=80`).
   - Validate requested dimensions against an allowlist to prevent cache-busting denial-of-service attacks.
2. **Accept-Header Format Negotiation**:
   - Inspect incoming `Accept` headers to serve AVIF to modern browsers, falling back to WebP or JPEG.
3. **Edge Caching**:
   - Cache transformed image buffers in Cloudflare Cache API (`caches.default`) with immutable cache-control headers (`s-maxage=31536000`).

## 2. Source Fetching & Security
- Fetch raw source assets from origin object storage (R2/S3) with signed authorization headers.
- Block hotlinking by verifying `Referer` or signed token HMAC parameters on external domains.
