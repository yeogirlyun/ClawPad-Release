# ClawPad API Quickstart (Stealth Server)

## 1. Start ClawPad in Stealth mode

Binary release:

```bash
./ClawPad.app/Contents/MacOS/ClawPad --stealth --api-port 18790
```

Source run:

```bash
python main.py --stealth --api-port 18790
```

## 2. Verify health and identity

```bash
curl -s http://127.0.0.1:18790/health | jq
curl -s http://127.0.0.1:18790/api/public/identity | jq
```

## 3. Enroll API client

1. `POST /api/auth/enroll/start`
2. `POST /api/auth/enroll`
3. Persist returned `client_id`, `access_token`, `refresh_token`
4. Sign each protected request

Reference: [API_AUTH_SIGNING_SPEC.md](./API_AUTH_SIGNING_SPEC.md)

## 4. First productive workflow

- Create project: `POST /api/projects`
- Send message: `POST /api/projects/{project_id}/messages`
- Read history: `GET /api/projects/{project_id}/messages`

## 5. Production-grade next steps

1. Read architecture and ops guidance: [STEALTH_SERVER_PRODUCTION_GUIDE.md](./STEALTH_SERVER_PRODUCTION_GUIDE.md)
2. Implement retry/error handling policy: [ERRORS_RETRIES_AND_FAILURE_POLICY.md](./ERRORS_RETRIES_AND_FAILURE_POLICY.md)
3. Follow readiness checks: [INTEGRATION_CHECKLIST.md](./INTEGRATION_CHECKLIST.md)
4. Use full endpoint contract: [REMOTE_API_REFERENCE_COMPLETE.md](./REMOTE_API_REFERENCE_COMPLETE.md)

## 6. Machine-readable references

- [reference/endpoints.json](../reference/endpoints.json)
- [reference/endpoint-summary.json](../reference/endpoint-summary.json)
- [reference/dashboard-payload.json](../reference/dashboard-payload.json)
