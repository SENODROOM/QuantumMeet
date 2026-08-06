# Staging ≈ prod checklist

## Parity requirements

| Item | Staging | Prod |
|------|---------|------|
| Mongo Atlas | Separate cluster/DB | Prod cluster |
| `JWT_SECRET` / `ROOM_TOKEN_SECRET` | Unique, strong | Unique, strong |
| `ICE_SERVERS` | Real TURN (can share pool) | Real TURN |
| `SENTRY_DSN` | Staging project | Prod project |
| `FEATURE_*` | Match prod flags | Source of truth |
| Vercel | Separate project or env | Production env |

## Synthetic check

From repo root / server:

```bash
BASE_URL=https://your-staging-api.vercel.app npm run synthetic:health
```

Expect exit 0: health `ok`, ice endpoint 200.

## Before promoting a build

1. Synthetic health green  
2. Two-browser join + chat + mute in staging  
3. Confirm fail-closed: kill staging Mongo briefly → `/api/rooms` returns 503  
4. Confirm `/api/ice` `hasTurn` matches prod intent  
