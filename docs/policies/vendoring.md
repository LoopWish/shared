# Vendoring policy (shared → consumer repos)

Denne policyen beskriver hvordan andre repos (web/android/apple/windows/backend) konsumerer artefakter fra `shared` med minst mulig manuelt arbeid.

## Mål

- Konsument-repoer pin’er en bestemt `shared`-versjon via git tag.
- Konsument-repoer vendor inn artefakter i `vendor/shared/` med samme mappestruktur som i `shared`.
- Konsument-repoer skal ikke gjøre manuelle endringer i vendorede filer.

## Pinning (tags)

- `shared` tagges med SemVer: `vX.Y.Z`.
- Hvert konsument-repo har en fil: `.loopwish/shared.ref`
  - Filformat: én linje som inneholder tag (f.eks. `v0.1.0`).

## Vendored struktur (kontrakt)

I hvert konsument-repo:

- `.loopwish/shared.ref`
- `vendor/shared/` (speiler `shared/`-struktur)

Eksempel (minimum v1):

- `vendor/shared/design-tokens/tokens.json`
- `vendor/shared/assets/logos/*`

## Oppdateringsflyt (én PR per plattform)

1. `shared`: gjør endringer i tokens/assets.
2. `shared`: lag ny tag `vX.Y.Z`.
3. For hvert konsument-repo:
   - Oppdater `.loopwish/shared.ref` til ny tag
   - Re-vendor inn artefakter til `vendor/shared/...`
   - Åpne PR

## CI (første fase: warn)

I første fase skal CI gi advarsel dersom:

- `.loopwish/shared.ref` peker på en tag som ikke finnes.
- Vendoret innhold i `vendor/shared/...` ikke matcher innholdet i `shared` på den taggen.
- Repoet har vendoret inn filer utenfor allowlist.

Når alle plattformer er migrert kan dette strammes til “fail”.
