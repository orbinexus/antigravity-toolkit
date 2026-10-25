---
name: cdn-asset-optimizer
description: Optimizes static web assets with Brotli/Gzip compression, immutable cache-control headers, content hashing, and image formats.
---

# Edge CDN & Static Asset Optimizer

This skill directs the packaging, compression, and HTTP caching strategy for static web bundles, fonts, and media assets deployed to edge CDNs.

## 1. Caching & Content Hashing

1. **Immutable Asset Strategy**:
   - Embed cryptographic content hashes into static file names (`main.[hash].js`, `styles.[hash].css`).
   - Set ultra-aggressive cache headers on hashed assets:
     `Cache-Control: public, max-age=31536000, immutable`
2. **HTML Entry Points**:
   - Root HTML files (`index.html`) must never be cached immutably:
     `Cache-Control: no-cache, no-store, must-revalidate`

## 2. Pre-Compression & Format Upgrades
- Pre-compress static assets during build pipelines with Brotli (`.br`, quality 11) and Gzip (`.gz`, level 9).
- Convert all raster images to WebP or AVIF with responsive `srcset` and `sizes` attributes.
- Subset web fonts to only include Latin or required language glyphs, converting to `woff2` format.
