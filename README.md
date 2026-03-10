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
  <a href="https://github.com/yeogirlyun/ClawPad-Release/releases/latest">
    <img src="https://img.shields.io/badge/Platform-macOS-lightgrey?style=for-the-badge&logo=apple" alt="macOS">
  </a>
</p>

---

## What This Repository Provides

This is the official distribution and release-note repository for ClawPad.

- signed/notarized release artifacts
- versioned release summaries
- version-matched API docs bundle

For product walkthroughs and downloads:
- [clawpad.ai](https://www.clawpad.ai)

---

## Velvet Lattice Architecture

ClawPad is built on the **Velvet Lattice** architecture — a vertically integrated platform where every layer (model routing, app runtime, UI rendering, data persistence, and API surface) is woven together into a single coherent system.

This architecture enables capabilities that are difficult or impossible with loosely coupled tools:

- **Automatic app evolution** — apps continuously gain new features, UI refinements, and competitive parity improvements through platform-level manufacturing processes. An app that ships with 15 operations today can grow to 45+ without manual intervention.
- **Intelligent model routing** — the platform monitors provider health in real time and automatically cascades through the best available model ranked by intelligence-per-dollar. If a provider goes down, your workflow continues seamlessly.
- **Domain-aware UI generation** — each app receives a UI specialized for its domain (data tables for spreadsheets, message streams for chat, canvas layouts for drawing) rather than a generic one-size-fits-all interface.
- **Self-healing release pipeline** — 1,758 automated tests validate every release with zero human interaction. Build, sign, notarize, and distribute in a single pipeline.

The result: a platform where **123 apps** ship as a single integrated product, each with a REST API, web UI, and full AI operability — and the platform keeps improving all of them simultaneously.

---

## Core Capabilities

1. **123-App Ecosystem**
   - 95 user-facing apps spanning productivity, finance, creative, developer tools, and more
   - every app has a REST API, browser-based UI, and AI-operable interface
   - apps are continuously expanded toward competitive feature parity with market leaders

2. **Intelligent Model Routing + Automatic Fallback**
   - single source of truth for active model resolution across cloud and local providers
   - real-time provider health monitoring with automatic recovery
   - fallback cascade: cloud models → alternative providers → local models → graceful degradation

3. **Massive-Scale UI Improvement**
   - platform-level UI generation produces domain-specialized interfaces for every app
   - 8 layout archetypes matched to app domains (tables, grids, dashboards, canvases, timelines, message streams)
   - UI improvements propagate across all apps in a single pass

4. **Continuous Feature Expansion**
   - automated competitive analysis identifies feature gaps against market leaders
   - platform manufacturing processes design, implement, and test new operations at scale
   - 30+ apps already expanded from minimal feature sets to 84-86% competitive parity

5. **Secure Pairing + Direct Client/Server Execution**
   - secure ticket-based remote enrollment
   - direct runtime connectivity for client/server operations

6. **Remote Server Lifecycle + Compatibility Contract**
   - lifecycle management surfaces for remote execution environments
   - compatibility contract for stable cross-version operation

7. **MCP Extension Ecosystem**
   - full extension lifecycle: catalog, install, configure, start, stop, update
   - operational health and failure visibility for production reliability

8. **Agent Jobs Control Plane**
   - durable jobs timeline with run-aware visibility
   - dashboard + API management for autonomous multi-step workflows

---

## Technology Footprint

- **Desktop platform:** Python + PyQt6 native application runtime
- **Local AI capability:** local-first runtime with GGUF-class model support
- **API protocols:** REST/JSON endpoints, WebSocket event stream, webhook ingress
- **Extension standard:** MCP-based extension ecosystem
- **Data substrate:** SQLite persistence with FTS-backed retrieval
- **Security posture:** authenticated API surface with encrypted credential storage
- **Distribution trust:** Apple Developer ID signing, notarization, and checksum verification

---

## Product Features

- **Intelligent Model Routing** with automatic fallback across cloud and local providers
- **123 bundled apps** with REST APIs, web UIs, and AI operability
- **Platform-scale UI generation** — domain-specialized interfaces for every app
- **Continuous feature expansion** — apps grow toward competitive parity automatically
- **Agent Jobs** as a first-class automation surface with timeline-backed operational visibility
- **Remote API platform** for application control, automation, and observability
- **MCP extension ecosystem** with production-oriented lifecycle management
- **Workspace continuity** across desktop and channel-connected usage paths

---

## API Docs Bundle (Shipped With Releases)

Each release includes a version-matched API docs bundle.

Primary entry points:
- [Quickstart](./api-docs/current/docs/QUICKSTART.md)
- [Remote API Developer Platform Guide](./api-docs/current/docs/REMOTE_API_DEVELOPER_PLATFORM_GUIDE.md)
- [Complete Endpoint Reference](./api-docs/current/docs/REMOTE_API_REFERENCE_COMPLETE.md)
- [API Auth Signing Spec](./api-docs/current/docs/API_AUTH_SIGNING_SPEC.md)
- [Errors, Retries, and Failure Policy](./api-docs/current/docs/ERRORS_RETRIES_AND_FAILURE_POLICY.md)
- [Integration Checklist](./api-docs/current/docs/INTEGRATION_CHECKLIST.md)

---

## Installation

1. Download latest DMG from [Releases](https://github.com/yeogirlyun/ClawPad-Release/releases/latest)
2. Double-click ClawPad.app to install (self-installs to Applications)
3. Configure your AI provider and start using

---

## License and Usage

- Free for personal, business, and commercial use.
- Remote API usage is included and free.

---

## Links

- Product: [clawpad.ai](https://www.clawpad.ai)
- Releases: [github.com/yeogirlyun/ClawPad-Release/releases](https://github.com/yeogirlyun/ClawPad-Release/releases)
- API Docs (in this repo): [api-docs/current](./api-docs/current/)
- Feedback / Questions / Inquiries: [ClawPad YouTube Community](https://www.youtube.com/@clawpad-ai/community)

---

*ClawPad is proprietary software. This repository distributes official release artifacts and associated documentation.*
