# Platform Integration Patterns

Treat ClawPad as a local platform service with two planes:

## Control plane

- auth lifecycle
- gateway/runtime lifecycle
- settings, model, and provider state

## Data plane

- projects, messages, files, search
- extension tools via `/api/tools/*`
- direct/remote transport endpoints for federated execution

## Recommended architecture

- API Client SDK layer (auth + signing)
- Workflow service layer (project/message/files orchestration)
- Event processor (`/ws` for incremental updates)
- Observability layer (`/health`, usage endpoints, logs)

## Production checklist

- dedicated service account per integration
- secret storage for refresh tokens
- periodic client key rotation
- schema validation on request/response boundaries
