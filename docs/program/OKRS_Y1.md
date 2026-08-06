# OKRs — Year 1 (Months 0–12)

**Outcome:** QuantumMeet is a shippable B2B education + meetings product (not a demo).  
**Owners:** Squad TLs commit KR owners monthly. Scores: 0.0–1.0 at quarter end.

Scaffolding already in the monorepo is **input**, not Year-1 completion.

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
| KR1.7 Classroom live-session contract frozen (IDs, host token, attendance) | Classroom + Meetings | Spec signed |

### Squad focus
- **Realtime:** TURN, ICE policy, host token hardening, event-bus indexes/load tests  
- **Platform:** Observability, Redis/Upstash rate limits, staging = prod-like  
- **Meetings/Classroom:** Harden create/join; no silent DB soft-fail in prod  

**Exit:** 2–8 person calls reliable; spoofed host impossible; P0 on-call exists.

---

## Y1Q2 — Classroom depth & org tenancy

### Company objective
O2: Paying pilot schools/tutors can run a semester classroom workflow.

| Key result | Squad | Target |
|------------|-------|--------|
| KR2.1 Assignment → submit → grade → export path complete | Classroom | E2E tested |
| KR2.2 Scheduled posts publish reliably (cron + teacher UX) | Classroom + Platform | ≥ 99% on-time in staging soak |
| KR2.3 Orgs/workspaces with roles (owner/admin/teacher/student) | Growth | GA for pilots |
| KR2.4 Recording upload to Blob + retention policy enforced | Meetings + Platform | Policy documented + implemented |
| KR2.5 Mesh soft-cap productized (warn + guidance, not just console) | Meetings + Realtime | UX shipped |
| KR2.6 Backup/restore drill completed | Platform | Pass with written report |
| KR2.7 ≥ N pilot orgs active (N set by PM) | Growth + PM | Met |

**Exit:** Semester workflow runnable by pilots without engineering white-glove for happy path.

---

## Y1Q3 — Scale small rooms; prepare large rooms

### Company objective
O3: Mesh is solid for ~15; SFU path is a signed decision with sandbox proof.

| Key result | Squad | Target |
|------------|-------|--------|
| KR3.1 Long-poll/SSE strategy proven at load vs SLO | Realtime | Report + go/no-go |
| KR3.2 Whiteboard bandwidth budget enforced | Realtime + Meetings | Under budget at 8 peers |
| KR3.3 SFU vendor spike + **ADR-002 accepted** | Realtime | Signed |
| KR3.4 Sandbox SFU demo ≥ 30 peers | Realtime | Recorded demo |
| KR3.5 Breakout parity with critical host tools | Meetings | Checklist complete |
| KR3.6 Attendance automation teachers trust (report accuracy study) | Classroom | ≥ agreed accuracy |
| KR3.7 PII data map + SOC2-ready logging plan | Platform | Artifacts reviewed |

**Exit:** ADR-002 signed; ~15 mesh OK; 30+ peer SFU sandbox demo.

---

## Y1Q4 — Enterprise readiness v1

### Company objective
O4: First enterprise/pilot contracts can be signed without custom forks.

| Key result | Squad | Target |
|------------|-------|--------|
| KR4.1 SSO (SAML and/or OIDC) for orgs | Growth | Production for ≥1 pilot |
| KR4.2 Retention + export/delete self-serve for classroom users | Growth + Classroom | Documented + shipped |
| KR4.3 Billing seats + per-org feature flags | Growth | Pilot billing live |
| KR4.4 Admin console v1 | Growth | Used by pilot admins |
| KR4.5 Full E2E suite: join, chat, knock, grade, attendance | Platform + QA | Blocking on release |
| KR4.6 Chaos test (Mongo/Vercel failure modes) | Platform | Report + fixes filed |
| KR4.7 Public API draft + eng handbook published | Platform + PM | Published internally |

**Exit:** Sales/legal can use standard packaging; no one-off forks for first contracts.

---

## Year-1 scoring ritual

1. Mid-quarter check (month 2 of Q): red/yellow/green per KR.  
2. End of Q: numeric score; misses feed next Q epic reorder.  
3. Do **not** mark KRs done based on scaffold PRs alone.

---

## Related

- [OKRS_Y2.md](./OKRS_Y2.md)  
- [EPICS_BACKLOG.md](./EPICS_BACKLOG.md)  
- [CAPACITY.md](./CAPACITY.md)  
