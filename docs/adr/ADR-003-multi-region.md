# ADR-003 — Multi-Region & Data Residency Direction

- **Status:** Proposed (detailed design Y1Q3–Y2Q2; epics E-309, E-601–E-605)  
- **Date:** 2026-08-07  
- **Squad:** Platform / Infra (Accountable); Realtime, Growth (Consulted)  

---

## Context

Education and enterprise buyers expect **latency**, **availability**, and often **data residency**. Today QuantumMeet assumes a single primary Atlas cluster and Vercel deployments with CORS for known frontends. Year-2 OKRs require multi-region Atlas, API routing, and DR drills.

## Primary region env

Set `ATLAS_PRIMARY_REGION` (e.g. `us-east-1`) in Platform runbooks so residency claims match the live cluster.

## Decision (directional)

1. **Y1:** Single primary region production; document PII map and residency *plan* (E-309, E-404). Do not fake multi-region.  
2. **Y2Q2:** Deploy Atlas **multi-region** (or equivalent) with clear primary write region and secondary read/failover strategy (E-601).  
3. **API:** Introduce regional routing only after data layer supports it (E-602); measure RTT budgets for poll/long-poll.  
4. **Realtime bus:** Prefer co-locating event storage with the API region; if cross-region poll RTT breaks SLOs, trigger ADR-001 addendum (dedicated edge) via E-603.  
5. **Media:** WebRTC mesh only on this deploy ([ADR-002](./ADR-002-sfu-evaluation.md)); TURN/ICE via `/api/ice`.  
6. **DR:** Quarterly failover game days (E-604); RPO/RTO published before enterprise contracts that require them.

## Consequences

- Platform capacity must reserve multi-region and DR work (see [CAPACITY.md](../program/CAPACITY.md)).  
- Growth/Compliance must not sell “EU-only” until residency is actually enforced.  
- Dual Vercel project model remains; region choice is env/project configuration, not a monorepo merge.

## Alternatives considered

| Alternative | Notes |
|-------------|-------|
| Stay single-region forever | Blocks enterprise; unacceptable for Y2 outcome |
| Active-active writes everywhere | High complexity; defer unless required |
| Customer-managed on-prem | Out of scope for first 24 months |

## Validation

- Y1: PII map + residency plan reviewed.  
- Y2: Multi-region live; game day pass; signaling SLO in two regions.

## References

- [OKRS_Y2.md](../program/OKRS_Y2.md) Y2Q2  
- [EPICS_BACKLOG.md](../program/EPICS_BACKLOG.md) E-601–E-605  
- [ADR-001](./ADR-001-realtime-strategy.md)  
