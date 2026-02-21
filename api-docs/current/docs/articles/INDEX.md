# ClawPad API Documentation Index

Generated: 2026-02-21T17:01:51.904274+00:00

This repository ships comprehensive API documentation and usage guidance for ClawPad developers.

## Core Guides

- [Remote API Developer Platform Guide](../REMOTE_API_DEVELOPER_PLATFORM_GUIDE.md)
- [Complete Endpoint Reference](../REMOTE_API_REFERENCE_COMPLETE.md)

## Usage Documents

- [Authentication Model: Enrollment + Signed Requests](./auth-signing.md)
  - ClawPad uses enrollment code exchange, short-lived access tokens, refresh tokens, and per-request Ed25519 signatures.
- [Complete Remote API Reference (All Endpoints)](./api-reference-complete.md)
  - Full endpoint-by-endpoint reference generated from the local registry, including methods, params, request/response examples, and system effects.
- [Endpoint Discovery and Dashboard](./endpoint-discovery.md)
  - Discover all available APIs through OpenAPI, category registry, and searchable dashboard endpoints.
- [Error Contract and Explicit Failure Semantics](./error-contract.md)
  - API responses use a strict envelope with explicit errors; failures are not hidden by synthetic fallback data.
- [Platform Integration Patterns](./platform-patterns.md)
  - Practical patterns for building external apps on ClawPad: control plane, data plane, and extension orchestration.
- [Quickstart: Run ClawPad as an API Platform](./quickstart.md)
  - Start ClawPad in API mode, verify server health, then create and message projects over HTTP in minutes.
- [Stealth Mode: API-Only Server Runtime](./stealth-mode.md)
  - Use ClawPad in headless offscreen mode for CI/automation and backend-style deployments.
- [WebSocket Event Streaming](./websocket-events.md)
  - Consume live ClawPad events over `/ws` and filter by topic for responsive integrations.

## Machine-Readable References

- [All Endpoints JSON](../../reference/endpoints.json)
- [Endpoint Summary JSON](../../reference/endpoint-summary.json)
- [Category Names JSON](../../reference/categories.json)
- [Dashboard Payload JSON](../../reference/dashboard-payload.json)

