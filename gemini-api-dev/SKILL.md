---
name: gemini-api-dev
description: Develops applications using Google Gemini API (Flash, Pro) with structured JSON outputs, function calling, multimodal inputs, and streaming responses.
---

# Google Gemini API Developer Guide

This skill directs integration with Google's Gemini models (Gemini 1.5/2.0 Flash, Flash-Lite, Pro) using the official Google Gen AI SDK.

## 1. Core Integration Patterns

1. **Structured Outputs with Pydantic / JSON Schema**:
   - Pass strict `response_schema` in `generation_config` to guarantee valid, parseable JSON objects without markdown fences.
2. **Function Calling & Tool Declarations**:
   - Expose native functions with clear parameter descriptions for automated model tool dispatch.
   - Handle iterative multi-turn tool calling loops with tool result messages.
3. **Multimodal Processing (Image, Audio, Video, PDF)**:
   - Upload large media files via the Gemini File API (`client.files.upload()`) rather than inlining giant base64 payloads into prompts.
