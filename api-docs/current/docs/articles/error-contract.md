# Error Contract and Explicit Failure Semantics

ClawPad responses follow a shared envelope:

```json
{
  "success": false,
  "error": "human-readable reason",
  "timestamp": "..."
}
```

## Operational guidance

- Check `success` before reading `data`
- On `401/403`, refresh tokens or re-enroll if revoked
- On startup ownership conflicts, treat as hard failure and retry on a free port
- Do not assume fallback data for unavailable resources

## Reliability practices

- Make `/health` checks part of startup and readiness probes
- Log `gateway_fingerprint` to detect version skew across instances
- Use idempotent retries for transient network failures only
