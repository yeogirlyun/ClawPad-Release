# ClawPad API Docs Bundle

This directory contains the API documentation payload that is shipped with binary releases.

## Layout

- `current/docs/` - human-readable markdown guides and full endpoint reference
- `current/reference/` - machine-readable JSON payloads

## Production-Grade Entry Points

- `current/docs/QUICKSTART.md`
- `current/docs/STEALTH_SERVER_PRODUCTION_GUIDE.md`
- `current/docs/API_AUTH_SIGNING_SPEC.md`
- `current/docs/ERRORS_RETRIES_AND_FAILURE_POLICY.md`
- `current/docs/SDK_BLUEPRINT.md`
- `current/docs/INTEGRATION_CHECKLIST.md`

## Release Shipping Rule

Every published binary release must include a matching API docs zip asset.

A GitHub Actions workflow in `.github/workflows/release-attach-api-docs.yml` automatically builds
and uploads this zip from `api-docs/current` whenever a release is published.
