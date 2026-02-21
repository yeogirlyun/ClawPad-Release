# ClawPad API Authentication and Signing Specification

Version: 1.0  
Applies to: `/api/*` protected endpoints

## 1. Security Constants

Current defaults in ClawPad:

- Access token TTL: `900` seconds (15 minutes)
- Refresh token TTL: `2592000` seconds (30 days)
- Enrollment code TTL: `300` seconds (5 minutes)
- Allowed timestamp skew: `±120` seconds
- Nonce replay window: `600` seconds (10 minutes)

## 2. Public Bootstrap Routes

These can be called before enrollment:

- `GET /api/public/identity`
- `POST /api/auth/enroll/start`
- `POST /api/auth/enroll`
- `POST /api/auth/token`

## 3. Required Headers for Protected Requests

- `Authorization: Bearer <access_token>`
- `X-CP-Client-ID: <client_id>`
- `X-CP-Timestamp: <unix_seconds>`
- `X-CP-Nonce: <unique_nonce>`
- `X-CP-Signature: <base64_ed25519_signature>`

## 4. Canonical Messages

### 4.1 Enrollment signature (`POST /api/auth/enroll`)

```
clawpad_enroll_v1
<display_name>
<fingerprint_id>
<enrollment_code>
```

### 4.2 Token refresh signature (`POST /api/auth/token`)

```
clawpad_refresh_v1
<client_id>
<timestamp>
<nonce>
<sha256(refresh_token)>
```

### 4.3 Protected request signature (`/api/*`)

```
clawpad_api_v1
<client_id>
<timestamp>
<nonce>
<METHOD>
<path_without_query>
<sha256(request_body_bytes)>
<sha256(access_token)>
```

Important:

- Use uppercase HTTP method.
- Sign path **without query string**.
- Hash raw request body bytes.
- Nonce must be unique per client within replay window.

## 5. Python Reference Implementation (Minimal)

```python
import base64
import hashlib
import json
import secrets
import time
import urllib.request

from cryptography.hazmat.primitives import serialization
from cryptography.hazmat.primitives.asymmetric.ed25519 import Ed25519PrivateKey


class ClawPadSigner:
    def __init__(self):
        self.private_key = Ed25519PrivateKey.generate()
        self.client_id = ""
        self.access_token = ""

    @staticmethod
    def _sha256_bytes(data: bytes) -> str:
        return hashlib.sha256(data).hexdigest()

    @staticmethod
    def _sha256_text(text: str) -> str:
        return hashlib.sha256(text.encode("utf-8")).hexdigest()

    def sign_request(self, method: str, path_no_query: str, body: bytes) -> dict:
        ts = str(int(time.time()))
        nonce = secrets.token_urlsafe(9)
        msg = "\n".join([
            "clawpad_api_v1",
            self.client_id,
            ts,
            nonce,
            method.upper(),
            path_no_query,
            self._sha256_bytes(body),
            self._sha256_text(self.access_token),
        ]).encode("utf-8")
        signature = base64.b64encode(self.private_key.sign(msg)).decode("ascii")
        return {
            "Authorization": f"Bearer {self.access_token}",
            "X-CP-Client-ID": self.client_id,
            "X-CP-Timestamp": ts,
            "X-CP-Nonce": nonce,
            "X-CP-Signature": signature,
        }
```

## 6. Scope Model

Scopes are attached at enrollment (`read`, `write`, `admin`).

- `admin`: full access.
- Non-admin GET: requires `read` or `write`.
- Non-admin mutation: requires `write`.
- `/api/auth/clients*`: admin required.

## 7. Common Auth Failures

- `401 Missing or invalid Authorization header`
- `401 Access token invalid/expired/revoked`
- `401 Signature verification failed`
- `401 Replay detected (nonce already used)`
- `401 Request timestamp outside allowed skew`
- `403 Admin scope required`
- `403 Write scope required`

## 8. Production Recommendations

1. Keep auth/signing in one dedicated module.
2. Refresh access token proactively before expiry.
3. Generate cryptographically strong nonces.
4. Use monotonic-aware clock sync and monitor skew.
5. Never cache signed headers between requests.
