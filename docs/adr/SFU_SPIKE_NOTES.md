# SFU vendor spike notes (E-304 light)

## Candidates

| Vendor | Pros | Cons |
|--------|------|------|
| LiveKit | OSS + cloud, good React SDK | Ops if self-host |
| mediasoup | Max control | Heavy DIY |
| Daily / similar managed | Fastest GA | Cost + vendor lock |

## Spike checklist (≥30 peers sandbox → E-305)

1. Token mint from QuantumMeet API (JWT → SFU room).
2. Publish/subscribe 30 synthetic or real peers.
3. Measure $/participant-hour vs mesh.
4. Confirm signaling stays on Mongo bus (ADR-001); SFU = media only.
5. Write ADR-002 decision: self-host vs managed.

## Scorecard draft (LiveKit first spike)

| Criterion | LiveKit (draft) | Notes |
|-----------|-----------------|-------|
| WebRTC quality | 4 | Simulcast solid |
| Ops fit | 4 | Cloud option reduces ops |
| Cost @100 | 3 | Measure in sandbox |
| Recording | 4 | Egress available |
| Security | 4 | Room tokens |
| Client SDK | 5 | React-friendly |
| Latency | 3–4 | POP dependent |
| Exit | 3 | Protocol portable-ish |

Fill mediasoup/Daily rows during E-304 before ADR-002 accept.
