# Epics Backlog — 24-Month Program

**How to use:** Squads pull epics into quarterly plans. Status values: `backlog` | `planned` | `in_progress` | `done` | `killed`.  
**Sizing:** Squad-weeks (see [CAPACITY.md](./CAPACITY.md)). Estimates are planning ranges, not contracts.

Prior in-repo spikes (tokens, long-poll, cron, flags) reduce some Y1Q1 epic sizes but **do not** set status to `done` until definition of done in [ORG.md](./ORG.md) is met in production.

---

## Legend

| Code | Squad |
|------|-------|
| RT | Realtime & Media |
| MT | Meetings Product |
| CL | Classroom / LMS |
| PL | Platform / Infra |
| GR | Growth / Identity / Mobile |

---

## Year 1

### Y1Q1 — Trust & call quality

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-101 | Production TURN (dedicated, creds, monitoring, runbook) | RT | 4–6 | — | backlog |
| E-102 | ICE policy, failover tests, client config hardening | RT | 2–3 | E-101 | backlog |
| E-105 | Signaling SLO doc + dashboards (p95 delivery) | RT + PL | 2–3 | — | backlog |
| E-106 | Observability: tracing, error budgets, Sentry required in prod | PL | 4–5 | — | backlog |
| E-108 | Staging = prod-like (data, secrets, synthetic checks) | PL | 3–4 | E-106 | backlog |
| E-110 | P0 on-call + paging + incident runbooks | PL | 2–3 | E-106 | backlog |

### Y1Q2 — Classroom depth & org tenancy

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-201 | Assignments pipeline + late policies | CL | 5–7 | — | backlog |
| E-202 | Quiz integrity + gradebook export | CL | 4–6 | E-201 | backlog |
| E-203 | Scheduled content UX + cron reliability soak | CL + PL | 3–4 | — | backlog |
| E-204 | Materials library v1 | CL | 3–4 | — | backlog |
| E-205 | Orgs/workspaces + RBAC | GR | 6–8 | — | backlog |
| E-206 | Invite flows + admin audit trail | GR | 3–4 | E-205 | backlog |
| E-207 | Recording → Blob upload + retention enforcement | MT + PL | 4–5 | — | backlog |
| E-208 | Waiting room / knock polish | MT | 2–3 | — | backlog |
| E-209 | Mesh soft-cap UX + teacher/host messaging | MT + RT | 2 | — | backlog |
| E-210 | Backup/restore drills + cost dashboards | PL | 3–4 | E-106 | backlog |
| E-211 | Preview environments per PR | PL | 3–4 | E-108 | backlog |

### Y1Q3 — Scale small rooms; prepare large rooms

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-301 | Long-poll/SSE at load — prove or kill vs SLO | RT | 4–6 | E-105 | backlog |
| E-302 | Whiteboard bandwidth budget + coalescing | RT + MT | 3–4 | E-301 | backlog |
| E-303 | Presence correctness under multi-tab / flaky network | RT | 3–4 | — | backlog |
| E-304 | SFU vendor spike (LiveKit / mediasoup / managed) | RT | 4–6 | — | backlog |
| E-305 | **ADR-002** accepted + sandbox ≥30 peers | RT | 2–3 | E-304 | backlog |
| E-306 | Breakout parity with host tool checklist | MT | 4–5 | — | backlog |
| E-307 | Call quality indicators (loss/bitrate UI) | MT + RT | 3–4 | E-105 | backlog |
| E-308 | Attendance automation + teacher trust study | CL | 4–5 | — | backlog |
| E-309 | Atlas capacity plan + PII data map | PL | 3–4 | — | backlog |
| E-310 | SOC2-ready logging / access controls plan | PL | 3–4 | E-106 | backlog |

