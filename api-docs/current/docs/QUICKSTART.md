# ClawPad API Quickstart

Five minutes from "is the gateway up?" to "I just signed an audit checkpoint." All examples below are live-tested against ClawPad **v0.16.0** running locally; copy and run them as-is.

> **Free.** ClawPad ships under the MIT License and is free for personal, business and commercial use. The Remote API is included at no cost — no key required, no quota, no tier — when you call it against your own local gateway. You only pay third-party LLM providers for tokens you choose to send through your own credentials.

## 1. Start the gateway

ClawPad's HTTP gateway listens on `127.0.0.1:8787` once the desktop app or `restart_gateway.sh` is running. If you have ClawPad installed:

```bash
# Option A — desktop app: just open ClawPad.app
open -a ClawPad

# Option B — from a source checkout
./scripts/restart_gateway.sh
```

Either way, the gateway is ready when `http://127.0.0.1:8787/` returns the React shell (HTML, not JSON).

## 2. Verify the gateway is up

The JSON-shaped probe is `/api/apps`. It always returns `200` with the list of bundled apps when the gateway is healthy:

```bash
curl -s http://127.0.0.1:8787/api/apps | jq '.apps | length'
```

Expected: a positive integer (23 on a stock v0.16.0 install). If you get `Connection refused`, the gateway isn't running yet — re-check step 1.

## 3. Hit a real endpoint — the signed audit checkpoint

Every state-changing action ClawPad takes lands in a signed audit chain. The chain's tip is exposed as a JSON object with an Ed25519 signature you can verify externally:

```bash
curl -s http://127.0.0.1:8787/api/audit/checkpoint | jq
```

Sample response:

```json
{
  "tip_id": "01KQRH526Z4FZY0BKBCCX5QRED",
  "tip_hash": "59f653bd4aac0bd6edb399406ff632a81b261536516166877211b71c5c1b9d5f",
  "signed_at": "2026-05-05T05:31:23.154716+00:00",
  "signer_kid": "kid_3b8056514f0f",
  "signature": "d54e18932aa0cadb7bf497d3ee54e3e8c4f5..."
}
```

The `signature` is Ed25519 over the BLAKE3 chain envelope — any external service holding the public key can verify the tip independently.

## 4. List installed apps

```bash
curl -s http://127.0.0.1:8787/api/apps | jq '.apps[] | {app_id, description}' | head -20
```

Each entry includes `app_id`, `description`, `version`, `kind`, `tier`, and `installed`. Use the `app_id` as the slug for per-app calls.

## 5. Call a per-app operation

Per-app operations live at `/api/apps/<app_id>/<operation_id>`. Browse the full surface with auto-generated examples at:

**[www.clawpad.ai/api](https://www.clawpad.ai/api/)**

The portal lists all 8,200+ REST operations across 309 apps with parameter schemas, response shapes, and copy-pasteable curl snippets per operation.

## Authentication on the local gateway

You do **not** need to enroll a client, sign requests, or supply an API key when calling `127.0.0.1:8787` from the same machine. The local gateway accepts unauthenticated calls because the security boundary is the localhost socket — anything that can reach `127.0.0.1:8787` is already on your machine.

If you put ClawPad behind a network-reachable hardened deployment, see `API_AUTH_SIGNING_SPEC.md` for the Ed25519-signed-token scheme — but for the desktop install, skip that file.

## Provider connections (optional)

ClawPad routes chat traffic through whatever providers you connect:

```bash
# What's enabled and authenticated?
curl -s http://127.0.0.1:8787/api/settings/providers | jq '.providers[] | {provider, enabled, has_key}'

# Codex OAuth status (the "no API key" path through your ChatGPT subscription)
curl -s http://127.0.0.1:8787/api/auth/codex/status | jq
```

Connecting Codex OAuth or supplying an API key is done in the desktop app's Settings → Providers; this guide doesn't cover the OAuth device flow.

## Where to go next

- **Full endpoint reference + interactive examples**: [www.clawpad.ai/api](https://www.clawpad.ai/api/)
- **Per-app OpenAPI specs** (one JSON file per app): `api/specs/<app_id>.json`
- **Auth signing spec** (production deployments only): `API_AUTH_SIGNING_SPEC.md`
- **Source + license**: [github.com/yeogirlyun/ClawPad-Release](https://github.com/yeogirlyun/ClawPad-Release)
