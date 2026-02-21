<p align="center">
  <img src="https://www.clawpad.ai/logo.png" alt="ClawPad Logo" width="180">
</p>

<h1 align="center">ClawPad</h1>

<p align="center">
  <strong>Local-First Native AI Workspace + Production Remote API Platform</strong>
</p>

<p align="center">
  <a href="https://github.com/yeogirlyun/ClawPad-Release/releases/latest">
    <img src="https://img.shields.io/github/v/release/yeogirlyun/ClawPad-Release?style=for-the-badge&color=7c3aed" alt="Latest Release">
  </a>
  <a href="https://www.clawpad.ai">
    <img src="https://img.shields.io/badge/Product-clawpad.ai-blue?style=for-the-badge" alt="Website">
  </a>
  <a href="https://github.com/yeogirlyun/ClawPad-Release/releases/latest">
    <img src="https://img.shields.io/badge/Platform-macOS-lightgrey?style=for-the-badge&logo=apple" alt="macOS">
  </a>
</p>

---

## What This Repository Is

This is the **official release repository** for ClawPad binaries and release assets.

- Download DMG builds
- Read release notes
- Access version-matched API docs bundles

For full product details, architecture, and user-facing workflows:

- [clawpad.ai](https://www.clawpad.ai)

---

## ClawPad at a Glance

ClawPad is a native PyQt6 desktop AI workspace with a **local-first architecture**.

- Default AI path is on-device (`local_openai`, `qwen3-4b-q4`) so users can start without cloud keys
- Hybrid routing supports local + cloud decisions with explicit confidence/gate traces
- Topic-based workspaces keep files, history, context, and model settings isolated
- Embedded OpenClaw runtime powers channels, tools, and automation
- Remote API is first-class: automation, UI control, screenshots, extensions, settings, and direct-link workflows

---

## Core Technical Achievements

These are the headline capabilities aligned with current architecture and requirements (`v0.5.2`):

1. **Local-first AI runtime (no-key start)**
   - Embedded local model workflow enabled by default
   - Cloud keys become optional, not mandatory

2. **Deterministic hybrid routing with observability**
   - Local/cloud decisions include confidence + gate trace metadata
   - Message/runtime telemetry supports reliability and optimization analysis

3. **Production Remote API platform**
   - **143 documented endpoints** + WebSocket stream
   - **15 categories**, including UI automation and extension/tool control

4. **Signed API security model**
   - `/api/*` is authenticated by default
   - Client enrollment + request signing headers documented in API auth spec

5. **Direct TLS remote mode (no hub relay dependency)**
   - Secure ticket-based pairing and direct client/server execution mode
   - Remote-server lifecycle and compatibility RPCs documented

6. **MCP extension operations + reliability controls**
   - Catalog/install/start/stop/env/update APIs
   - Health probing, explicit failure contracts, and reliability metric surfaces

7. **Multi-instance runtime leadership controls**
   - API/bot/gateway ownership safety with fingerprint-aware lifecycle behavior

8. **Release integrity workflow**
   - RRA gate + release preflight + signed/notarized distribution + matched docs bundle

---

## Product Features

- Topic-centric AI workspace (Telegram-style navigation, chat continuity)
- Per-topic model and routing controls
- File ingestion, search, and artifact management
- Channel-connected workflows (desktop + messaging channels)
- Extension ecosystem via MCP
- Theme system and native desktop UX
- Built-in API Explorer for live endpoint execution/testing

For product deep dive and visuals:

- [clawpad.ai](https://www.clawpad.ai)

---

## API Coverage (Documented)

Current API snapshot (`api-docs/current/reference/endpoint-summary.json`):

- **Total:** 143
- **Methods:** GET 66, POST 63, PUT 5, DELETE 8, WebSocket 1
- **Categories:** 15

Category counts:

| Category | Endpoints |
|---|---:|
| Health & Status | 5 |
| Developer Docs & Discovery | 11 |
| Gateway & Connection | 39 |
| Projects | 7 |
| Messages & AI | 7 |
| Files & Artifacts | 6 |
| Search | 4 |
| Settings & Config | 16 |
| Themes & Appearance | 2 |
| AI Models | 1 |
| System & Database | 4 |
| UI Control | 17 |
| Screenshots | 8 |
| Extensions & Tools | 15 |
| WebSocket | 1 |

This means core platform capabilities are not just UI-only; they are exposed and documented for automation and integration.

---

## API Docs Bundle (Shipped With Every Binary)

Each release includes a version-matched API docs zip asset.

- In-repo source: `api-docs/current/`
- Release asset: `clawpad-api-docs-<release-tag>.zip`
- Manifest: `api-docs/manifest.json`

Primary docs entry points:

- [Quickstart](./api-docs/current/docs/QUICKSTART.md)
- [Remote API Developer Platform Guide](./api-docs/current/docs/REMOTE_API_DEVELOPER_PLATFORM_GUIDE.md)
- [Complete Endpoint Reference](./api-docs/current/docs/REMOTE_API_REFERENCE_COMPLETE.md)
- [API Auth Signing Spec](./api-docs/current/docs/API_AUTH_SIGNING_SPEC.md)
- [Stealth Server Production Guide](./api-docs/current/docs/STEALTH_SERVER_PRODUCTION_GUIDE.md)
- [Errors, Retries, and Failure Policy](./api-docs/current/docs/ERRORS_RETRIES_AND_FAILURE_POLICY.md)
- [SDK Blueprint](./api-docs/current/docs/SDK_BLUEPRINT.md)
- [Integration Checklist](./api-docs/current/docs/INTEGRATION_CHECKLIST.md)

Companion docs repository:

- [github.com/yeogirlyun/clawpad-api-docs](https://github.com/yeogirlyun/clawpad-api-docs)

---

## Installation

1. Download latest DMG from [Releases](https://github.com/yeogirlyun/ClawPad-Release/releases/latest)
2. Drag ClawPad into Applications
3. Launch ClawPad

---

## Links

- Product: [clawpad.ai](https://www.clawpad.ai)
- Releases: [github.com/yeogirlyun/ClawPad-Release/releases](https://github.com/yeogirlyun/ClawPad-Release/releases)
- API Docs: [github.com/yeogirlyun/clawpad-api-docs](https://github.com/yeogirlyun/clawpad-api-docs)
- Support: `support@clawpad.ai`

---

*ClawPad is proprietary software. This repository distributes official release artifacts and associated documentation.*
