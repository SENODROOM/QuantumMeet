# ADR-001 — Realtime Signaling Strategy

- **Status:** Accepted (program baseline)  
- **Date:** 2026-08-07  
- **Squad:** Realtime & Media (Accountable); Platform (Consulted)  
- **Related epics:** E-301, E-603  

---

## Context

QuantumMeet must run on **Vercel serverless** for the HTTP API. Persistent Socket.io (or similar long-lived Node WebSocket servers) on Vercel is not a viable primary architecture. Media is **WebRTC P2P (mesh)** for small rooms; signaling and app events still need an out-of-band bus before data channels exist.

Early product iterations used managed pub/sub (Ably), then a **Mongo-backed event bus + short-poll / long-poll** (`RoomEvent`, presence, SecretMeet inbox) via Express REST. That pattern keeps the API serverless-compatible but has latency and load tradeoffs.

## Decision

1. **Primary app API** remains dual Vercel projects: `client/` SPA + `server/` Express.  
2. **Primary signaling / fan-out (Year 1)** remains **Mongo event bus + HTTP poll/long-poll** (`GET/POST /api/rooms/:roomId/events`, presence heartbeats). No Socket.io server on Vercel.  
3. **Do not** reintroduce a third-party pub/sub as the *required* production bus unless ADR-001 is amended with cost/SLO justification.  
4. **Year 1 exit for the bus:** published SLOs (p95 delivery), indexes, backpressure, load tests (see `docs/slo/signaling.md`, epic E-301).  
5. **Year 2:** If SLOs cannot be met with poll/long-poll under multi-region load, evaluate a **dedicated realtime edge** (e.g. Cloudflare Durable Objects, PartyKit-class, or regional Node fleet) — still **not** “Socket.io bolted onto Vercel Hobby/Pro as the only listener.” Record the choice as an **addendum** to this ADR.  
6. **Media** stays **WebRTC mesh** on this deploy ([ADR-002](./ADR-002-sfu-evaluation.md)); mesh does not replace app-level chat/host event persistence.

## Consequences

### Positive

- Fits serverless deploy and ops model already chosen.  
- Durable events and presence survive multi-instance deploys.  
- Clear ownership for Realtime squad without rewriting the Room socket-shaped client adapter overnight.

### Negative / risks

- Polling adds latency (~hundreds of ms) and Mongo QPS cost at scale.  
- Whiteboard and ICE bursts need coalescing and budgets (E-302).  
- Long-poll holds serverless execution time — must respect platform limits (cap wait ≤ ~25s).

### Compliance

- Event TTLs and retention must align with privacy epics (E-403).  
- Host actions remain authorized via room tokens, not client-trusted IDs alone.  

## Alternatives considered

| Alternative | Why not (for now) |
|-------------|-------------------|
| Socket.io on long-lived Node (Railway/Render) | Splits ops model; prior goal was Vercel serverless API |
| Ably / Pusher as required bus | Cost + vendor lock; removed by product direction |
| WebRTC data channels only | Cannot bootstrap mesh (chicken-and-egg) |

## Validation

- Load tests and SLO checks (`docs/slo/signaling.md`, `/api/health` metrics).  
- Y1Q3 go/no-go on long-poll/SSE (see `docs/slo/long-poll-gonogo.md`).  
- Amend this ADR if a dedicated edge is selected in Y2Q2 (E-603).

## Y2 edge addendum (E-603)

Trigger when dual-region poll RTT breaks signaling SLO. Options: edge workers for long-poll wake, or managed realtime edge. Keep media on WebRTC mesh (ADR-002) — no hosted SFU.

## References

- `server/lib/events.js`, `client/src/lib/realtimeClient.js`  
- [EPICS_BACKLOG.md](../program/EPICS_BACKLOG.md)  
- [OKRS_Y1.md](../program/OKRS_Y1.md)  
