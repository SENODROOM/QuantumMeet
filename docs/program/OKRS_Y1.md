# OKRs — Year 1 (Months 0–12)

**Outcome:** QuantumMeet is a shippable B2B education + meetings product (not a demo).  
**Owners:** Squad TLs commit KR owners monthly. Scores: 0.0–1.0 at quarter end.  
**Constraint:** Vercel serverless + WebRTC mesh + Mongo HTTP signaling (no hosted SFU).

Finished light work is **removed** from this file (not marked done). See [EPICS_BACKLOG.md](./EPICS_BACKLOG.md).

---

## Y1Q1 — Trust & call quality

### Company objective
O1: Pilots can complete reliable 2–8 person calls with trustworthy host controls.

| Key result | Squad | Target |
|------------|-------|--------|
| KR1.1 Call success rate (join → sustained media ≥2 min) on pilot networks | Realtime | ≥ 95% |
| KR1.2 Host-auth abuse incidents (spoofed host actions in prod) | Realtime + Meetings | **0** |
| KR1.3 Production TURN with credentials, health checks, runbook | Realtime | Live in staging + prod |
| KR1.4 Signaling p95 delivery latency under load test (agreed N rooms) | Realtime + Platform | SLO published + met in staging |
| KR1.5 P0 on-call rotation + paging for API/Realtime | Platform | Staffed, documented |
| KR1.6 CI: unit + Playwright smoke on every PR to main | Platform | Required checks green |

**Exit:** 2–8 person calls reliable; spoofed host impossible; P0 on-call exists.

---

## Y1Q2 — Classroom depth & org tenancy

### Company objective
O2: Paying pilot schools/tutors can run a semester classroom workflow.

| Key result | Squad | Target |
|------------|-------|--------|
| KR2.2 Scheduled posts publish reliably (cron + teacher UX) | Classroom + Platform | ≥ 99% on-time in staging soak |
| KR2.3 Orgs/workspaces with roles (owner/admin/teacher/student) | Growth | GA for pilots |
| KR2.4 Recording upload to Blob + retention policy enforced | Meetings + Platform | Policy documented + implemented |
| KR2.6 Backup/restore drill completed | Platform | Pass with written report |
| KR2.7 ≥ N pilot orgs active (N set by PM) | Growth + PM | Met |

**Exit:** Semester workflow runnable by pilots without engineering white-glove for happy path.

---

## Y1Q3 — Mesh quality & classroom trust

### Company objective
O3: Mesh holds for ~15 peers on Vercel; teachers trust attendance signals.

| Key result | Squad | Target |
|------------|-------|--------|
| KR3.6 Attendance automation teachers trust (report accuracy study) | Classroom | ≥ agreed accuracy |

**Exit:** Attendance accuracy study signed; soft-cap/mesh path already in product.

---

## Y1Q4 — Enterprise readiness v1

### Company objective
O4: First enterprise/pilot contracts can be signed without custom forks.

| Key result | Squad | Target |
|------------|-------|--------|
| KR4.1 SSO (SAML and/or OIDC) for orgs | Growth | Production for ≥1 pilot |
| KR4.3 Billing seats + per-org feature flags | Growth | Pilot billing live |
| KR4.5 Full E2E suite: join, chat, knock, grade, attendance | Platform + QA | Blocking on release |
| KR4.6 Chaos test (Mongo/Vercel failure modes) | Platform | Report + fixes filed |

**Exit:** Sales/legal can use standard packaging; no one-off forks for first contracts.

---

## Year-1 scoring ritual

1. Mid-quarter check (month 2 of Q): red/yellow/green per KR.  
2. End of Q: numeric score; misses feed next Q epic reorder.  
3. Do **not** mark KRs done based on scaffold PRs alone — remove the row when ops/pilot proof exists.

---

## Related

- [OKRS_Y2.md](./OKRS_Y2.md)  
- [EPICS_BACKLOG.md](./EPICS_BACKLOG.md)  
- [CAPACITY.md](./CAPACITY.md)  