### Y1Q4 — Enterprise readiness v1

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-401 | SSO SAML and/or OIDC for orgs | GR | 6–8 | E-205 | backlog |
| E-402 | SCIM stretch (or explicit defer) | GR | 3–5 | E-401 | backlog |
| E-403 | Retention + export/delete self-serve | GR + CL | 4–5 | E-309 | backlog |
| E-404 | DPA templates + residency plan (legal + eng) | PL + GR | 2–3 | E-309 | backlog |
| E-405 | Billing seats + per-org feature flags | GR | 5–7 | E-205 | backlog |
| E-406 | Admin console v1 | GR | 4–6 | E-205 | backlog |
| E-407 | E2E suite: join, chat, knock, grade, attendance | PL + QA | 5–7 | — | backlog |
| E-408 | Chaos tests Mongo/Vercel failure modes | PL | 3–4 | E-108 | backlog |
| E-409 | Public API draft + eng handbook | PL + PM | 3–4 | — | backlog |

---

## Year 2

### Y2Q1 — SFU production

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-501 | SFU production cluster + deploy pipeline | RT + PL | 8–12 | E-305 | backlog |
| E-502 | Mesh default ≤N; SFU auto above threshold | RT + MT | 4–6 | E-501 | backlog |
| E-503 | Simulcast + bandwidth adaptation | RT | 5–7 | E-501 | backlog |
| E-504 | Reconnection / migration between mesh and SFU | RT | 4–6 | E-502 | backlog |
| E-505 | SFU cost dashboard $/participant | PL + RT | 2–3 | E-501 | backlog |
| E-506 | Server-side recording (egress) spike or ship | RT + MT | 5–8 | E-501 | backlog |

### Y2Q2 — Multi-region & edge

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-601 | Atlas multi-region | PL | 5–7 | E-309 | backlog |
| E-602 | API regional routing + RTT budgets | PL + RT | 4–6 | E-601 | backlog |
| E-603 | Realtime edge evaluation (ADR-001 addendum) | RT | 4–6 | E-301 | backlog |
| E-604 | DR / failover playbook + quarterly game day | PL | 3–4 | E-601 | backlog |
| E-605 | Dual-region signaling SLO compliance | RT | 3–4 | E-602 | backlog |

### Y2Q3 — Mobile & integrations

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-701 | Mobile ADR (RN vs Capacitor vs PWA+) | GR | 2–3 | — | backlog |
| E-702 | Mobile GA core meeting + classroom flows | GR + MT + CL | 10–14 | E-701 | backlog |
| E-703 | Camera/mic permission UX + degraded modes | GR + MT | 3–4 | E-702 | backlog |
| E-704 | LTI 1.3 integration | CL + GR | 6–8 | E-205 | backlog |
| E-705 | Calendar ICS + Google/Outlook | GR + MT | 5–7 | — | backlog |
| E-706 | Webhooks GA (sign, retry, DLQ) | GR | 3–4 | — | backlog |
| E-707 | Public API keys + partner rate limits | GR + PL | 4–5 | E-409 | backlog |

### Y2Q4 — Growth & polish

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-801 | Teacher analytics product | CL | 6–8 | E-308 | backlog |
| E-802 | Classroom templates / starter packs | CL + Design | 3–4 | — | backlog |
| E-803 | SecretMeet moderation **or** sunset | MT + GR | 3–6 | — | backlog |
| E-804 | WCAG audit + remediation critical flows | Design + all | 4–6 | — | backlog |
| E-805 | Localization EN + 1–2 locales | GR + product | 5–7 | — | backlog |
| E-806 | Cost per MAU reporting | PL + PM | 2–3 | E-505 | backlog |

---

## Standing / always-on (not quarter-locked)

| ID | Epic | Squad | Cadence |
|----|------|-------|---------|
| E-901 | Security review / pen test remediation | PL + RT | Quarterly |
| E-902 | Design system evolution | Design + MT/CL | Continuous |
| E-903 | Reliability debt (15% Platform capacity) | PL | Continuous |
| E-904 | Hiring & leveling | EM | Continuous |

---

## Pull order guidance (Y1Q1 first month)

1. E-106, E-101 (parallel)  
2. E-110, E-108  
3. E-105, E-102  

---

## Related

- [OKRS_Y1.md](./OKRS_Y1.md) / [OKRS_Y2.md](./OKRS_Y2.md)  
- [ORG.md](./ORG.md)  
- [../adr/](../adr/)  
