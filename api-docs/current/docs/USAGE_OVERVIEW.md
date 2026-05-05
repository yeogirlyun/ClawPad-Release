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

---# ClawPad API Usage Overview

This overview is organized in the same structure commonly expected from major platform docs:

1. Runtime architecture
2. Authentication contract
3. Resource workflows
4. Error/retry policy
5. Production operations

## Start Here

- Stealth architecture: [STEALTH_SERVER_PRODUCTION_GUIDE.md](./STEALTH_SERVER_PRODUCTION_GUIDE.md)
- Auth and signing spec: [API_AUTH_SIGNING_SPEC.md](./API_AUTH_SIGNING_SPEC.md)
- Error and retry contract: [ERRORS_RETRIES_AND_FAILURE_POLICY.md](./ERRORS_RETRIES_AND_FAILURE_POLICY.md)
- SDK design pattern: [SDK_BLUEPRINT.md](./SDK_BLUEPRINT.md)
- Go-live checklist: [INTEGRATION_CHECKLIST.md](./INTEGRATION_CHECKLIST.md)

## Integration Lifecycle

1. Start runtime (`--stealth`).
2. Enroll and bootstrap tokens.
3. Create project contexts.
4. Send messages and collect outputs.
5. Add files/search/event streaming.
6. Operate with explicit failure and observability.

## Contract Principles

- No synthetic fallback payloads.
- `success=false` errors are first-class API outcomes.
- Protected endpoints must always be signed correctly.
- Scope and policy failures are not retryable until corrected.

## Reference Assets

- Human full reference: [REMOTE_API_REFERENCE_COMPLETE.md](./REMOTE_API_REFERENCE_COMPLETE.md)
- Machine endpoint inventory: [reference/endpoints.json](../reference/endpoints.json)
- Developer article index: [articles/INDEX.md](./articles/INDEX.md)
