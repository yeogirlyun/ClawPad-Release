# API Auth & Signing Spec

This spec described an Ed25519-signed bearer-token scheme used by the pre-v0.16.0 `/api/auth/enroll` enrollment flow. **As of v0.16.0 those endpoints are no longer served.** The local desktop gateway on `127.0.0.1:8787` accepts unauthenticated calls because the security boundary is the localhost socket — anything on that loopback is already on the user's machine.

If a future hardened deployment story is restored, an updated signing spec will replace this stub. Until then:

- **[QUICKSTART.md](QUICKSTART.md)** — current API entry point, no auth required
- **[clawpad.ai/api](https://www.clawpad.ai/api/)** — full endpoint surface
- The audit chain itself still uses Ed25519 over BLAKE3; verify a checkpoint with `GET /api/audit/checkpoint` and the public key advertised at `signer_kid`.

The pre-v0.16.0 content (full enrollment + signing protocol) is preserved in git history at the [file's commit log](https://github.com/yeogirlyun/ClawPad-Release/commits/main/api-docs/current/docs/API_AUTH_SIGNING_SPEC.md).
