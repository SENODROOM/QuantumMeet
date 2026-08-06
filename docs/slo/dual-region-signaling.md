# Dual-region signaling SLO (E-605)

## Targets

| Metric | Single region | Dual region |
|--------|---------------|-------------|
| Event list p95 (no wait) | &lt; 300ms | &lt; 450ms either region |
| Long-poll hold | ≤ 20s | ≤ 20s |
| Cross-region RTT (API→Atlas) | n/a | budget &lt; 120ms preferred |

## Verify

```bash
# Primary
BASE_URL=https://api-primary.example npm run synthetic:health

# Secondary / preview
BASE_URL=https://api-secondary.example npm run synthetic:health

# Compare list latency
npm run load:events -- https://api-primary.example
npm run load:events -- https://api-secondary.example
```

Health JSON includes `region` from `ATLAS_PRIMARY_REGION` / `QM_REGION`.

## Fail

If secondary list p95 &gt; 450ms consistently → do not route users there; open E-603 edge evaluation.
