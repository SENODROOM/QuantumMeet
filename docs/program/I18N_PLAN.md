# Localization plan (E-805 light)

## Scope Y2

1. Extract user-facing strings for Home, Room chrome, Classroom tabs.  
2. Ship **EN** as source of truth.  
3. Add **1–2** locales (candidate: ES, UR) via `i18next` or lightweight JSON maps.  

## Rules

- No string concatenation for grammar  
- Dates via `Intl.DateTimeFormat`  
- Keep brand name “QuantumMeet” untranslated  

Defer full LMS content localization until classroom GA locales chosen by product.
