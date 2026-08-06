# Security review cadence (E-901)

## Quarterly checklist — 2026-08-07 cycle

- [x] Dependency audit (`npm audit` client + server) — server: express/mongoose/rate-limit bumped; remaining blob/uuid need major bumps (tracked, no `--force`)  
- [x] Secrets not in git (`.env`, TURN, JWT) — `.gitignore` covers `.env`  
- [x] Host token revoke path smoke-tested — unit tests in `server/__tests__/roomAuth.test.js`  
- [x] Fail-closed DB still on for `/api/rooms`  
- [x] Rate limits active (not `RATE_LIMIT_STORE=memory` in prod)  
- [x] CORS allowlist matches prod domains  
- [x] SFU not introduced — media stays mesh on Vercel  
- [x] Pen-test findings triaged within 30 days — none open this cycle  

Log findings in the issue tracker; do not “fix” by disabling auth.

Next review: ~2026-11-07.
