# Project: OrderVox – Voice AI Order Agent

## Overview
- **Type:** Personal
- **Repo:** https://github.com/bhargavram0211/OrderVox

## Stack
- **Languages:** Python, JavaScript
- **Backend:** FastAPI, WebSockets
- **LLM & Voice:** Llama 3.2, Whisper (OpenAI STT), Piper (TTS)
- **Infrastructure:** Locally-hosted on 8GB M2 MacBook

## What It Does
A locally-hosted voice AI agent for restaurant order-taking designed to run on resource-constrained devices (8GB M2 MacBook). Implements a custom speech-to-text → LLM → text-to-speech pipeline with WebSocket-driven live transcript updates and real-time cart state management. Includes function-calling system for menu queries and handles multi-turn conversations with natural interruptions and mid-order modifications.

## Quantitative
- Runs locally on 8GB M2 MacBook (resource-efficient)
- Real-time transcript and cart updates via WebSockets
- Multi-turn conversation handling with interruption tolerance
- Custom STT→LLM→TTS pipeline

## Bullets

### DevOps/Infra Frame
**Bullet (2L):** Engineered locally-hosted voice AI agent architecture on resource-constrained hardware (8GB M2 MacBook) using FastAPI, WebSockets, and custom Whisper→Llama→Piper pipeline; optimized for real-time latency and efficient resource utilization while maintaining conversational state across multi-turn interactions.

**Bullet (1L):** Built voice AI agent on M2 MacBook; FastAPI + WebSockets, optimized for latency and resources.

### FullStack/Product Frame
**Bullet (2L):** Built OrderVox, a locally-hosted voice AI order agent using FastAPI, Whisper STT, Llama 3.2 LLM, and Piper TTS; designed function-calling system for menu queries and cart state management, handling multi-turn conversations with natural interruptions and mid-order modifications.

**Bullet (1L):** Built voice AI order agent (Whisper, Llama 3.2, Piper); handles multi-turn conversations, mid-order changes.

## Tags
fastapi, websockets, llm, voice-ai, ai, llama, whisper, piper, tts, stt, python, javascript, real-time, nlp, conversational-ai
