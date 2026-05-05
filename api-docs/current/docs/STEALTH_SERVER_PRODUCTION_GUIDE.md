# Stealth Server Production Guide

This guide described ClawPad's pre-v0.16.0 `--stealth` server mode and the production deployment story for an authenticated network-reachable API. **As of v0.16.0, the `--stealth` flag and the `/api/auth/enroll` endpoints no longer ship.** The local desktop gateway runs unauthenticated on `127.0.0.1:8787`; there is no public-network deployment recipe at this time.

For current usage:

- **[QUICKSTART.md](QUICKSTART.md)** — five live-tested curls against v0.16.0
- **[clawpad.ai/api](https://www.clawpad.ai/api/)** — the auto-generated portal listing all 8,200+ current operations
- **README.md** — pricing, license, and stats

The pre-v0.16.0 content of this file (a network-reachable hardened deployment guide with Ed25519-signed token enrollment) is preserved in git history at the [file's commit log](https://github.com/yeogirlyun/ClawPad-Release/commits/main/api-docs/current/docs/STEALTH_SERVER_PRODUCTION_GUIDE.md).
