# ADR-002 — SFU Evaluation Criteria (Large Rooms)

- **Status:** Proposed (decision due Y1Q3 — epic E-305)  
- **Date:** 2026-08-07  
- **Squad:** Realtime & Media (Accountable); Meetings, Platform, Classroom (Consulted)  
- **Related epics:** E-304, E-305, E-501–E-506  

---

## Context

Full-mesh WebRTC scales poorly (O(n²) uplink). QuantumMeet classrooms and lectures need **tens to 100+** participants. Mesh remains appropriate for small meetings (soft cap ~8–12). An **SFU** (Selective Forwarding Unit) is required for large rooms. Choice of self-hosted vs managed and which stack (LiveKit, mediasoup, Daily-class, etc.) drives multi-year cost and ops.

This ADR defines **how we choose**, not the final vendor (final vendor is recorded when E-305 completes).

## Decision (process)

1. Keep **mesh default** for rooms with peer count ≤ `MESH_SOFT_CAP` / policy N.  
2. Use **SFU** when peer count ≥ `SFU_THRESHOLD` or room type = lecture/classroom large.  
3. App signaling (chat, host controls, knocks) stays on the **Mongo/HTTP bus** ([ADR-001](./ADR-001-realtime-strategy.md)); SFU carries **media** (and optionally data channels for high-rate UX later).  
4. Y1Q3: time-boxed spike (E-304) + sandbox demo ≥30 peers + **accept this ADR with a chosen vendor**.  
5. Y2Q1: production SFU path (E-501+).

## Evaluation scorecard (must fill before accept)

Score each candidate 1–5. Weight in parentheses. Minimum weighted average **3.5** to accept.

| Criterion (weight) | What “5” looks like |
|--------------------|---------------------|
| **WebRTC quality (20%)** | Simulcast, SVC or equivalent, stable under loss |
| **Ops fit (15%)** | Deploy/runbooks match Platform skill; multi-region story |
| **Cost at 100 concurrent (15%)** | Clear $/participant; predictable at pilot scale |
| **Recording / egress (10%)** | Server-side recording or clean export path |
| **Security (10%)** | Token auth, room isolation, no open TURN abuse |
| **Client SDK fit (10%)** | Works with React web; mobile path plausible |
| **Latency / region (10%)** | Deployable near users; measured RTT OK |
| **Vendor lock / exit (10%)** | Open protocol or export path; kill-switch possible |

### Candidates to spike (minimum)

1. **LiveKit** (OSS + cloud)  
2. **mediasoup** (self-host)  
3. **One managed API** (e.g. Daily-class or equivalent) as cost/ops baseline  

Add more only if spike capacity allows.

## Non-goals for SFU v1

- Replacing classroom REST/LMS with SFU data channels  
- Global anycast on day one (see [ADR-003](./ADR-003-multi-region.md))  
- Abandoning mesh for 1:1 and small groups  

## Consequences (once accepted)

- Platform owns SFU deploy/cost dashboards with Realtime.  
- Meetings owns UX for “you are in SFU mode” and quality indicators.  
- Classroom lecture mode defaults toward SFU thresholds.  
- Budget OpEx line item required before Y2Q1 production.

## Validation

- Sandbox: ≥30 peers, recorded demo, quality notes (E-305).  
- Production: opted-in orgs, cost dashboard, mesh↔SFU policy (E-501–E-505).  
- Update this ADR status to **Accepted** and add “Chosen vendor” section.

## Chosen vendor

_To be filled at end of E-305:_

- Vendor: _TBD_  
- Deploy mode: _self-host / cloud / hybrid_  
- Decision date: _TBD_  
- Sign-off: Realtime TL, Platform TL, EM  
- **Gate:** simulcast (or equivalent) required; sandbox ≥30 peers; scorecard ≥ 3.5  
- Token stub: `GET /api/sfu/token` (501 until vendor wired)

## References

- [ADR-001](./ADR-001-realtime-strategy.md)  
- [OKRS_Y1.md](../program/OKRS_Y1.md) Y1Q3 / [OKRS_Y2.md](../program/OKRS_Y2.md) Y2Q1  
- `FEATURE_SFU`, `SFU_THRESHOLD`, `SFU_VENDOR`  
- [SFU_SPIKE_NOTES.md](./SFU_SPIKE_NOTES.md)  
