# Epics Backlog — 24-Month Program

**How to use:** Squads pull epics into quarterly plans. Status values: `backlog` | `planned` | `in_progress` | `done` | `killed`.  
**Sizing:** Squad-weeks (see [CAPACITY.md](./CAPACITY.md)). Estimates are planning ranges, not contracts.

Finished light/stub work is **removed** from this list (not marked done) so squads do not re-pull it. Remaining rows need real production depth.

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

## Year 1 — remaining hard work

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-304 | SFU vendor spike (sandbox ≥30 peers, scorecard) | RT | 4–6 | — | backlog |
| E-305 | **ADR-002** accepted with chosen vendor | RT | 2–3 | E-304 | backlog |
| E-401 | SSO OIDC/SAML GA for orgs | GR | 6–8 | — | backlog |
| E-407 | Full E2E: join, chat, knock, grade, attendance | PL + QA | 5–7 | — | backlog |

*(Y1 stubs already in repo: `/api/sfu/*`, `/api/auth/oidc/*`, Playwright smoke/create/API stub specs, ADR-002 gates.)*

---

## Year 2 — remaining hard work

### SFU production

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-501 | SFU production cluster + deploy pipeline | RT + PL | 8–12 | E-305 | backlog |
| E-502 | Mesh default ≤N; SFU auto above threshold | RT + MT | 4–6 | E-501 | backlog |
| E-503 | Simulcast + bandwidth adaptation | RT | 5–7 | E-501 | backlog |
| E-504 | Reconnection / migration mesh ↔ SFU | RT | 4–6 | E-502 | backlog |

### Multi-region

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-601 | Atlas multi-region live | PL | 5–7 | — | backlog |
| E-602 | API regional routing + RTT budgets | PL + RT | 4–6 | E-601 | backlog |
| E-605 | Dual-region signaling SLO compliance | RT | 3–4 | E-602 | backlog |

### Mobile & integrations (GA)

| ID | Epic | Squad | Size (sw) | Depends | Status |
|----|------|-------|-----------|---------|--------|
| E-702 | Mobile GA core meeting + classroom | GR + MT + CL | 10–14 | — | backlog |
| E-704 | LTI 1.3 launch GA | CL + GR | 6–8 | — | backlog |

*(Removed after multi-squad push: E-402 SCIM defer note, E-505/506 stubs, E-603/604 docs, E-703/705–707 stubs, E-801–806 plans, E-701 ADR-004, PWA manifest, partner keys, ICS, webhook HMAC, classroom templates, media permission helpers.)*

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

1. E-304 SFU sandbox → E-305 ADR accept  
2. E-401 OIDC GA  
3. E-407 expand Playwright beyond stubs  
4. E-501 SFU production  

---

## Related

- [OKRS_Y1.md](./OKRS_Y1.md) / [OKRS_Y2.md](./OKRS_Y2.md)  
- [ORG.md](./ORG.md)  
- [CAPACITY.md](./CAPACITY.md)  
