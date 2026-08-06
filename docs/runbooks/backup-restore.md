# Atlas backup / restore drill (E-210)

## Cadence

Quarterly restore drill. Record date + owner in the table below.

| Date | Env | Owner | Result | Notes |
|------|-----|-------|--------|-------|
| _TBD_ | staging | | | |

## Backup

1. Atlas → Cluster → Backup → ensure continuous cloud backup **on**.
2. Confirm retention ≥ 7 days (prod target ≥ 30 if budget allows).
3. Snapshot policy matches RPO in `docs/program/OKRS_Y1.md`.

## Restore drill (staging)

1. Pick a point-in-time ≤ 24h ago.
2. Restore to a **new** cluster or temp DB name `quantummeet-restore-drill`.
3. Point staging `MONGO_URI` at restored DB (or local tunnel).
4. Run `npm run synthetic:health` + create room + classroom join.
5. Revert URI; delete restore cluster.

## Cost glance

- Atlas backup $/mo vs cluster tier — note in quarterly cost review (E-806 later).
- Vercel Blob storage for recordings — purge policy TBD (E-207 retention).
