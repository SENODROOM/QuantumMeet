# Cost / MAU reporting

## Live endpoint

`GET /api/growth/cost/mau`

Env inputs: `COST_ATLAS_USD`, `COST_VERCEL_USD`, `COST_TURN_USD`, `COST_BLOB_USD`, `COST_MAU`.

## Formula

`cost_per_mau = monthly_infra_usd / monthly_active_users`

Publish monthly in Platform cost review. No hosted SFU line item — mesh + Vercel only.
