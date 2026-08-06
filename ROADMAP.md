# QuantumMeet — 2-Year Upgrade Roadmap

Living document for the dual-Vercel + WebRTC mesh + Mongo event-bus architecture.
Do **not** reintroduce Ably or Socket.io as the primary realtime fabric.

## Architecture lock

```
Browser → Vercel SPA → REST poll/long-poll → Vercel Express → MongoDB
Browser ↔ WebRTC P2P media
```

## Year 1 — Harden & productize

### H1 (implemented foundation)

| Item | Status |
|------|--------|
| Room host JWT tokens | Done — issued on create; required for host actions |
| ICE via `REACT_APP_ICE_SERVERS` | Done — public openrelay removed; STUN default |
| Adaptive poll + long-poll | Done — `wait` query + adaptive intervals |
| Rate limits (login/events/presence/chat/secret) | Done — express-rate-limit helpers |
| ScheduledPost cron | Done — `/api/cron/scheduled-posts` + Vercel crons |
| Observability hook | Done — optional `SENTRY_DSN` |
| CI smoke | Done — `.github/workflows/ci.yml` |

### H2 (implemented foundation)

| Item | Status |
|------|--------|
| Claim host with account JWT | Done — `POST /api/rooms/:id/claim-host` |
| Classroom session uses real roomId + hostToken | Done |
| Attendance from presence | Done — `POST .../attendance/from-presence` |
| Mesh soft cap UX | Done — warn at `MESH_SOFT_CAP` / `REACT_APP_MESH_SOFT_CAP` |
| SecretMeet report + join rate limit | Done |

## Year 2 — Scale & grow

### H3

| Item | Status |
|------|--------|
| Long-poll / SSE-compatible wait | Done (HTTP long-poll ≤25s) |
| SFU feature flag + threshold | Scaffold — `FEATURE_SFU`, `SFU_THRESHOLD` |
| Audit log | Done — `AuditLog` model + host/secret actions |
| Event bus load script | Done — `npm run load:events` |
| E2E Playwright | Scaffold — see `client/e2e/` |

### H4

| Item | Status |
|------|--------|
| Meeting schedules API | Done — `/api/growth/schedules` |
| Orgs / workspaces | Scaffold — flag `FEATURE_ORGS` |
| Webhooks (session.end) | Done — `/api/growth/webhooks` |
| PWA manifest | Done — `client/public/manifest.json` |

## Milestone calendar

| When | Milestone |
|------|-----------|
| M3 | Room tokens + owned TURN credentials in env + rate limits |
| M6 | Cron scheduled posts + Sentry + CI |
| M9 | Classroom↔meeting host bridge + attendance |
| M12 | Mesh caps + recording/Blob retention policy |
| M18 | Long-poll + optional SFU provider wiring |
| M24 | Scheduling UI, LMS embed, org seats |

## Ops runbook (dual Vercel)

1. Deploy **API** from `server/` with `MONGO_URI`, `JWT_SECRET`, `ROOM_TOKEN_SECRET`, `CLIENT_URL`, `CRON_SECRET`, `BLOB_READ_WRITE_TOKEN`.
2. Deploy **SPA** from `client/` with `REACT_APP_SERVER_URL`, optional `REACT_APP_ICE_SERVERS` (JSON TURN/STUN).
3. Cron hits `/api/cron/scheduled-posts` with `Authorization: Bearer $CRON_SECRET`.
4. Incident: check `/api/health`, Atlas connectivity, Vercel function logs, poll errors in browser network tab.
