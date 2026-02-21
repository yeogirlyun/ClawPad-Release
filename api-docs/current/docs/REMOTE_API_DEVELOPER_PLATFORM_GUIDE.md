# ClawPad Remote API Developer Platform Guide

Version: 1.0  
Date: 2026-02-21  
Audience: Engineers building applications on top of ClawPad

## 1. Platform Positioning

ClawPad can run as a local API platform server with:

- REST API for control/data operations
- WebSocket stream for real-time events
- Signed authentication model (enrollment + token + request signing)
- GitHub-hosted, release-aligned documentation bundle

This enables ClawPad to act as an application backend for local assistants,
automation pipelines, workflow engines, and integration tools.

## 2. Runtime Modes

### 2.1 Stealth API-only mode (headless)

```bash
python main.py --stealth --api-port 18790
```

Use when you want ClawPad as an API server process without a visible UI.

### 2.2 API + GUI mode

```bash
python main.py --api --api-port 18790
```

Use when developers need both UI and API, including rendered UI workflows.

## 3. Discovery Surfaces

- OpenAPI Swagger UI: `http://127.0.0.1:18790/docs`
- ReDoc: `http://127.0.0.1:18790/redoc`
- OpenAPI JSON: `http://127.0.0.1:18790/openapi.json`
- Dashboard JSON: `GET /api/developer/dashboard`
- Developer docs index/search: `GET /api/developer/docs`
- Unified docs + endpoint search: `GET /api/developer/search`
- Complete endpoint reference JSON: `GET /api/developer/reference`
- Complete endpoint reference Markdown: `GET /api/developer/reference/markdown`
- Release-hub docs index: `api-docs/current/docs/articles/INDEX.md`

## 4. Quickstart Flow

### 4.1 Health check

```bash
curl -s http://127.0.0.1:18790/health
```

### 4.2 Auth bootstrap (required for protected `/api/*`)

1. `POST /api/auth/enroll/start` to create one-time enrollment code.
2. `POST /api/auth/enroll` with your client public key + signed enrollment proof.
3. Store `client_id`, `access_token`, `refresh_token`.
4. Sign each protected request and send required headers.
5. Refresh access token via `POST /api/auth/token`.

### 4.3 First data workflow

1. `POST /api/projects`
2. `POST /api/projects/{project_id}/messages`
3. `GET /api/projects/{project_id}/messages`

## 5. Security Contract

Protected endpoints require all of:

- `Authorization: Bearer <access_token>`
- `X-CP-Client-ID: <client_id>`
- `X-CP-Timestamp: <unix_seconds>`
- `X-CP-Nonce: <nonce>`
- `X-CP-Signature: <base64_signature>`

### 5.1 Scope model

Clients are enrolled with scopes (`read`, `write`, `admin`).
Admin-only endpoints reject insufficient scope with explicit errors.

### 5.2 Failure semantics

ClawPad APIs use explicit failure responses and avoid synthetic fallback payloads.
If required data is unavailable, requests fail with actionable error details.

## 6. API Topology (High-level)

- Health and identity
- Auth and provider credentials
- Projects, messages, files
- Search, settings, themes, models
- Usage and runtime metrics
- UI control and screenshots
- Extensions/tools execution
- Remote/direct transport APIs
- WebSocket realtime channel

Use the dashboard endpoint (`/api/developer/dashboard`) to programmatically
retrieve the current endpoint inventory and category counts.

## 7. Documentation Access and API Lookup

### 7.1 GitHub release-hub docs

Docs search example:

```bash
curl -s "http://127.0.0.1:18790/api/developer/docs?q=stealth&limit=10"
```

Unified search example:

```bash
curl -s "http://127.0.0.1:18790/api/developer/search?q=auth+token&method=POST"
```

Complete reference (all endpoints) example:

```bash
curl -s "http://127.0.0.1:18790/api/developer/reference?limit=1000"
```

### 7.2 Recommended docs set for teams

- `QUICKSTART.md` for onboarding
- `STEALTH_SERVER_PRODUCTION_GUIDE.md` for architecture/ops
- `API_AUTH_SIGNING_SPEC.md` for implementation contract
- `ERRORS_RETRIES_AND_FAILURE_POLICY.md` for reliability behavior
- `SDK_BLUEPRINT.md` and `INTEGRATION_CHECKLIST.md` for production readiness

## 8. Real-time Events

Use WebSocket endpoint:

- `ws://127.0.0.1:18790/ws`

Recommended pattern:

1. Connect
2. Send subscribe message with topic list
3. Process sequenced events (`seq`)
4. Reconnect with backoff on disconnect

## 9. Integration Practices

- Build a thin API client library that centralizes signing and token refresh.
- Store refresh tokens in secure secret storage.
- Add readiness check (`/health`) before workload execution.
- Capture `gateway_fingerprint` for version-awareness across instances.
- Treat auth and ownership conflicts as hard failures; do not assume fallback.
- Validate API schemas at boundaries in production.

## 10. Recommended Delivery Pattern

For production-grade integrations:

1. One dedicated stealth API owner process.
2. One application-side worker service using ClawPad API client.
3. Optional UI process for human inspection and API Explorer use.
4. Monitoring based on `/health`, runtime status endpoints, and logs.

This pattern gives stable ownership, clear operational boundaries,
and consistent API behavior across local and automated environments.
