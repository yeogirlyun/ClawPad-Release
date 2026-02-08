<p align="center">
  <img src="https://www.clawpad.ai/logo.png" alt="ClawPad Logo" width="180">
</p>

<h1 align="center">ClawPad</h1>

<p align="center">
  <strong>The OpenClaw Desktop Experience — Telegram-style AI Workspace</strong>
</p>

<p align="center">
  <a href="https://github.com/yeogirlyun/ClawPad-Release/releases/latest">
    <img src="https://img.shields.io/github/v/release/yeogirlyun/ClawPad-Release?style=for-the-badge&color=7c3aed" alt="Latest Release">
  </a>
  <a href="https://www.clawpad.ai">
    <img src="https://img.shields.io/badge/Website-clawpad.ai-blue?style=for-the-badge" alt="Website">
  </a>
  <a href="https://github.com/yeogirlyun/ClawPad-Release/releases/latest">
    <img src="https://img.shields.io/badge/Platform-macOS-lightgrey?style=for-the-badge&logo=apple" alt="macOS">
  </a>
  <a href="#">
    <img src="https://img.shields.io/badge/Price-Free-brightgreen?style=for-the-badge" alt="Free">
  </a>
</p>

---

## What is ClawPad?

ClawPad is a native desktop AI workspace that makes it effortless to install, manage, and use [OpenClaw Gateway](https://openclaw.ai). Think of it as **Telegram for AI** — a beautiful, organized interface where every conversation lives in its own topic with dedicated context, files, and history.

ClawPad automatically installs and manages OpenClaw Gateway, giving you seamless AI access across your desktop and every connected messaging channel (Telegram, Discord, WhatsApp, LINE, and more).

**100% Free. No subscriptions. No hidden fees.**

---

## Key Benefits

| | Benefit | Description |
|---|---------|-------------|
| 🚀 | **One-Click Setup** | ClawPad installs OpenClaw Gateway automatically. No terminal commands, no Docker, no manual configuration. |
| 🧠 | **Unified AI Memory** | Every conversation has context. ClawPad injects topic names, recent history, and relevant files into every message — your AI always knows what you're working on. |
| 📁 | **Project Isolation** | Each topic is an isolated workspace with its own history, files, and context. Work on multiple projects simultaneously without mixing context. |
| 🎨 | **Rich Workspace** | Beautiful native interface with 9 art-inspired themes (Starry Night, Klimt Golden, Monet Lilies, and more). |
| 🔄 | **Multi-Model Support** | Switch between Claude, GPT-4, Gemini, and Grok with one click. Your choice syncs globally across all connected channels. |
| 📱 | **Channel Mirrors** | Browse your Telegram, Discord, LINE, and WhatsApp conversations right inside ClawPad. |
| 💻 | **Native Performance** | Built with PyQt6 — not Electron. Fast startup, smooth scrolling, proper macOS integration. |
| 🔒 | **Local-First Privacy** | Local SQLite database, encrypted API keys, no cloud storage. Your data stays on your device. |
| 🔧 | **Full Data Control** | Database backup/restore, export conversations, manage API keys. You own everything. |
| 🧩 | **Smart Context Injection** | Configurable context modes (auto/full/minimal/off), history depth, file inclusion, and token budgets. |

---

## Features

### Core Capabilities

- **Smart Context Injection** — ClawPad's superpower. Every message includes topic name, recent history, and relevant files — the AI always knows exactly what you're working on.
- **Multi-Model Support** — Switch between Claude, GPT-4, Gemini, and Grok with one click. Your choice syncs globally.
- **Topic-Based Organization** — Each topic is an isolated workspace with its own history, files, and context.
- **Channel Mirrors** — Browse Telegram, Discord, LINE, and WhatsApp conversations inside ClawPad.
- **Parallel Conversations** — Start a chat, switch topics, and both continue streaming simultaneously.
- **File Management** — Attach files to topics. Track inputs and AI-generated outputs with version history and lineage.

### Design & Experience

- **Unified Memory** — Seamless sync across all channels via OpenClaw Gateway.
- **Private & Secure** — Local SQLite database, encrypted API keys, no cloud storage.
- **9 Art-Inspired Themes** — Starry Night, Klimt Golden, Monet Lilies, and more.
- **Native Performance** — Built with PyQt6 for fast startup and smooth scrolling.
- **Full Control** — Database backup/restore, connection management, API key configuration.
- **Code & Markdown** — Full syntax highlighting, markdown rendering, and copy buttons for code blocks.

---

## Developer Remote API

ClawPad includes a comprehensive REST API and WebSocket interface, enabling developers to build applications on top of ClawPad's rich AI conversation data.

### Why Build on ClawPad?

ClawPad isn't just a chat client — it's an **AI data platform**. Every conversation includes:

- **AI responses with full context** — model provider, model ID, streaming state, context injection metadata
- **Per-topic model switching** — each project can use a different AI model
- **Global memory and context injection** — configurable modes (auto/full/minimal/off) with token budgets
- **File lineage tracking** — which AI message generated a file, input/output file relationships, token counts
- **Real-time events** via WebSocket — message created, project updated, streaming state changes

All of this data is accessible via the Remote API for developers to build analytics dashboards, workflow automation, AI pipelines, and more.

### API Overview

| Category | Endpoints | Description |
|----------|-----------|-------------|
| 💚 Health & Status | 4 | Server health, version, app state, uptime |
| 📁 Projects | 7 | Create, list, get, update, pin, select, delete topics |
| 💬 Messages & AI | 7 | Send messages, get AI responses, export conversations |
| 📎 Files & Artifacts | 6 | Manage files with lineage tracking and token counts |
| 🔍 Search | 4 | Global search, project-scoped search, file search |
| ⚙️ Settings & Config | 2 | Get/update context injection settings, system prompts |
| 🎨 Themes | 2 | List and switch between 9 art-inspired themes |
| 🤖 AI Models | 1 | List available AI models across all providers |
| 🔌 Gateway | 3 | Connection status, reconnect, gateway info |
| 🗄️ System | 4 | Database info, backup, notifications |
| 📡 WebSocket | 1 | Real-time event streaming |

**41 endpoints** across **11 categories** — all accessible at `http://127.0.0.1:18790`

### Quick Start

```bash
# Launch ClawPad with API enabled
./ClawPad.app/Contents/MacOS/ClawPad --api

# Or run headless (no UI) for automation
./ClawPad.app/Contents/MacOS/ClawPad --stealth
```

### Example: Send a Message and Get AI Response

```bash
# Create a new topic
curl -X POST http://127.0.0.1:18790/api/projects \
  -H "Content-Type: application/json" \
  -d '{"name": "My AI Project"}'

# Send a message and wait for AI response
curl -X POST http://127.0.0.1:18790/api/projects/{project_id}/messages \
  -H "Content-Type: application/json" \
  -d '{"content": "Explain quantum computing in simple terms", "wait_for_response": true}'
```

```python
import requests

BASE = "http://127.0.0.1:18790"

# Create project
project = requests.post(f"{BASE}/api/projects", json={"name": "My AI Project"}).json()
project_id = project["data"]["id"]

# Send message with AI response
response = requests.post(
    f"{BASE}/api/projects/{project_id}/messages",
    json={"content": "Explain quantum computing", "wait_for_response": True}
).json()

print(response["data"]["content"])         # AI response text
print(response["data"]["model_provider"])  # "anthropic"
print(response["data"]["model_id"])        # "claude-sonnet-4-20250514"
```

### Built-in API Explorer

ClawPad includes a built-in **API Explorer** window accessible via the **Developer** menu (`Cmd+Shift+D`). Features include:

- Searchable endpoint browser with 11 categories
- Interactive parameter editor for path, query, and body params
- One-click request execution with response viewer
- Auto-generated cURL and Python code examples
- Live connection status monitoring with latency display
- Full theme integration (all 9 themes supported)

### Stealth Mode

Run ClawPad in headless mode for CI/CD pipelines, automation, and server-side deployment:

```bash
# Headless API-only mode
./ClawPad.app/Contents/MacOS/ClawPad --stealth --api-port 18790
```

### WebSocket Real-Time Events

```python
import asyncio
import websockets
import json

async def listen():
    async with websockets.connect("ws://127.0.0.1:18790/ws") as ws:
        await ws.send(json.dumps({"type": "subscribe", "channel": "all"}))
        async for message in ws:
            event = json.loads(message)
            print(f"Event: {event['type']} - {event.get('data', {})}")

asyncio.run(listen())
```

---

## Supported AI Models

| Provider | Models |
|----------|--------|
| **Anthropic** | Claude Sonnet 4, Claude Opus 4, Claude 3.5 Sonnet, Claude 3.5 Haiku |
| **OpenAI** | GPT-4o, GPT-4o Mini, GPT-4 Turbo, o1, o1-mini |
| **Google** | Gemini 2.0 Flash, Gemini 1.5 Pro, Gemini 1.5 Flash |
| **xAI** | Grok |

---

## Messenger Integrations

Chat with AI across all your messaging platforms — powered by OpenClaw Gateway:

| Platform | Status |
|----------|--------|
| Telegram | ✅ Supported |
| WhatsApp | ✅ Supported |
| Discord | ✅ Supported |
| LINE | ✅ Supported |
| Facebook Messenger | ✅ Supported |
| WeChat | 🔄 Coming Soon |
| Slack | 🔄 Coming Soon |
| Signal | 🔄 Coming Soon |

---

## Installation

### Requirements

- macOS 13.0 (Ventura) or later
- Apple Silicon (M1/M2/M3/M4) or Intel Mac

### Install in 3 Steps

1. **Download** — Get the latest `.dmg` from the [Releases page](https://github.com/yeogirlyun/ClawPad-Release/releases/latest)
2. **Install** — Open the DMG and drag ClawPad to your Applications folder
3. **Launch** — Open ClawPad from Applications. It will automatically set up OpenClaw Gateway on first launch.

That's it. No terminal commands, no Docker, no manual configuration.

---

## Download

📥 **[Download ClawPad (macOS)](https://github.com/yeogirlyun/ClawPad-Release/releases/latest)**

---

## Links

- 🌐 **Website:** [www.clawpad.ai](https://www.clawpad.ai)
- 📧 **Support:** support@clawpad.ai
- 🐛 **Issues:** [GitHub Issues](https://github.com/yeogirlyun/ClawPad-Release/issues)

---

*ClawPad is a proprietary application. This repository is for releases only.*

*Copyright 2024-2026 ClawPad. All rights reserved.*
