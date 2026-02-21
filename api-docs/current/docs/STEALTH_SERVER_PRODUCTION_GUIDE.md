# ClawPad Stealth Server: Production Integration Guide

Version: 1.0  
Audience: Platform engineers, backend engineers, automation teams

## Purpose

This guide defines a production-grade way to run ClawPad as a **Stealth Server** (`--stealth`) and integrate external applications through its signed REST/WebSocket API.

## 1. What Makes This Production-Grade

ClawPad follows patterns used by major API platforms:

- Explicit authentication and authorization boundaries.
- Deterministic request signing with replay protection.
- Stable response envelope (`success`, `data`, `error`, `timestamp`).
- Explicit failure semantics (no synthetic fallback payloads).
- Machine-readable endpoint inventory for tooling and CI validation.

## 2. Runtime Modes

### 2.1 Binary release runtime (recommended for operators)

```bash
./ClawPad.app/Contents/MacOS/ClawPad --stealth --api-port 18790
```

### 2.2 Source runtime (recommended for local development)

```bash
python main.py --stealth --api-port 18790
```

## 3. Stealth Server Topology

Recommended deployment pattern:

1. One dedicated ClawPad Stealth process on each host.
2. One integration service (your app) that owns API auth/signing and retries.
3. Optional human-facing ClawPad GUI process for inspection.
4. Health checks and structured logs around API availability.

## 4. Readiness and Health Gates

Use these gates before running workflows:

1. `GET /health` must return `success=true`.
2. Persist `gateway_fingerprint` from `/health` and detect drift across upgrades.
3. If not healthy, fail fast and alert; do not synthesize fallback state.

Example:

```bash
curl -s http://127.0.0.1:18790/health | jq
```

## 5. Security Lifecycle

All protected routes are under `/api/*`. Use this flow:

1. `POST /api/auth/enroll/start` (localhost only) to get one-time code.
2. `POST /api/auth/enroll` with client public key + signature.
3. Persist `client_id`, `access_token`, `refresh_token`.
4. Sign every protected request.
5. Rotate access token via `POST /api/auth/token`.

Canonical details are in `API_AUTH_SIGNING_SPEC.md`.

## 6. Core Application Workflow

Minimal productive sequence:

1. Create workspace: `POST /api/projects`.
2. Send prompt: `POST /api/projects/{project_id}/messages`.
3. Read history: `GET /api/projects/{project_id}/messages`.
4. Attach/retrieve files: `/api/projects/{project_id}/files*`.
5. Add global search or WebSocket event stream as needed.

## 7. Eventing Model

Realtime endpoint:

- `ws://127.0.0.1:18790/ws`

Guidance:

1. Subscribe to required topics only.
2. Track event sequence (`seq`) for ordering/lag checks.
3. Reconnect with exponential backoff.
4. Use REST reconciliation after reconnect if event gaps are suspected.

## 8. Retry and Failure Strategy

- Retry transient network and `5xx` errors only.
- Do not blind-retry all `4xx`.
- On `401`, refresh token once and retry once.
- On `403`, treat as policy/scope failure.
- On ownership/startup conflict, treat as hard infrastructure error.

Detailed matrix: `ERRORS_RETRIES_AND_FAILURE_POLICY.md`.

## 9. Versioning and Contract Checks

For each release:

1. Keep `api-docs/current/reference/endpoints.json` in source control.
2. Compare endpoint/method inventory in CI against previous release.
3. Validate integration tests against release-tagged docs zip.

## 10. Release Shipping Rule

Every binary release must include:

- `clawpad-api-docs-<tag>.zip` asset
- The same `api-docs/current` content checked into release hub

This keeps runtime artifacts and documentation contract-aligned.

## 11. Recommended Go-Live Checklist

See `INTEGRATION_CHECKLIST.md` for pre-production and production gates.
