# Cost / MAU reporting (E-806 light)

## Inputs

| Cost driver | Source |
|-------------|--------|
| Atlas | Invoice / metrics |
| Vercel | Usage |
| TURN | Provider invoice |
| Blob | Storage + egress |

## Formula (draft)

`cost_per_mau = monthly_infra_usd / monthly_active_users`

Publish monthly in Platform cost review. No hosted SFU line item — mesh + Vercel only.
