# WebSocket Event Streaming

Use `ws://127.0.0.1:<port>/ws` for live events.

## Basic flow

1. Connect
2. Receive welcome frame
3. Subscribe by topic set
4. Process sequenced events (`seq`)

## Example client message

```json
{
  "action": "subscribe",
  "topics": ["message.sent", "message.chunk", "project.updated"]
}
```

## Keepalive

Send:

```json
{"action": "ping"}
```

Receive `pong` response with server timestamp.
