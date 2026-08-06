# ADR-003 — Multi-Region & Data Residency Direction

- **Status:** Accepted (single-primary now; expand when Atlas secondaries are provisioned)  
- **Date:** 2026-08-07  
- **Squad:** Platform / Infra (Accountable); Realtime, Growth (Consulted)  

---

## Context

Education and enterprise buyers expect **latency**, **availability**, and often **data residency**. QuantumMeet runs a primary Atlas cluster and dual Vercel projects. Region is exposed via `ATLAS_PRIMARY_REGION` / `QM_REGION` and `X-QM-Region`.

## Decision

1. **Production default:** single primary Atlas region; do not claim multi-region until secondaries are live.  
2. **Config ready:** `ATLAS_SECONDARY_REGIONS` + `/api/health.region.multiRegionConfigured` for ops.  
3. **API:** regional routing only after data layer supports it; measure RTT with `docs/slo/dual-region-signaling.md`.  
4. **Realtime bus:** co-locate with API region; if cross-region poll breaks SLOs, use ADR-001 edge addendum.  
5. **Media:** WebRTC mesh only ([ADR-002](./ADR-002-sfu-evaluation.md)); TURN/ICE via `/api/ice`.  
6. **DR:** quarterly restore drills per [backup-restore.md](../runbooks/backup-restore.md).

## Consequences

- Do not sell “EU-only” until residency is enforced.  
- Dual Vercel project model remains.

## References

- [EPICS_BACKLOG.md](../program/EPICS_BACKLOG.md)  
- [ADR-001](./ADR-001-realtime-strategy.md)  
