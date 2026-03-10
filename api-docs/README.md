# ClawPad API Docs Bundle

This directory contains the API documentation payload shipped with binary releases.

## Stats (v0.9.0)

- **4,458 REST endpoints** across 123 apps
- **Methods:** GET 1,586 | POST 2,140 | PUT 431 | DELETE 299 | PATCH 2
- **Per-app OpenAPI specs** available at [clawpad.ai/api](https://www.clawpad.ai/api/)

## Layout

- `current/docs/` — human-readable markdown guides and full endpoint reference
- `current/reference/` — machine-readable JSON payloads (endpoint summary, categories, full endpoint list)

## Entry Points

- `current/docs/QUICKSTART.md` — first API call in 5 minutes
- `current/docs/REMOTE_API_DEVELOPER_PLATFORM_GUIDE.md` — full developer platform guide
- `current/docs/REMOTE_API_REFERENCE_COMPLETE.md` — complete endpoint reference
- `current/docs/API_AUTH_SIGNING_SPEC.md` — Ed25519 authentication spec
- `current/docs/ERRORS_RETRIES_AND_FAILURE_POLICY.md` — error handling and retry policy
- `current/docs/INTEGRATION_CHECKLIST.md` — production integration checklist

## Online Portal

For interactive browsing with per-app specs and example requests: **[www.clawpad.ai/api](https://www.clawpad.ai/api/)**

## Release Rule

Every published binary release includes a matching API docs zip asset, built automatically by GitHub Actions from this directory.
