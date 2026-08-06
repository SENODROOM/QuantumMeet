# ADR-004 — Mobile client strategy

- **Status:** Proposed  
- **Date:** 2026-08-07  
- **Squad:** Growth (Accountable); Meetings, Classroom (Consulted)  
- **Related:** Y2Q3 mobile OKRs  

---

## Context

QuantumMeet is a React web app (CRA) with WebRTC mesh + Mongo HTTP signaling. Teachers and students need a credible mobile path without rewriting the stack twice.

## Options

| Option | Fit | Risk |
|--------|-----|------|
| **PWA+** (enhance web) | Fastest; same codebase | iOS WebRTC / background limits |
| **Capacitor** wrap | Native shell, reuse React | Plugin surface for media |
| **React Native** | Best device APIs | Parallel product; highest cost |

## Decision (proposed)

1. **Y2Q3 default:** ship **PWA+** (installable, offline shell, permission UX) as GA mobile for meetings + classroom browse.  
2. Spike **Capacitor** only if PWA fails camera/mic or App Store requirement.  
3. Defer full **React Native** unless enterprise mobile SLA demands it (revisit after PWA+ GA).

## Consequences

- Invest in mobile WebRTC permission / degraded modes on web first.  
- Mesh WebRTC path stays web-first ([ADR-002](./ADR-002-sfu-evaluation.md)).  
- Do not fork classroom LMS into native for Y2.
