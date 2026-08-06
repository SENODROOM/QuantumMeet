# OKRs — Year 2 (Months 12–24)

**Outcome:** Reliable mesh rooms on Vercel + Atlas; multi-tenant orgs; mobile-usable; school-IT integrations.  
**Constraint:** No hosted SFU — media stays WebRTC mesh ([ADR-002](../adr/ADR-002-sfu-evaluation.md)).  
**Prerequisite:** Year-1 exits met or explicitly waived by EM + PM in writing.

Finished light work is **removed** from this file (not marked done).

---

## Y2Q1 — Mesh quality & soft-cap product

### Company objective
O5: Small/medium rooms stay high-quality mesh; hosts get clear soft-cap guidance.

| Key result | Squad | Target |
|------------|-------|--------|
| KR5.1 Soft-cap UX trusted by hosts | Meetings + Realtime | Dismissal + copy validated |
| KR5.2 Mesh simulcast / bandwidth adaptation | Realtime | Measurable quality gain |
| KR5.3 Reconnection under network flap | Realtime | ≥ agreed recover rate |
| KR5.4 Cost model $/MAU (Atlas + Vercel + TURN) | Platform | Dashboard live |

**Exit:** Soft-cap + mesh quality path validated; cost model tracked.

---

## Y2Q2 — Multi-region & realtime edge

### Company objective
O6: Latency and DR meet published SLOs for primary regions.

| Key result | Squad | Target |
|------------|-------|--------|
| KR6.1 Atlas multi-region deployed | Platform | Primary + secondary |
| KR6.2 API regional routing + RTT budgets | Platform + Realtime | Dashboards green |
| KR6.3 Dedicated realtime edge decision (if poll SLO missed) | Realtime | ADR-001 addendum |
| KR6.4 DR / failover playbook quarterly tested | Platform | Pass |
| KR6.5 Signaling p95 within SLO in two regions | Realtime | Met |

**Exit:** Multi-region readiness; failover drilled.

---

## Y2Q3 — Mobile & integrations

### Company objective
O7: Mobile clients and school IT integrations are production-grade.

| Key result | Squad | Target |
|------------|-------|--------|
| KR7.1 Mobile strategy ADR (RN vs Capacitor vs PWA+) accepted | Growth | Signed |
| KR7.2 Mobile GA for join + classroom teacher/student core flows | Growth + Meetings + Classroom | Store or PWA GA |
| KR7.3 LTI 1.3 OR calendar (ICS/Google/Outlook) in production | Classroom + Growth | ≥1 integration GA |
| KR7.5 Partner/public API with API keys + rate limits | Growth + Platform | External pilot using it |

**Exit:** At least one mobile path + one integration path in production use.

---

## Y2Q4 — Growth engine & polish

### Company objective
O8: Product is operable at scale with analytics, a11y, and clear SecretMeet fate.

| Key result | Squad | Target |
|------------|-------|--------|
| KR8.1 Teacher analytics (engagement, attendance trends, at-risk) | Classroom | GA for paid orgs |
| KR8.3 SecretMeet: moderation at scale **or** sunset decision | Meetings + Growth | Written decision executed |
| KR8.4 WCAG target level agreed + critical flows audited | Design + all product squads | Audit passed or remediated |
| KR8.5 Localization: EN + 1–2 locales | Growth + product | Shipped |
| KR8.6 Cost per MAU tracked | Platform + PM | Monthly report |

**Exit:** Y2 company outcome metrics on [ROADMAP.md](../../ROADMAP.md) met or variance explained.

---

## Year-2 executive metrics (carry from program)

| Horizon | Metric |
|---------|--------|
| M18 | Soft-cap mesh rooms stable; p95 signaling within SLO |
| M24 | Mobile GA; SSO GA; LTI or calendar in production; cost/MAU tracked |

---

## Related

- [OKRS_Y1.md](./OKRS_Y1.md)  
- [EPICS_BACKLOG.md](./EPICS_BACKLOG.md)  
- [../adr/ADR-002-sfu-evaluation.md](../adr/ADR-002-sfu-evaluation.md)  
