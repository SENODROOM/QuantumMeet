# Long-poll go/no-go

Run against a live API (local or staging):

```bash
# Short list latency (SLO: p95 < 300ms)
npm run load:events -- http://localhost:5000

# Long-poll hold (SLO: ≤ 15–20s wait)
LONG_POLL=1 npm run load:events -- http://localhost:5000
```

Interpret `verdict` in the JSON output.

| Result | Action |
|--------|--------|
| GO short + GO long | Keep Mongo long-poll as primary; defer SSE |
| NO-GO short | Index / Atlas / payload size — see `signaling.md` |
| NO-GO long only | Cap `wait`, reduce concurrency, or kill long-poll via `FEATURE_LONG_POLL=0` |

SSE is **not** required to exit this spike if long-poll meets SLOs under expected concurrency.
