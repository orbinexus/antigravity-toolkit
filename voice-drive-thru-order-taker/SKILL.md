---
name: voice-drive-thru-order-taker
description: Builds real-time conversational phone and drive-thru voice AI order-taking agents using Twilio WebSockets and Gemini Multimodal Live API.
---

# AI Phone & Drive-Thru Voice Order Taker

This skill guides the implementation of low-latency, natural conversational AI voice bots for phone-in takeaway orders and restaurant drive-thrus.

## 1. Real-Time Telephony Architecture

1. **Twilio Media Streams over WebSocket**:
   - Stream incoming telephone audio (`mu-law 8kHz`) from Twilio directly to application backend over WebSockets.
   - Resample audio to 16kHz/24kHz PCM for Gemini Multimodal Live API.
2. **Interruption & Barge-In Handling**:
   - When customer speaks while AI is describing menu options, detect voice activity immediately (VAD) and clear outgoing telephony audio buffers in sub-100ms.

## 2. Conversational Guardrails & Upselling
- Natural disambiguation: *"Did you want the spicy crispy chicken burger or the grilled chicken burger?"*
- Contextual upselling triggers: When a burger is ordered without fries/drink, prompt: *"Would you like to make that a combo meal with seasoned curly fries and a Coke for just $3 more?"*
- Final confirmation read-back: Read back itemized order cleanly before issuing POS checkout.
