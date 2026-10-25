---
name: ffmpeg-media-wizard
description: Automates video compression, multi-bitrate HLS/DASH streaming packaging, audio waveform extraction, and image transformations using FFmpeg.
---

# FFmpeg Video Processing & Streaming Media Wizard

This skill guides high-performance video transcoding, streaming packaging, thumbnail extraction, and audio manipulation using FFmpeg pipelines.

## 1. Video Transcoding & Compression

1. **Two-Pass & CRF Optimization**:
   - Web standard compression using H.264 (`libx264`) or H.265 (`libx265`) with Constant Rate Factor (`-crf 23` for x264, `-crf 28` for x265) and `-preset slow` for optimal size/quality balance.
   - Set pixel format `-pix_fmt yuv420p` and move metadata to beginning of file for instant web streaming (`-movflags +faststart`).
2. **Adaptive Bitrate Streaming (HLS)**:
   - Slice source video into multiple resolutions (1080p, 720p, 480p) and generate master playlist `.m3u8` with `.ts` or fragmented `.mp4` chunks.

## 2. Thumbnail & Asset Extraction
- Extract representative keyframe thumbnails at specific timestamps or periodic intervals without decoding the entire video stream (`-ss <timestamp> -i <input> -vframes 1`).
- Generate dynamic animated WebP/GIF previews with palette generation filters.
