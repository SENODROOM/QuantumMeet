# Camera / mic permission UX (E-703 light)

## Modes

| Mode | Trigger | UX |
|------|---------|-----|
| Full | Permissions granted | Normal join |
| Audio-only | Video denied / fail | Join with mic; show “Enable camera” |
| View-only | Both denied | Join as spectator; chat/whiteboard if allowed |
| Blocked | Browser blocks permanently | Explain settings path; link to help |

## Client hooks

- Prefetch permission state before `getUserMedia` where supported  
- Never loop permission prompts after dismiss  
- Soft-cap / SFU banners must not obscure permission dialogs  

PWA+ (ADR-004) should reuse these modes.
