# Quickstart: Run ClawPad as an API Platform

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
