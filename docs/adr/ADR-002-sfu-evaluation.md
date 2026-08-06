# ADR-002 — Large-room media on Vercel (mesh policy)

- **Status:** Accepted  
- **Date:** 2026-08-07  
- **Squad:** Realtime & Media  
- **Related:** ADR-001 (Mongo/HTTP signaling)

---

## Context

QuantumMeet deploys **API + client on Vercel serverless**. Media is **WebRTC mesh (P2P)**. Hosted SFUs (LiveKit, Daily, etc.) are **out of scope** — they are paid/external services and not part of this serverless stack.

## Decision

1. **Media = WebRTC mesh only** for this product deployment.  
2. **Signaling = Mongo-backed HTTP poll/long-poll** on Vercel (ADR-001).  
3. Soft-cap UX warns hosts when peer count is high; do not auto-route to a paid SFU.  
4. Optional mesh simulcast/bandwidth helpers may run in the browser to reduce uplink load.  
5. Revisit a self-hosted/free SFU only if product explicitly changes deploy model off “Vercel-only.”

## Non-goals

- LiveKit / mediasoup Cloud / other paid SFU vendors  
- SFU token minting in this repo  

## Consequences

- Large rooms remain mesh-bound; product must set expectations (soft-cap messaging).  
- Cost model stays Atlas + Vercel (+ optional owned TURN), not SFU SaaS.  

## References

- [ADR-001](./ADR-001-realtime-strategy.md)  
- `MESH_SOFT_CAP`, `/api/sfu/health` (`policy: mesh_only`)  
