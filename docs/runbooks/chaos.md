# Chaos / failure modes

| Failure | Expect | Verify |
|---------|--------|--------|
| Mongo down | `/api/rooms/*` → 503 `DB_UNAVAILABLE`; `/api/health` → degraded | Kill URI briefly |
| Rate limit storm | 429 from express-rate-limit; Mongo store if configured | `load:events` high concurrency |
| Long-poll timeout | Client falls back to short poll | `FEATURE_LONG_POLL=0` or kill mid-wait |
| Vercel cold start | First request slow; health still 200 | Hit idle preview |
| Bad ICE | Media fail, signaling OK | Empty `ICE_SERVERS` + strict NAT |

Game day: pick 2 rows, time recovery, file follow-ups. Do **not** disable fail-closed to “fix” prod.

## Game day template

| Field | Value |
|-------|-------|
| Date | |
| Owner | |
| Failures exercised | |
| RPO observed | |
| RTO observed | |
| Follow-ups filed | |
