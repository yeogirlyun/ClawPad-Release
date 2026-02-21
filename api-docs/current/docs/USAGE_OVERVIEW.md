# ClawPad API Usage Overview

This page explains how developers should approach ClawPad as a platform.

## Integration Lifecycle

1. Start runtime (`--stealth` for API-only mode).
2. Complete enrollment and token bootstrap.
3. Create project contexts.
4. Send/stream messages and collect outputs.
5. Manage files, search, and automation endpoints.
6. Observe usage/health and enforce explicit error handling.

## Security Baseline

- Treat all `/api/*` routes as protected unless explicitly documented public.
- Implement token refresh and request signing in one reusable client module.
- Validate non-2xx responses as contract errors, not soft fallbacks.

## Operational Baseline

- Check `/health` before heavy workflow operations.
- Use idempotent reads for discovery and retries.
- Use explicit failure paths for missing resources or auth expiration.

## Where to Read Next

- Quickstart: [QUICKSTART.md](./QUICKSTART.md)
- Auth and signing: [Authentication Model](./articles/auth-signing.md)
- WebSocket events: [WebSocket Event Streaming](./articles/websocket-events.md)
- Full endpoint reference: [REMOTE_API_REFERENCE_COMPLETE.md](./REMOTE_API_REFERENCE_COMPLETE.md)
