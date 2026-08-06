# Public API draft (E-409 light)

Base: `{API}/api`

| Area | Endpoints | Auth |
|------|-----------|------|
| Health | `GET /health`, `GET /ice` | none |
| Rooms | `POST /rooms`, events, presence, knock | host token where noted |
| Classroom | `/classrooms/*` | JWT |
| Growth | `/growth/features`, schedules, orgs | JWT (+ flags) |

Eng handbook stub: local `npm run dev` in `server/` + `client/`; dual Vercel projects; Mongo event bus (no Socket.IO on Vercel).

Partner API keys + rate limits → E-707.
