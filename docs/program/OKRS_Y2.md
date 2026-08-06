# OKRs — Year 2 (Months 12–24)

**Outcome:** Reliable mesh rooms on Vercel + Atlas; multi-tenant orgs; mobile-usable; school-IT integrations.  
**Constraint:** No hosted SFU — media stays WebRTC mesh ([ADR-002](../adr/ADR-002-sfu-evaluation.md)).

Finished light work is **removed** (not marked done).

---

## Y2Q2 — Multi-region & DR

### Company objective
O6: Latency and DR meet published SLOs for primary regions.

| Key result | Squad | Target |
|------------|-------|--------|
| KR6.1 Atlas multi-region deployed | Platform | Primary + secondary |
| KR6.2 API regional routing + RTT budgets | Platform + Realtime | Dashboards green |
| KR6.4 DR / failover playbook quarterly tested on live Atlas | Platform | Pass with restore |
| KR6.5 Signaling p95 within SLO in two regions | Realtime | Met |

**Exit:** Multi-region readiness; failover drilled on real clusters.

---

## Y2Q3 — Mobile & integrations (production proof)

### Company objective
O7: Mobile and school IT integrations used in production.

| Key result | Squad | Target |
|------------|-------|--------|
| KR7.2 Mobile GA — PWA installed by pilot teachers/students | Growth + Meetings + Classroom | Real usage |
| KR7.3 LTI 1.3 **or** Google/Outlook calendar sync in production | Classroom + Growth | ≥1 external platform |

**Exit:** At least one mobile path + one external integration in real use.

---

## Y2Q4 — Polish remaining

### Company objective
O8: Accessibility contrast + remaining enterprise polish.

| Key result | Squad | Target |
|------------|-------|--------|
| KR8.4 Contrast ≥ 4.5:1 on remaining amber chips / body text | Design + product | Audit closed |

**Exit:** Marketing can claim accessible classrooms without contrast exceptions.

---

## Related

- [OKRS_Y1.md](./OKRS_Y1.md)  
- [EPICS_BACKLOG.md](./EPICS_BACKLOG.md)  
- [../adr/ADR-002-sfu-evaluation.md](../adr/ADR-002-sfu-evaluation.md)  
