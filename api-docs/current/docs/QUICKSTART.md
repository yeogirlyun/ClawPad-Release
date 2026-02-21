# ClawPad API Quickstart (GitHub Edition)

## 1. Start ClawPad API

```bash
python main.py --stealth --api-port 18790
```

## 2. Verify server health

```bash
curl -s http://127.0.0.1:18790/health | jq
```

## 3. Enroll API client (required for `/api/*` endpoints)

1. `POST /api/auth/enroll/start`
2. `POST /api/auth/enroll`
3. Store returned `client_id`, `access_token`, `refresh_token`
4. Sign each protected request with required security headers

See auth details: [Authentication Model](./articles/auth-signing.md)

## 4. First workflow

- Create project: `POST /api/projects`
- Send prompt: `POST /api/projects/{project_id}/messages`
- Fetch messages: `GET /api/projects/{project_id}/messages`

## 5. Explore endpoint catalog

- Full reference markdown: [REMOTE_API_REFERENCE_COMPLETE.md](./REMOTE_API_REFERENCE_COMPLETE.md)
- Machine JSON: [reference/endpoints.json](../reference/endpoints.json)
