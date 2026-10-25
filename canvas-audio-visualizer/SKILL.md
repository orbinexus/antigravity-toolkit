---
name: canvas-audio-visualizer
description: Builds real-time audio visualizers, reactive neon particles, FFT spectrum analyzers, and generative fluid canvas art using HTML5 Canvas and the Web Audio API.
---

# Generative Canvas & Real-Time Audio Visualizer

This skill guides the creation of mesmerizing, GPU-efficient audio spectrum analyzers, neon waveforms, reactive fluid particles, and interactive generative visualizers.

## 1. Web Audio Pipeline Architecture

1. **Audio Node Graph**:
   - `AudioContext` -> `MediaElementAudioSourceNode` (or `getUserMedia` microphone) -> `AnalyserNode` -> `AudioDestinationNode`.
   - Configure `analyser.fftSize` (typically 512, 1024, or 2048) and `analyser.smoothingTimeConstant` (0.8 - 0.85) for silky frequency response.
2. **Frequency & Time-Domain Data**:
   - Extract frequency data via `analyser.getByteFrequencyData(dataArray)` for bass/mid/treble energy.
   - Extract waveform data via `analyser.getByteTimeDomainData(dataArray)` for oscilloscope line renderings.

## 2. Canvas Rendering Best Practices

- Use `requestAnimationFrame` render loops with timestamp delta timing.
- Apply alpha trail trails (`ctx.fillStyle = 'rgba(10, 10, 15, 0.15)'` before `fillRect`) for neon glow retention and trailing ghost effects.
- Separate bass frequencies to drive dynamic radial pulses and particle emission explosions.
