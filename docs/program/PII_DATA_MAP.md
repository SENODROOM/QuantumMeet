# Atlas capacity + PII map

## Capacity (starting points)

| Collection | Growth driver | Index notes |
|------------|---------------|-------------|
| `roomevents` | Signaling chatter | TTL / roomId+createdAt (see models) |
| `presences` | Heartbeats | roomId+userId+connectionId |
| `posts` / `submissions` | Classroom LMS | classroomId indexes |
| `auditlogs` | Host actions | time-bounded queries |

Watch Atlas Metrics: connections, opcounters, disk. Alert at 70% storage / CPU.

## PII data map (draft)

| Data | Where | Retention |
|------|-------|-----------|
| Display name / userId | Presence, chat, classroom members | Room/session scoped + LMS |
| Email (auth) | User accounts | Until account delete |
| Recordings (blob URL) | Audit + Blob | Until retention purge job |
| Invite codes | Classroom | Rotate via regenerate |

Do not log full JWT or TURN credentials.
