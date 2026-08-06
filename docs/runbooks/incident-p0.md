# P0 incident runbook (meetings)

## Severity

**P0:** No one can create/join rooms, or DB hard-down, or mass call failures.

## First 5 minutes

1. Open `GET https://<api>/api/health` — expect `status: ok`, `db: connected`.
2. If `503` / `db: disconnected` → check Atlas status + `MONGO_URI` on Vercel.
3. Check Vercel function logs for `DB_UNAVAILABLE` / `payload_too_large` spikes.
4. Confirm client `REACT_APP_SERVER_URL` points at the healthy API.

## Mitigations

| Symptom | Action |
|---------|--------|
| DB down | Fail-closed is intentional; restore Atlas first |
| Rate-limit storms | Check `rate_limit_hits` collection; raise limits only temporarily |
| Signaling lag | Disable long-poll via `FEATURE_LONG_POLL=0`; restart clients |
| ICE fail | Check `GET /api/ice` `hasTurn` + `ICE_SERVERS` (see `turn.md`) |

## Escalate

- Platform on-call (when staffed) + Realtime TL  
- Post status to team channel with health JSON snapshot  

## After

- File follow-up in backlog (observability / TURN / capacity)  
- Do not “fix” by disabling fail-closed in production  
