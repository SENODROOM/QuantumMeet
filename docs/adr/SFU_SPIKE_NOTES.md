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

`FEATURE_SFU=0` until spike accepted. Soft-cap UX already warns hosts (E-209).
