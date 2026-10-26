---
name: client-side-media-converter
description: Performs 100% in-browser client-side image resizing, WebP/AVIF transcoding, and video trimming using HTML5 Canvas and WebCodecs to eliminate backend compute costs.
---

# Client-Side In-Browser Media Processor

This skill guides zero-cost client-side image compression, format transcoding, and video manipulation directly inside user browsers prior to upload.

## 1. Zero-Server In-Browser Processing

1. **Client-Side Image Optimization**:
   - Draw uploaded images to an offscreen HTML5 `Canvas` or `OffscreenCanvas`.
   - Scale down dimensions to maximum required bounds (e.g. 2000px max width) with bicubic smoothing.
   - Convert to modern compressed formats (`canvas.toBlob(callback, 'image/webp', 0.85)`).
   - Reduces a 25MB DSLR photo to 400KB in 80ms on the user's CPU, cutting upload time and backend storage by 95%.
2. **Video Frame Scrubbing & Trimming**:
   - Utilize WebCodecs API and `VideoDecoder` to extract thumbnails and trim durations entirely client-side.
