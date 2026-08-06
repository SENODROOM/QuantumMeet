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

*(Solo IC pulled these; rows removed so squads do not re-pull: E-101 TURN/`/api/ice`, E-106 request-id + structured logs, E-108 staging checklist + synthetic health.)*

### Y1Q2 — Classroom depth & org tenancy

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-205 | Orgs/workspaces + RBAC | GR | 6–8 | — | backlog |

*(Removed after multi-squad 30m push: E-201–E-204, E-206–E-211. API invite/role endpoints exist under growth; full org product UI remains E-205.)*

### Y1Q3 — Scale small rooms; prepare large rooms

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-304 | SFU vendor spike (LiveKit / mediasoup / managed) | RT | 4–6 | — | backlog |
| E-305 | **ADR-002** accepted + sandbox ≥30 peers | RT | 2–3 | E-304 | backlog |

*(Removed: E-301–E-303, E-306–E-310. Spike notes: `docs/adr/SFU_SPIKE_NOTES.md`.)*

### Y1Q4 — Enterprise readiness v1

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-401 | SSO SAML and/or OIDC for orgs | GR | 6–8 | E-205 | backlog |
| E-402 | SCIM stretch (or explicit defer) | GR | 3–5 | E-401 | backlog |
| E-403 | Retention + export/delete self-serve | GR + CL | 4–5 | — | backlog |
| E-404 | DPA templates + residency plan (legal + eng) | PL + GR | 2–3 | — | backlog |
| E-405 | Billing seats + per-org feature flags | GR | 5–7 | E-205 | backlog |
| E-406 | Admin console v1 | GR | 4–6 | E-205 | backlog |
| E-407 | E2E suite: join, chat, knock, grade, attendance | PL + QA | 5–7 | — | backlog |

*(Removed light docs: E-408, E-409 → `docs/runbooks/chaos.md`, `docs/program/PUBLIC_API_DRAFT.md`. Smoke/join e2e scaffolding left; E-407 stays until full suite.)*

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

## Pull order guidance (next)

Y1Q1 cleared. Solo IC next pulls from **Y1Q2** (classroom/meetings) and light **Y1Q3** realtime scale as capacity allows.

---

## Related

- [OKRS_Y1.md](./OKRS_Y1.md) / [OKRS_Y2.md](./OKRS_Y2.md)  
- [ORG.md](./ORG.md)  
- [../adr/](../adr/)  
