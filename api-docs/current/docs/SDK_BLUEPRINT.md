# ClawPad API SDK Blueprint

Version: 1.0  
Goal: A maintainable client SDK structure for production integrations.

## 1. Modules

Recommended package layout:

1. `transport`
2. `auth`
3. `signing`
4. `resources.projects`
5. `resources.messages`
6. `resources.files`
7. `resources.search`
8. `events.websocket`
9. `errors`
10. `models`

## 2. Responsibilities

- `transport`: HTTP execution, retries, timeout policy, telemetry hooks.
- `auth`: enrollment, token refresh lifecycle, secure token store interface.
- `signing`: canonical string construction and Ed25519 signatures.
- `resources.*`: typed endpoint wrappers.
- `events.websocket`: connect/subscribe/reconnect loop.

## 3. Core Interfaces

```text
class AuthProvider:
  enroll(display_name)
  refresh_if_needed()
  auth_headers(method, path_no_query, body_bytes)

class ClawPadClient:
  create_project(...)
  send_message(...)
  list_messages(...)
  add_file(...)
  search(...)
```

## 4. Timeout Defaults

Suggested defaults:

- Connect timeout: 5s
- Read timeout: 30s
- Long inference requests: configurable 120s+

## 5. Error Mapping

Map server responses into typed SDK errors:

- `AuthError` (`401`)
- `ForbiddenError` (`403`)
- `NotFoundError` (`404`)
- `ValidationError` (`400`)
- `ServerError` (`5xx`)
- `TransportError` (network failures)

## 6. Test Strategy

1. Unit test canonical signing format.
2. Unit test token refresh branch and expiry thresholds.
3. Integration test full enroll-create-message-read flow.
4. Integration test forbidden scope branch.
5. Integration test replay rejection with duplicate nonce.

## 7. Release Discipline

For each ClawPad release tag:

1. Pull matching `clawpad-api-docs-<tag>.zip`.
2. Diff endpoint inventory (`reference/endpoints.json`).
3. Run SDK compatibility test suite.
4. Publish SDK changelog entry with contract notes.
