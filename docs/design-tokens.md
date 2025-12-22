# Design tokens (v1)

Denne guiden beskriver hvordan Loopwish bruker design tokens som felles “kontrakt” mellom plattformer.

Mål:
- Samme semantiske roller på tvers av web/Android/iOS/Windows.
- UI-kode bruker kun semantiske roller (stabilt API), ikke rå fargeverdier.
- Tokens kan utvikles (palett/tema) uten at UI må refaktoreres.

## Source of truth

- Canonical fil: `design-tokens/tokens.json`
- Denne filen versjoneres via git tags i `shared` (SemVer `vX.Y.Z`). Konsument-repoer pin’er en tag i `.loopwish/shared.ref`.

## Modell: primitives vs semantic

- **Primitives**: rå verdier (palett), f.eks. hex-farger.
- **Semantic**: roller basert på intent (text/surface/action/border/state). Dette er det UI skal konsumere.

## V1 semantic roles (stabil kontrakt)

V1 definerer følgende fargeroller (14 nøkler). Disse skal finnes i både `light` og `dark`.

1. `color.text.primary`
2. `color.text.secondary`
3. `color.text.onAccent`
4. `color.surface.canvas`
5. `color.surface.elevated`
6. `color.surface.accent`
7. `color.border.default`
8. `color.border.focus`
9. `color.action.primary.bg`
10. `color.action.primary.fg`
11. `color.action.secondary.fg`
12. `color.state.hover`
13. `color.state.pressed`
14. `color.state.disabled`

## Komponentguide (minimal)

Dette er en praktisk oppskrift for konsekvent UI på tvers av plattformer.

### Button

- Primary:
  - Bakgrunn: `color.action.primary.bg`
  - Tekst/ikon: `color.action.primary.fg`
- Secondary (lenke/ghost):
  - Tekst/ikon: `color.action.secondary.fg`
  - Border (valgfritt): `color.border.default`
- Focus:
  - Fokusmarkering: `color.border.focus`
- Interaksjon:
  - Hover: `color.state.hover`
  - Pressed: `color.state.pressed`
  - Disabled: `color.state.disabled`

### Text

- Standard tekst: `color.text.primary`
- Sekundær tekst / metadata: `color.text.secondary`
- Tekst på aksent (f.eks. på primary button): `color.text.onAccent`

### Surface / Card

- App-bakgrunn: `color.surface.canvas`
- Kort/overflate: `color.surface.elevated`
- Aksent-overflate (f.eks. banner/markering): `color.surface.accent`
- Delere/outline: `color.border.default`

### Input + Focus

- Standard border: `color.border.default`
- Fokus border/ring: `color.border.focus`
- Tekst: `color.text.primary`
- Placeholder/sekundær: `color.text.secondary`

### Disabled (felles regel)

Bruk `color.state.disabled` konsekvent for “disabled” uttrykk (knapper, input, tekst der det gir mening). Unngå plattformspesifikke ad-hoc varianter.

## Endringer og kompatibilitet

- **Semantiske keys er kontrakt**: ikke rename/fjern i patch/minor.
- Deprecation: marker som deprecated (docs) i én minor, fjern først i neste major.
- Primitives kan endres oftere, så lenge semantic mapping holdes stabil.
