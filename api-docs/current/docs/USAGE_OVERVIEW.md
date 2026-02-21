# ClawPad API Usage Overview

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
