# Epics Backlog — 24-Month Program

**How to use:** Squads pull epics into quarterly plans. Status values: `backlog` | `planned` | `in_progress` | `done` | `killed`.  
**Sizing:** Squad-weeks (see [CAPACITY.md](./CAPACITY.md)). Estimates are planning ranges, not contracts.

Finished solo/multi-squad light work is **removed** from this list (not marked done) so squads do not re-pull it.

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

*(Cleared — last multi-squad push removed: E-304 SFU stub/scorecard, E-305 ADR-002 gates, E-401 OIDC stub, E-407 Playwright stub specs. Repo already has `/api/sfu/*`, `/api/auth/oidc/*`, e2e smoke/create/api-stubs.)*

---

## Year 2 — remaining hard work

### SFU production

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-501 | SFU production cluster + deploy pipeline | RT + PL | 8–12 | — | backlog |
| E-502 | Mesh default ≤N; SFU auto above threshold | RT + MT | 4–6 | E-501 | backlog |
| E-503 | Simulcast + bandwidth adaptation | RT | 5–7 | E-501 | backlog |
| E-504 | Reconnection / migration mesh ↔ SFU | RT | 4–6 | E-502 | backlog |

### Multi-region

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-601 | Atlas multi-region live | PL | 5–7 | — | backlog |
| E-602 | API regional routing + RTT budgets | PL + RT | 4–6 | E-601 | backlog |
| E-605 | Dual-region signaling SLO compliance | RT | 3–4 | E-602 | backlog |

*(Also removed from Y2 after last push: E-702 PWA manifest / mobile ADR path, E-704 LTI config stub — not full GA.)*

---

## Standing / always-on

| ID | Epic | Squad | Cadence |
|----|------|-------|---------|
| E-901 | Security review / pen test remediation | PL + RT | Quarterly |
| E-902 | Design system evolution | Design + MT/CL | Continuous |
| E-903 | Reliability debt (15% Platform capacity) | PL | Continuous |
| E-904 | Hiring & leveling | EM | Continuous |

---

## Pull order (next)

1. E-501 SFU production (build on existing `/api/sfu` stub)  
2. E-502 / E-503 media path  
3. E-601 Atlas multi-region  

---

## Related

- [OKRS_Y1.md](./OKRS_Y1.md) / [OKRS_Y2.md](./OKRS_Y2.md)  
- [ORG.md](./ORG.md)  
- [CAPACITY.md](./CAPACITY.md)  
