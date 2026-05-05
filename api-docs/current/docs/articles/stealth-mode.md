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

---# Stealth Mode: API-Only Server Runtime

`--stealth` runs ClawPad as an API owner process with offscreen Qt.

## Command

```bash
python main.py --stealth --api-port 18790
```

## Behavior

- API server starts and owns configured port
- UI runs offscreen (`QT_QPA_PLATFORM=offscreen`)
- Designed for automation and agent orchestration
- Fails fast on ownership/port conflicts (no fake success)

## When not to use stealth

For workflows that need GPU-backed rendered screenshots/web previews,
use windowed API mode:

```bash
python main.py --api --api-port 18790
```

## Recommended topology

- One stealth API owner process
- Optional additional normal GUI windows for human review
- External apps integrate against `http://127.0.0.1:<port>`
