# Media scale notes (mesh on Vercel)

## Policy

Deploy target: **Vercel serverless** + **WebRTC mesh** + Mongo HTTP bus.  
**No hosted SFU** (LiveKit and similar are paid and excluded).

## Soft-cap

- `MESH_SOFT_CAP` (default 10): warn hosts/participants; do not block join.  
- Encourage fewer cameras / lower quality when near cap.

## Browser helpers

- Optional simulcast encodings on mesh publishers (`client/src/lib/simulcast.js`) — still P2P, no server media.  
