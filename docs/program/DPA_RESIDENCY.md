# DPA / residency plan (E-404 light)

## Draft posture

- **Controller:** QuantumLogics (product operator).  
- **Processors:** MongoDB Atlas, Vercel, TURN provider, optional Sentry.  
- **Residency:** Primary region = Atlas cluster region chosen at provision (document in runbook). No multi-region until E-601.  
- **DPA:** Use Atlas/Vercel standard DPAs; customer DPA template TBD with legal.  

## Engineering obligations

- Fail-closed DB; no secrets in client for TURN (use `/api/ice`).  
- Retention purge + account export/delete endpoints.  
- PII map: `docs/program/PII_DATA_MAP.md`.

Legal must review before enterprise contracts.
