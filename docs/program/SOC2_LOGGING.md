# SOC2-oriented logging / access

## Logging

- Prefer `server/lib/log.js` JSON lines with `requestId`.
- Never log passwords, tokens, ICE credentials, or full SDP.
- Health metrics are operational, not audit-grade.

## Access

- Classroom APIs: JWT required.
- Room host actions: host token + jti revoke.
- Cron: `CRON_SECRET` bearer.
- Prod secrets only in Vercel env / secret manager — not git.

## Next for full epic

Central SIEM drain, access reviews, change management evidence.
