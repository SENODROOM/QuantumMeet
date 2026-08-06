# Localization

## Shipped

- Lightweight catalogs: `client/src/lib/i18n.js`  
- Locales: **EN**, **ES**, **UR**  
- Persist via `localStorage.qm_locale`  

## Usage

```js
import { t, setLocale, availableLocales } from '../lib/i18n';
setLocale('es');
t('home.create');
```

## Rules

- No string concatenation for grammar  
- Dates via `Intl.DateTimeFormat`  
- Keep brand name “QuantumMeet” untranslated  

Expand Home/Room/Classroom string coverage incrementally.
