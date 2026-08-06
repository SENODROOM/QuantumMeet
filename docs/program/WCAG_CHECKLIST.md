# WCAG critical-flow audit checklist

## Flows to audit first

1. Home create/join meeting  
2. Room controls (mute, leave, chat, knock admit)  
3. Classroom login + assignment submit  
4. Org create/invite  

## Checks

- [x] Keyboard only (primary chrome: Home, Room controls, Classroom tabs)  
- [x] Visible focus (browser default + button outlines)  
- [x] Labels / `aria-*` on icon buttons (Room soft-cap dismiss, key controls)  
- [ ] Contrast ≥ 4.5:1 body text (spot-check remaining amber chips)  
- [x] Live regions for knock/toast (`role="status"` soft-cap + waiting UI)  

Remediate remaining contrast blockers before marketing “accessible classrooms.”
