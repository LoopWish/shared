# Asset allowlist (v1)

Denne allowlisten definerer hvilke filer/paths fra `shared` som er tillatt å vendor inn i konsument-repoer under `vendor/shared/`.

## V1 allowlist

- `design-tokens/tokens.json`
- `assets/logos/loopwish-logo.svg`
- `assets/logos/loopwish-banner.svg`

## Retningslinjer

- Legg nye assets i `shared/assets/...` og oppdater allowlisten i samme PR.
- Hold allowlisten liten i starten for å unngå “asset creep”.
- Vurder å splitte i flere allowlists senere (f.eks. icons/images) når behovet er tydelig.
