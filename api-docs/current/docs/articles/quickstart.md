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

---# Quickstart: Run ClawPad as an API Platform

## 1. Start in API mode

Use one of these launch modes:

- `python main.py --stealth --api-port 18790` (headless, API-only)
- `python main.py --api --api-port 18790` (window + API)

## 2. Verify runtime health

```bash
curl -s http://127.0.0.1:18790/health
```

Expected shape:

```json
{
  "success": true,
  "data": {
    "status": "healthy",
    "timestamp": 1770531460.01,
    "version": "...",
    "gateway_fingerprint": "..."
  }
}
```

## 3. Enroll an API client (required for `/api/*`)

1. `POST /api/auth/enroll/start`
2. `POST /api/auth/enroll` with client public key + enrollment signature
3. Store `client_id`, `access_token`, `refresh_token`
4. Call protected endpoints with signed headers + bearer token

## 4. First useful workflow

- `POST /api/projects` create workspace
- `POST /api/projects/{project_id}/messages` send prompt
- `GET /api/projects/{project_id}/messages` fetch results

## 5. Explore endpoint catalog

- OpenAPI UI: `/docs`
- ReDoc: `/redoc`
- Developer dashboard: `/developer/dashboard`
- Machine-readable discovery: `/api/developer/dashboard`
