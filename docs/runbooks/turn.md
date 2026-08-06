# Production TURN runbook (E-101)

## Goal

Reliable NAT traversal with **owned** TURN (not public openrelay). Clients prefer `GET /api/ice` so credentials stay on the API.

## Configure

1. Provision TURN (Metered, Twilio, coturn, Cloudflare Calls, etc.).
2. Set server env (never commit secrets):

```bash
ICE_SERVERS=[{"urls":"stun:stun.l.google.com:19302"},{"urls":"turn:turn.example.com:3478","username":"...","credential":"..."}]
```

3. Optional client override: `REACT_APP_ICE_SERVERS` (dev only; prod should use `/api/ice`).
4. Redeploy API + verify `GET /api/ice` returns `hasTurn: true`.

## Verify

| Check | Expect |
|-------|--------|
| `GET /api/ice` | `hasTurn: true`, TURN urls present |
| Two browsers behind strict NAT | Media connects (`relay` candidates OK) |
| `iceTransportPolicy: relay` test | Still connects when forced |

## Monitor

- Spike in "ICE failed" / black video with working signaling → rotate TURN creds or capacity.
- Incident P0 table: see `incident-p0.md` ICE row.

## Do not

- Ship username/password in the React bundle for production.
- Use ephemeral public openrelay as the default.
