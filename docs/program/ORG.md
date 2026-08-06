# QuantumMeet Engineering Organization

**Audience:** Engineering managers, tech leads, ICs  
**Horizon:** 24 months | **Steady-state ICs:** 25  
**Product bet:** Meetings + Classroom LMS as equal pillars; education GTM first

This document is the operating org design. It does **not** claim multi-year features are “done.” Squads pull work from [EPICS_BACKLOG.md](./EPICS_BACKLOG.md).

---

## Principles

1. **Squad ownership** — one backlog, one on-call rotation per squad where applicable.
2. **No thrash** — dual Vercel deploy (client + server) stays; no Socket.io-on-Vercel as primary realtime.
3. **Media = WebRTC mesh on Vercel** — no hosted SFU (LiveKit/etc.); soft-cap UX instead.
4. **Scaffold ≠ shipped** — early code spikes in-repo are foundations only; definition of done is squad exit criteria + OKRs.

---

## Steady-state squads (25 ICs)

| Squad | Headcount | Mission | Primary code areas |
|-------|-----------|---------|-------------------|
| **Realtime & Media** | 5 | Call quality, signaling, TURN, mesh | `server/lib/events.js`, `client/src/lib/realtimeClient.js`, `client/src/hooks/useWebRTC.js` |
| **Meetings Product** | 5 | Room UX, host tools, breakouts, recording, SecretMeet, calendar | `client/src/pages/Room.js`, `Home.js`, meeting components, `server/roomRealtime.js` |
| **Classroom / LMS** | 5 | Posts, gradebook, attendance, LTI, teacher analytics | `server/classroom.js`, `client/src/pages/classroom/*` |
| **Platform / Infra** | 5 | CI/CD, observability, Atlas, security, multi-region, flags | `server/vercel.json`, `server/lib/db.js`, CI, runbooks |
| **Growth / Identity / Mobile** | 5 | Auth/SSO, orgs/billing, admin, webhooks, PWA/native | `server/routes/authRoutes.js`, `server/growth.js`, `server/models/growth.js`, mobile shells |

### Shared (may sit outside the 25 or dual-hat)

| Role | Count | Notes |
|------|-------|-------|
| Eng Manager / Tech Lead | 1 per squad (dual-hat OK early) | Owns OKRs, hiring bar, reviews |
| Product Managers | 2 | Meetings+Realtime; Classroom+Growth |
| Design | 2–3 | Design system + squad embeds |
| QA | 2–3 | E2E ownership with Platform |

---

## RACI (program-level)

| Decision | Realtime | Meetings | Classroom | Platform | Growth | EM/PM |
|----------|----------|----------|-----------|----------|--------|-------|
| Signaling / event-bus SLO | **A** | C | C | C | I | I |
| Media policy (mesh-only) | **A** | C | C | C | I | C |
| Room UX / host flows | C | **A** | C | I | I | C |
| LMS curriculum features | I | C | **A** | I | C | C |
| Deploy / secrets / on-call tooling | C | I | I | **A** | I | I |
| SSO / orgs / billing | I | C | C | C | **A** | C |
| Quarterly OKR commit | C | C | C | C | C | **A** |

**R** = Responsible, **A** = Accountable, **C** = Consulted, **I** = Informed (table uses A/C/I for clarity).

---

## Hiring ramp (12 → 25)

| When | IC headcount | Focus hires |
|------|--------------|-------------|
| **Y1Q1 start** | 12–15 | 2 Realtime, 2 Meetings, 2 Classroom, 2 Platform, 2 Growth, + seniors/TL |
| **Y1Q1 end** | 16–18 | Fill Realtime TURN/media; Platform SRE-shaped |
| **Y1Q2 end** | **25** | Full 5×5; second TL if needed |
| **Y1Q3–Y2** | 25 steady | Backfill only; prefer seniority mix |

### Suggested leveling mix at 25

| Level | Approx. count |
|-------|----------------|
| Staff / Principal | 2–3 (Realtime + Platform) |
| Senior | 8–10 |
| Mid | 8–10 |
| Junior / new grad | 3–4 (paired) |

### Hiring bar (minimum)

- Production experience in distributed systems **or** WebRTC **or** edtech LMS **or** React at scale
- Written design docs; on-call willingness for Platform/Realtime
- No “AI stub as delivery” — PRs must include tests and observability for their layer

---

## Cadence

| Ritual | Frequency | Owner |
|--------|-----------|-------|
| Squad standup | Daily | TL |
| Squad planning | Biweekly | TL + PM |
| Cross-squad architecture | Weekly 45m | Staff eng |
| Program review (OKRs) | Monthly | EM + PMs |
| Security review | Quarterly | Platform |
| Customer advisory | Monthly | PM |
| On-call handoff | Weekly | Platform + Realtime |

---

## Definition of done (squad epic)

An epic is **done** only when:

1. Acceptance criteria in [EPICS_BACKLOG.md](./EPICS_BACKLOG.md) met  
2. Tests (unit and/or E2E) in CI  
3. Metrics/logs for failure modes  
4. Runbook updated if ops-facing  
5. PM/design sign-off for user-facing work  

Spikes and ADRs are done when a decision is recorded in `docs/adr/` and linked from the epic.

---

## Related docs

- [CAPACITY.md](./CAPACITY.md) — hours model  
- [OKRS_Y1.md](./OKRS_Y1.md) / [OKRS_Y2.md](./OKRS_Y2.md)  
- [EPICS_BACKLOG.md](./EPICS_BACKLOG.md)  
- [../adr/](../adr/) — architecture decisions  
- [../../ROADMAP.md](../../ROADMAP.md) — executive index  
