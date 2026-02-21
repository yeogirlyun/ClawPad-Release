# Authentication Model: Enrollment + Signed Requests

All `/api/*` endpoints are protected except explicit public routes.

## Public bootstrap routes

- `GET /api/public/identity`
- `POST /api/auth/enroll/start`
- `POST /api/auth/enroll`
- `POST /api/auth/token`

## Protected request requirements

- `Authorization: Bearer <access_token>`
- `X-CP-Client-ID: <client_id>`
- `X-CP-Timestamp: <unix_seconds>`
- `X-CP-Nonce: <nonce>`
- `X-CP-Signature: <base64_ed25519_sig>`

The signature input binds method, path, body hash, timestamp, nonce,
and token hash to prevent replay/tampering.

## Token lifecycle

- Access token: short TTL for active calls
- Refresh token: longer TTL to mint new access token
- Use `POST /api/auth/token` before expiration windows

## Scope model

Client enrollment stores scopes (e.g. `read`, `write`, `admin`).
Admin-gated routes reject callers without `admin` scope.
