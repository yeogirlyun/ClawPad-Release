# Stealth Mode: API-Only Server Runtime

`--stealth` runs ClawPad as an API owner process with offscreen Qt.

## Command

```bash
python main.py --stealth --api-port 18790
```

## Behavior

- API server starts and owns configured port
- UI runs offscreen (`QT_QPA_PLATFORM=offscreen`)
- Designed for automation and agent orchestration
- Fails fast on ownership/port conflicts (no fake success)

## When not to use stealth

For workflows that need GPU-backed rendered screenshots/web previews,
use windowed API mode:

```bash
python main.py --api --api-port 18790
```

## Recommended topology

- One stealth API owner process
- Optional additional normal GUI windows for human review
- External apps integrate against `http://127.0.0.1:<port>`
