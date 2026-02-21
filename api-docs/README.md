# ClawPad API Docs Bundle

This directory contains the API documentation payload that is shipped with binary releases.

## Layout

- `current/docs/` - human-readable markdown guides and full endpoint reference
- `current/reference/` - machine-readable JSON payloads

## Release Shipping Rule

Every published binary release must include a matching `clawpad-api-docs-<tag>.zip` asset.

A GitHub Actions workflow in `.github/workflows/release-attach-api-docs.yml` automatically builds
and uploads this zip from `api-docs/current` whenever a release is published.
