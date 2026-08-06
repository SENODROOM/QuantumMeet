# OKRs — Year 1 (Months 0–12)

**Outcome:** QuantumMeet is a shippable B2B education + meetings product (not a demo).  
**Constraint:** Vercel serverless + WebRTC mesh + Mongo HTTP signaling (no hosted SFU).

Finished light work is **removed** (not marked done).

---

## Y1Q1 — Trust & call quality

### Company objective
O1: Pilots can complete reliable 2–8 person calls with trustworthy host controls.

| Key result | Squad | Target |
|------------|-------|--------|
| KR1.1 Call success rate (join → sustained media ≥2 min) on pilot networks | Realtime | ≥ 95% (`GET /api/metrics/call-quality`) |
| KR1.2 Host-auth abuse incidents (spoofed host actions in prod) | Realtime + Meetings | **0** |
| KR1.3 Production TURN with credentials live in staging + prod | Realtime | `hasTurn: true` on `/api/ice` |
| KR1.4 Signaling p95 met under load in staging | Realtime + Platform | SLO green (`docs/slo/signaling.md`) |

**Exit:** Pilot call quality + TURN + staging SLO proven.

---

## Y1Q2 — Classroom depth & org tenancy

### Company objective
O2: Paying pilot schools/tutors can run a semester classroom workflow.

| Key result | Squad | Target |
|------------|-------|--------|
| KR2.2 Scheduled posts ≥ 99% on-time in staging soak | Classroom + Platform | Soak report |
| KR2.3 Orgs GA for pilots (`FEATURE_ORGS=1`) | Growth | ≥1 pilot org live |
| KR2.7 ≥ N pilot orgs active (N set by PM) | Growth + PM | Met |

**Exit:** Pilots run semester workflow without white-glove for happy path.

---

## Year-1 scoring ritual

1. Mid-quarter check: red/yellow/green per KR.  
2. Remove the row when ops/pilot proof exists (do not leave “done” markers).

---

## Related

- [OKRS_Y2.md](./OKRS_Y2.md)  
- [EPICS_BACKLOG.md](./EPICS_BACKLOG.md)  
