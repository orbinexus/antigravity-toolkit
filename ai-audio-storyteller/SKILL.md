---
name: ai-audio-storyteller
description: Scripts, orchestrates, and structures multi-speaker AI podcasts, audio dramas, sound effects (SFX), and multi-voice generation pipelines using TTS and audio layering.
---

# AI Multi-Voice Podcast & Audio Drama Studio

This skill directs the generation of conversational multi-speaker audio dramas, technical debates, podcast episodes, and sound effects layering pipelines.

## 1. Dialogue & Flow Architecture

1. **Natural Dialogue Dynamics**:
   - Write realistic conversational rhythms: include natural micro-interruptions, agreement tokens (`[sighs]`, `[laughs]`, `hmm`, `right`), and varying sentence cadences.
   - Avoid monotonous alternating paragraphs; create fast back-and-forth exchanges.
2. **Character Voice Attribution**:
   - Define distinct speaker profiles with tone, pitch, pace, and persona instructions.
   - Attach metadata markers for target TTS engines (e.g., ElevenLabs voice IDs, OpenAI TTS voices like `alloy`, `echo`, `fable`, `onyx`, `nova`, `shimmer`).

## 2. Audio Layering & SFX Cueing

- Include timecoded audio engineering cues:
  - `[INTRO_THEME: Fade in 0:00 - Fade out 0:08]`
  - `[SFX: Ambient coffee shop background murmur - volume: -18dB]`
  - `[OUTRO_STINGER: High energy beat]`
- Generate Python scripts using `pydub` or `ffmpeg` to concatenate generated voice segments, adjust volumes, and layer background music beds seamlessly.
