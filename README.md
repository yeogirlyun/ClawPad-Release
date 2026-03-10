<p align="center">
  <img src="https://www.clawpad.ai/logo.png" alt="ClawPad Logo" width="180">
</p>

<h1 align="center">ClawPad</h1>

<p align="center">
  <strong>Local-First AI Workspace + Production Remote API Platform</strong>
</p>

<p align="center">
  <strong>License:</strong> Free for personal, business, and commercial use. Remote API is included and free.
</p>

<p align="center">
  <a href="https://github.com/yeogirlyun/ClawPad-Release/releases/latest">
    <img src="https://img.shields.io/github/v/release/yeogirlyun/ClawPad-Release?style=for-the-badge&color=0ea5e9" alt="Latest Release">
  </a>
  <a href="https://www.clawpad.ai">
    <img src="https://img.shields.io/badge/Product-clawpad.ai-blue?style=for-the-badge" alt="Website">
  </a>
  <a href="https://www.clawpad.ai/api/">
    <img src="https://img.shields.io/badge/API_Portal-Developer_Docs-green?style=for-the-badge" alt="API Portal">
  </a>
  <a href="https://github.com/yeogirlyun/ClawPad-Release/releases/latest">
    <img src="https://img.shields.io/badge/Platform-macOS-lightgrey?style=for-the-badge&logo=apple" alt="macOS">
  </a>
</p>

---

## What This Repository Provides

This is the official distribution and release-note repository for ClawPad.

- signed and notarized macOS release artifacts
- versioned release summaries
- version-matched API documentation bundle

