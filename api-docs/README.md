# ClawPad API Docs Bundle

This directory contains the API documentation payload shipped with binary releases.

## Free for personal, business and commercial use

ClawPad ships under the **MIT License** and is **free for personal, business, and commercial use**. The **Remote API is included at no cost** — no key, no quota, no tier. You only pay third-party LLM providers (OpenAI, Anthropic, Google, etc.) for tokens you choose to send to them through your own credentials.

This applies to every endpoint in the bundle below.

## Stats (v0.16.0)

- **8,200+ REST operations** across **309 apps**
- **Methods:** GET 3,172 | POST 3,650 | PUT 766 | DELETE 616 | PATCH 2
- **Per-app OpenAPI specs** with example requests at [clawpad.ai/api](https://www.clawpad.ai/api/)

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

For interactive browsing with per-app specs, schemas, and example requests:
**[www.clawpad.ai/api](https://www.clawpad.ai/api/)**

## License

ClawPad and these API docs are released under the [MIT License](https://github.com/yeogirlyun/ClawPad-Release/blob/main/LICENSE). Use them in any commercial or non-commercial setting; fork, audit, redistribute, and embed without restriction.

## Release Rule

Every published binary release includes a matching API docs zip asset, built automatically from this directory.
