# Capacity Model — 25 Engineers / 24 Months

**Purpose:** Planning numbers for EM/PM. Revisit each quarter; do not over-commit above contingency.

---

## Inputs

| Assumption | Value | Notes |
|------------|-------|-------|
| Steady-state ICs | 25 | See [ORG.md](./ORG.md) hiring ramp |
| Working days / person / year | ~220 | Holidays, PTO, sick leave averaged |
| Productive eng hours / day | ~5 | 9–5 calendar minus meetings, review, slack, ops |
| Annual productive hours (at 25) | 25 × 220 × 5 ≈ **27,500** | |
| Two-year productive hours | ≈ **55,000** | |
| Contingency reserve | **20%** | Incidents, debt, ramp inefficiency, hiring |
| **Planned committed work** | ≈ **44,000 eng-hours** | Use this for epic sizing |

During ramp (Y1Q1–Q2), effective capacity is lower — plan ~60–70% of steady-state until headcount = 25.

---

## Hours by squad (steady-state year)

Equal split of 27,500 ≈ **5,500 hours / squad / year** (before contingency).  
After 20% contingency ≈ **4,400 hours / squad / year** of committed epic work.

| Squad | Committed hours / year | Rough squad-weeks / year |
|-------|------------------------|---------------------------|
| Realtime & Media | ~4,400 | ~22 weeks × 5 people (overlap parallelized) |
| Meetings Product | ~4,400 | same |
| Classroom / LMS | ~4,400 | same |
| Platform / Infra | ~4,400 | same |
| Growth / Identity / Mobile | ~4,400 | same |

**Squad-week** ≈ 5 people × 5 h × 5 days = **125 eng-hours**.  
A “4 squad-week epic” ≈ **500 eng-hours**.

---

## Estimation rules

1. Estimate epics in **squad-weeks**, not story points alone.  
2. Include: design review, implementation, tests, docs, rollout, on-call bake.  
3. Spikes: time-box (1–2 weeks); output = ADR or kill decision.  
4. Never book more than **80%** of a quarter’s committed hours (leave slack for interrupts).  
5. Platform gets a standing **15%** of its capacity for reliability debt every quarter.

---

## Quarterly capacity (at full 25)

| Quarter | Calendar weeks | Committed eng-hours (org) | Notes |
|---------|----------------|---------------------------|-------|
| Typical Q | ~13 weeks | ~27,500 / 4 ≈ **6,900** | After contingency already in yearly model use ~5,500–6,000 committed |
| Planning figure per Q | — | **~5,500–6,000** org-wide committed | Safer for Y1 |

**Y1Q1–Q2 (ramping):** use **3,500–5,000** org-wide committed hours per quarter until hiring completes.

---

## Two-year budget sketch (illustrative)

| Bucket | Share of 44k hours | Hours | Examples |
|--------|-------------------|-------|----------|
| Realtime & Media (incl. SFU Y2) | 22% | ~9,700 | TURN, bus SLOs, SFU prod |
| Meetings Product | 18% | ~7,900 | Room UX, recording, calendar |
| Classroom / LMS | 20% | ~8,800 | Gradebook, LTI, analytics |
| Platform / Infra | 20% | ~8,800 | Observability, multi-region, security |
| Growth / Identity / Mobile | 15% | ~6,600 | SSO, orgs, billing, mobile |
| Cross-cutting / buffer | 5% | ~2,200 | Pen tests, design system, program |

Adjust after each quarterly OKR review.

---

## What this is not

- Not a promise that AI or a single engineer “finishes Year 2.”  
- Not permission to mark epics done without [ORG.md definition of done](./ORG.md).  
- Not a substitute for financial budget (infra SFU cost is separate OpEx).

---

## Related

- [ORG.md](./ORG.md)  
- [OKRS_Y1.md](./OKRS_Y1.md)  
- [OKRS_Y2.md](./OKRS_Y2.md)  
- [EPICS_BACKLOG.md](./EPICS_BACKLOG.md)  
