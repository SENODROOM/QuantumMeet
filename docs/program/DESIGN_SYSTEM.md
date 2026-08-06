# Design system notes (E-902)

## Tokens (`client/src/App.css` `:root`)

| Token | Role |
|-------|------|
| `--bg` … `--surface4` | Surfaces |
| `--accent` / `--accent-d` | Primary actions |
| `--amber-text` | Warning copy on dark (contrast-safer) |
| `--space-1` … `--space-6` | Spacing scale |
| `--z-chrome` / `--z-overlay` / `--z-modal` | Stacking |
| `--font-ui` / `--font-head` / `--font-mono` | Type |

## Rules

- Prefer tokens over hard-coded hex in new UI.  
- Icon-only buttons need `aria-label`.  
- Focus: `button:focus-visible` already set globally.  

Revisit after major product surfaces change.
