# Cost / MAU reporting (E-806 light)

## Inputs

| Cost driver | Source |
|-------------|--------|
| Atlas | Invoice / metrics |
| Vercel | Usage |
| TURN | Provider invoice |
| SFU (future) | `$/participant-min` × `sfuParticipantMinutes` metric |
| Blob | Storage + egress |

## Formula (draft)

`cost_per_mau = monthly_infra_usd / monthly_active_users`

Publish monthly in Platform cost review. Wire SFU estimate when E-505 counters are real.
