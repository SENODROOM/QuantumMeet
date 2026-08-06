# QuantumMeet — Executive Roadmap (24 Months · ~25 Engineers)

**This is the program index for employees and leadership.**  
It is **not** a claim that two years of product work are finished in code.

Early monorepo spikes (room tokens, long-poll, cron, feature flags, etc.) are **foundational experiments**. Delivery happens when squads complete epics under [docs/program/EPICS_BACKLOG.md](docs/program/EPICS_BACKLOG.md) with the definition of done in [docs/program/ORG.md](docs/program/ORG.md).

---

## Product bet

- **Pillars:** Meetings + Classroom LMS (equal)  
- **GTM:** Education first (tutoring, schools, universities)  
- **Architecture:** Dual Vercel (SPA + API), WebRTC mesh for small rooms, Mongo/HTTP event bus for signaling; **SFU in Year 2** for large rooms  

```mermaid
flowchart LR
  subgraph year1 [Year1]
    Mesh[WebRTC_mesh]
    Bus[Mongo_HTTP_bus]
    API[Vercel_API]
  end
  subgraph year2 [Year2]
    SFU[SFU_large_rooms]
    Region[Multi_region]
    Mobile[Mobile_clients]
  end
  year1 --> year2
```

---

## Program documentation pack

| Doc | Purpose |
|-----|---------|
| [docs/program/ORG.md](docs/program/ORG.md) | 5 squads, RACI, hiring bar, cadence, DoD |
| [docs/program/CAPACITY.md](docs/program/CAPACITY.md) | ~55k eng-hours / 2 years; 20% contingency → ~44k planned |
| [docs/program/OKRS_Y1.md](docs/program/OKRS_Y1.md) | Quarterly OKRs months 0–12 |
| [docs/program/OKRS_Y2.md](docs/program/OKRS_Y2.md) | Quarterly OKRs months 12–24 |
| [docs/program/EPICS_BACKLOG.md](docs/program/EPICS_BACKLOG.md) | Epic IDs, squad, size, dependencies |
| [docs/adr/](docs/adr/) | ADR-001 realtime, ADR-002 SFU, ADR-003 multi-region |

---

## Hiring ramp (12 → 25 ICs)

| Milestone | Headcount | Intent |
|-----------|-----------|--------|
| **Y1Q1 start** | 12–15 | Core: Realtime, Meetings, Classroom, Platform, Growth |
| **Y1Q1 end** | 16–18 | Strengthen media + SRE-shaped Platform |
| **Y1Q2 end** | **25** | Full 5×5 squad model |
| **Y1Q3–Y2** | 25 steady | Backfill only |

Detail: [docs/program/ORG.md](docs/program/ORG.md#hiring-ramp-12--25).

Until headcount is 25, plan **60–70%** of steady-state capacity ([CAPACITY.md](docs/program/CAPACITY.md)).

---

## Year outcomes (executive)

| Year | Outcome |
|------|---------|
| **Y1** | Shippable B2B education + meetings product; SSO/billing path; SFU vendor chosen + sandbox |
| **Y2** | SFU in production; multi-region; mobile GA; LTI or calendar; analytics; cost/MAU |

### Milestone metrics

| When | Metric |
|------|--------|
| M6 | Call success ≥ 95% on pilots; host-auth abuse incidents = 0 |
| M12 | Pilot orgs active (N from PM); enterprise packaging without forks |
| M18 | SFU in production; signaling p95 within SLO |
| M24 | Mobile GA; SSO GA; integration GA; cost/MAU tracked |

---

## Quarterly story (one line each)

| Quarter | Theme |
|---------|-------|
| Y1Q1 | Trust & call quality (TURN, host auth, on-call, CI) |
| Y1Q2 | Classroom depth & org tenancy |
| Y1Q3 | Mesh at ~15; SFU ADR + 30-peer sandbox |
| Y1Q4 | Enterprise v1 (SSO, retention, billing, E2E) |
| Y2Q1 | SFU production path |
| Y2Q2 | Multi-region & realtime edge decision |
| Y2Q3 | Mobile & school IT integrations |
| Y2Q4 | Analytics, a11y, i18n, SecretMeet fate |

Full OKRs: [OKRS_Y1.md](docs/program/OKRS_Y1.md) · [OKRS_Y2.md](docs/program/OKRS_Y2.md).

---

## Squads at a glance

| Squad | n | Owns |
|-------|---|------|
| Realtime & Media | 5 | Signaling, TURN, mesh, SFU, quality |
| Meetings Product | 5 | Room UX, host tools, recording, calendar |
| Classroom / LMS | 5 | LMS, attendance, LTI, teacher analytics |
| Platform / Infra | 5 | CI/CD, Atlas, security, multi-region |
| Growth / Identity / Mobile | 5 | SSO, orgs, billing, mobile, webhooks |

---

## Explicit non-goals (first 12 months)

- Rewriting the entire UI framework  
- Merging client + server into one Vercel project  
- White-label marketplace before tenancy/billing works  
- Declaring “2 years complete” via AI-generated stubs  

---

## How employees start Monday morning

1. Read [ORG.md](docs/program/ORG.md) — find your squad.  
2. Read this quarter’s section in OKRs.  
3. Pull next epic from [EPICS_BACKLOG.md](docs/program/EPICS_BACKLOG.md) with TL.  
4. Respect ADRs before changing realtime or media architecture.  

**Questions:** Eng Manager / squad Tech Lead — not the roadmap file.