For product walkthroughs and downloads: [clawpad.ai](https://www.clawpad.ai)

---

## Velvet Lattice Architecture

ClawPad is built on the **Velvet Lattice** — a vertically integrated architecture where model intelligence, app runtime, interface rendering, data persistence, and API surface are woven into a single coherent platform.

What this makes possible:

- **Natural language to problem-solving apps at scale** — describe what you need, and the platform produces working applications with real backends, specialized UIs, and full API access.
- **Automatic app evolution** — apps continuously gain new features and competitive parity improvements through platform-level processes. An app that ships with basic capabilities today grows to match market leaders without manual intervention.
- **Massive-scale UI improvement** — every app receives a domain-specialized interface (data tables for finance, message streams for communication, canvas layouts for creative tools) generated and refined at platform scale rather than hand-built one at a time.
- **Intelligent model management** — the platform monitors AI provider health in real time and automatically routes through the best available model. If a provider goes down, your workflow continues on the next best option without interruption.
- **Self-verifying releases** — thousands of automated tests validate every release end-to-end with zero human interaction, ensuring production quality across the entire app ecosystem.

The result: **123 apps** ship as a single integrated product — each with a REST API, web UI, and full AI operability — and the platform keeps improving all of them simultaneously.

---

## Core Capabilities

### 123-App Ecosystem
95 user-facing apps spanning productivity, finance, creative, developer tools, health, education, and more. Every app has a REST API, a browser-based UI, and an AI-operable interface. Apps are continuously expanded toward competitive feature parity with market leaders.

### Intelligent Model Routing
Seamless AI model management across cloud and local providers. Real-time health monitoring with automatic recovery. If one provider goes down, the platform cascades through alternatives — cloud, other providers, local models — with zero user intervention.

### Platform-Scale Manufacturing
The platform can analyze competitive landscapes, identify feature gaps, design new capabilities, and implement them across dozens of apps in a single pass. This is how 30+ apps grew from minimal feature sets to 84-86% competitive parity with market leaders.

### Domain-Specialized Interfaces
Each app gets a UI matched to its domain — not a generic template. Eight distinct layout archetypes cover the full range from data-heavy spreadsheets to freeform creative canvases, with domain-specific widgets and interaction patterns.

### Agent Jobs + Automation
Durable autonomous workflows with timeline-backed visibility. Create, schedule, monitor, and manage multi-step AI-driven jobs through both the desktop interface and the REST API.

### MCP Extension Ecosystem
Full extension lifecycle — discover, install, configure, run, monitor, and update. Production-grade health visibility and failure handling for reliable integrations.

### Remote API Platform
Complete programmatic control over everything ClawPad does. Application operations, automation, AI orchestration, extension management, and system observability — all through authenticated REST endpoints.

### Secure Local-First Design
All data stays on your machine. Encrypted credential storage. Authenticated API surfaces. Apple Developer ID signed and notarized distribution.

---

## API Developer Portal

<p align="center">
  <a href="https://www.clawpad.ai/api/">
    <strong>www.clawpad.ai/api</strong>
  </a>
</p>

The API portal is the primary resource for developers building on ClawPad. It provides:

- **Interactive endpoint browser** — explore every REST endpoint across all 123 apps with parameter schemas and example requests
- **Per-app OpenAPI specs** — full machine-readable specifications for each app (JSON format), ready for code generation
- **Getting started guide** — authentication setup, first API call, and SDK quickstart
- **Headless mode docs** — run ClawPad without a GUI as a pure API server for automation and CI/CD pipelines
- **Orchestration guide** — build multi-step AI workflows that chain app operations together
- **Python SDK reference** — native Python client for all ClawPad APIs

### What you can build with the API

- **Custom dashboards** that pull data from multiple ClawPad apps
- **Automation pipelines** — trigger app operations from external systems via webhooks
- **AI agent integrations** — let AI models operate ClawPad apps through the standard REST interface
- **Headless batch processing** — run ClawPad as a backend service for scheduled tasks
- **Channel bots** — connect ClawPad capabilities to Telegram, Discord, Slack, LINE, or WhatsApp

### Quick links

| Resource | URL |
|----------|-----|
| API Portal Home | [www.clawpad.ai/api](https://www.clawpad.ai/api/) |
| Getting Started | [www.clawpad.ai/api/getting-started](https://www.clawpad.ai/api/getting-started) |
| Headless Mode | [www.clawpad.ai/api/headless](https://www.clawpad.ai/api/headless) |
| Orchestration | [www.clawpad.ai/api/orchestration](https://www.clawpad.ai/api/orchestration) |
| Python SDK | [www.clawpad.ai/api/sdk](https://www.clawpad.ai/api/sdk) |
| OpenAPI Specs | [www.clawpad.ai/api/specs](https://www.clawpad.ai/api/) (per-app JSON) |

---

## Technology Footprint

- **Desktop:** native macOS application (Apple Silicon + Intel via Rosetta)
- **Local AI:** local-first runtime with support for open-weight models
- **API:** REST/JSON endpoints, WebSocket event streams, webhook ingress
- **Extensions:** MCP-based extension ecosystem
- **Data:** local SQLite persistence with full-text search
- **Security:** authenticated API surface, encrypted credential storage
- **Distribution:** Apple Developer ID signed, notarized, and checksum verified

---

## Installation

1. Download the latest DMG from [Releases](https://github.com/yeogirlyun/ClawPad-Release/releases/latest)
2. Double-click ClawPad.app to install (self-installs to Applications)
3. Configure your AI provider and start using

---

## License and Usage

Free for personal, business, and commercial use. Remote API usage is included and free.

---

## Links

- Product: [clawpad.ai](https://www.clawpad.ai)
- API Portal: [clawpad.ai/api](https://www.clawpad.ai/api/)
- Releases: [github.com/yeogirlyun/ClawPad-Release/releases](https://github.com/yeogirlyun/ClawPad-Release/releases)
- API Docs (bundled): [api-docs/current](./api-docs/current/)
- Feedback: [ClawPad YouTube Community](https://www.youtube.com/@clawpad-ai/community)

---

*ClawPad is proprietary software. This repository distributes official release artifacts and documentation.*
