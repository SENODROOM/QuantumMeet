# Epics Backlog — 24-Month Program

Finished light work is **removed** (not marked done).

**Deploy constraint:** Vercel serverless + WebRTC mesh + Mongo HTTP signaling. **No hosted SFU (e.g. LiveKit).**

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

## Year 1–2 feature rows

*(Cleared — mesh/serverless path is the product. Soft-cap UX + browser simulcast helpers remain in code.)*

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

1. Remaining Y1Q1 OKRs (TURN live, SLO met, on-call, CI gates)  
2. Atlas/Vercel reliability (E-903)  
3. Security review cadence (E-901)  

---

## Related

- [ADR-001](../adr/ADR-001-realtime-strategy.md) · [ADR-002](../adr/ADR-002-sfu-evaluation.md) (mesh-only)  
- [ORG.md](./ORG.md) · [CAPACITY.md](./CAPACITY.md)  
