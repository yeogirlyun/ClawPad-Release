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

## Core Technical Achievements

1. **Intelligent Model Routing + Automatic Fallback**
   - ModelRouter as single source of truth for active model resolution
   - ModelHealthRegistry with 15-minute provider health probes and TTL-based recovery
   - intelligence-per-dollar ranking for smart fallback cascade (READY → FALLBACK → LOCAL_ONLY)

2. **123-App Ecosystem with Competitive Feature Parity**
   - 95 user-facing apps, each with REST API, web UI, and AI operability
   - PDForge manufacturing pipeline: 30+ apps expanded to 40-45 operations at 84-86% competitive parity
   - domain-specific UI specialization via UIForge profiles across all apps

3. **Secure Pairing + Direct Client/Server Execution**
   - secure ticket-based remote enrollment
   - direct runtime connectivity for client/server operations

4. **Remote Server Lifecycle + Compatibility Contract**
   - lifecycle management surfaces for remote execution environments
   - compatibility contract for stable cross-version operation

5. **MCP Extension Operations + Reliability Controls**
   - full extension lifecycle capabilities: catalog, install, configure, start, stop, update
   - explicit operational health and failure visibility for extension/runtime safety

6. **Proactive Engine + Agent Jobs Control Plane**
   - durable jobs timeline with run-aware visibility
   - dashboard + API management for create, update, filter, select, and execute flows

7. **Embedded OpenClaw Gateway**
   - integrated local gateway for unified AI model access
   - automatic provider health monitoring and model switching

8. **Release Integrity Workflow**
   - 1,758 automated tests with zero human interaction (RRG auto suite)
   - signed/notarized artifacts with synchronized release/docs bundle

---

## Technology Footprint

- **Desktop platform:** Python + PyQt6 native application runtime
- **Local AI capability:** local-first runtime with GGUF-class model support
- **API protocols:** REST/JSON endpoints, WebSocket event stream, webhook ingress
- **Extension standard:** MCP-based extension ecosystem
- **Data/search substrate:** SQLite persistence with FTS-backed retrieval (platform DB + per-app DBs)
- **Security posture:** authenticated API surface and encrypted credential storage capabilities
- **Distribution trust:** Apple Developer ID signing, notarization, and checksum verification
- **App manufacturing:** PDForge pipeline + UIForge specialization for competitive feature parity

---

## Product Features

- **Intelligent Model Routing** with automatic fallback across cloud and local providers
- **123 bundled apps** — productivity, finance, creative, developer tools, and more
- **Agent Jobs** as a first-class automation surface with timeline-backed operational visibility
- **Remote API platform** for application control, automation, extension operations, and observability
- **MCP extension ecosystem** with production-oriented lifecycle and reliability visibility
- **Workspace continuity** across desktop and channel-connected usage paths
- **Release-grade distribution quality** for production rollouts and update integrity

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
