# Classroom live-session contract

**Status:** Frozen for Y1  
**Owners:** Classroom + Meetings

## Flow

1. Teacher (JWT user) calls `POST /api/rooms` with:
   - `userId` — meeting peer id (may equal account id)
   - `hostName`
   - `isPublic: false`
   - `title`
   - `classroomId` — classroom id
   - `accountUserId` — JWT `user.id`
2. API persists `Room` and returns `{ roomId, hostToken, link }`.
3. Client stores `hostToken` at `localStorage qm_room_token_{roomId}` and `qm_host_{roomId}`.
4. Client creates `SessionLog` via `POST /api/classrooms/:classroomId/sessions` with same `roomId`.
5. Navigate to `/room/{roomId}?classroom={classroomId}`.
6. Host actions send `roomToken` + `userId` on every privileged REST call.
7. Attendance: `POST /api/classrooms/:classroomId/attendance/from-presence` with `{ roomId, sessionId }`.

## Invariants

- **Never** invent a client-side `roomId` different from `POST /api/rooms` response.
- Host privilege = valid **host** room JWT (`jti` not revoked), not `localStorage qm_host_*` alone.
- If Mongo is down, room create returns **503** `DB_UNAVAILABLE`.
- Rotate host token: `POST /api/rooms/:roomId/token/rotate` with current `roomToken`.

## Out of scope (later)

- Server-side recording egress  

