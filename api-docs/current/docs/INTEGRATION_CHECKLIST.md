> ⚠️ **This guide is being rewritten for ClawPad v0.16.0.**
>
> The procedures below describe a `--stealth` server mode and a
> `/api/auth/enroll` token-enrollment flow that no longer match the
> shipping product. The local gateway listens on `127.0.0.1:8787`
> (not `:18790`) and accepts unauthenticated calls from localhost.
>
> **For working examples right now, use:**
> - **[QUICKSTART.md](QUICKSTART.md)** — verified against v0.16.0
> - **[clawpad.ai/api](https://www.clawpad.ai/api/)** — auto-generated portal with all 8,200+ current operations
>
> The Ed25519 signed-token scheme described here may still apply
> for hardened production deployments behind a reverse proxy, but
> none of the desktop-install or local-gateway examples below are
> currently accurate. Treat as historical until rewritten.

---# ClawPad Stealth Server Integration Checklist

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
- [ ] Matching API docs zip asset attached.
- [ ] Team validated docs version against runtime tag.
- [ ] Integration regression suite completed.
