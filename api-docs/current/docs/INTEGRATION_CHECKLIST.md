# ClawPad Stealth Server Integration Checklist

Version: 1.0

## 1. Pre-Integration

- [ ] Decide runtime mode (`--stealth` recommended for backend use).
- [ ] Define API owner process model (single owner per host/port).
- [ ] Define secret storage for refresh token and private key.
- [ ] Establish observability stack for health/error metrics.

## 2. Authentication Implementation

- [ ] Implement enrollment start/enroll flow.
- [ ] Persist `client_id`, access token, refresh token.
- [ ] Implement request signing per canonical contract.
- [ ] Implement nonce uniqueness protection client-side.
- [ ] Add proactive token refresh before expiry.

## 3. Core Workflow Validation

- [ ] Health check passes (`/health`).
- [ ] Create project flow passes.
- [ ] Send/read message flow passes.
- [ ] File attach/list/read flow passes.
- [ ] WebSocket subscription/reconnect flow passes.

## 4. Failure Handling

- [ ] 401 refresh-and-retry branch implemented.
- [ ] 403 scope errors mapped and surfaced.
- [ ] 404 domain errors surfaced without fallback.
- [ ] 5xx backoff strategy implemented with cap.

## 5. Production Readiness

- [ ] Structured logs include method/path/status/error.
- [ ] Dashboards include health and failure rate.
- [ ] Alerting defined for prolonged `5xx` and auth failures.
- [ ] Release compatibility check against docs zip is automated.

## 6. Release Operations

- [ ] Binary release uploaded.
- [ ] Matching `clawpad-api-docs-<tag>.zip` attached.
- [ ] Team validated docs version against runtime tag.
- [ ] Integration regression suite completed.
