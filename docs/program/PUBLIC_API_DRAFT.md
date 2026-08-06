# Public API draft (E-409 light)

Base: `{API}/api`

| Area | Endpoints | Auth |
|------|-----------|------|
| Health | `GET /health`, `GET /ice` | none |
| Rooms | `POST /rooms`, events, presence, knock | host token where noted |
| Classroom | `/classrooms/*` | JWT |
| Growth | `/growth/features`, schedules, orgs, ICS | JWT (+ flags) |
| LTI | `/lti/config` | stub |
| Media policy | `/sfu/health` (`mesh_only`), `/sfu/token` → 501 | none |
| Partner | `/partner/keys`, `/partner/whoami` | API key (`qm_…`) |

Eng handbook stub: local `npm run dev` in `server/` + `client/`; dual Vercel projects; Mongo event bus (no Socket.IO on Vercel).

Partner keys: `POST /api/partner/keys` (JWT) issues a one-time `qm_…` secret; call `/api/partner/whoami` with `Authorization: Bearer qm_…`.
