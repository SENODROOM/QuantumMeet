# Attendance accuracy study

## Method

1. Run live session with known roster.  
2. Host calls `POST /api/classrooms/:id/attendance/from-presence`.  
3. Fetch `GET /api/classrooms/:id/attendance/accuracy`.  
4. Compare `avgRosterCoveragePct` to target (default **90%**, env `ATTENDANCE_ACCURACY_TARGET`).

## Pass criteria

- `meetsTarget === true` across ≥3 sessions in staging.  
- Teachers review sample absences (false positives from late joins).

## Notes

Presence-based attendance marks roster students absent when not in room; guests appear as present extras.
