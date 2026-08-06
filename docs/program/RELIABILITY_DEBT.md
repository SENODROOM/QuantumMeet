# Reliability debt log (E-903)

Cadence: spend ~15% Platform capacity. Log items as they are paid down.

| Date | Item | Owner | Result |
|------|------|-------|--------|
| 2026-08-07 | Event-bus payload caps + idle poll | RT | Shipped |
| 2026-08-07 | Fail-closed DB for stateful APIs | PL | Shipped |
| 2026-08-07 | Mesh-only media policy (`/api/sfu/health`) | RT | Shipped |
| | Mongo connection storm under Vercel concurrency | PL | Open |
| | Presence stale GC under multi-tab races | RT | Open |

Do not close this epic — it is continuous capacity, not a feature.
