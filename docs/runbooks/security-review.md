# Security review cadence (E-901)

## Quarterly checklist

- [ ] Dependency audit (`npm audit` client + server)  
- [ ] Secrets not in git (`.env`, TURN, JWT)  
- [ ] Host token revoke path smoke-tested  
- [ ] Fail-closed DB still on for `/api/rooms`  
- [ ] Rate limits active (not `RATE_LIMIT_STORE=memory` in prod)  
- [ ] CORS allowlist matches prod domains  
- [ ] SFU not introduced — media stays mesh on Vercel  
- [ ] Pen-test findings triaged within 30 days  

Log findings in the issue tracker; do not “fix” by disabling auth.
