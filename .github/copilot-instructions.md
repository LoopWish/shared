# GitHub Copilot Agent Instructions (Shared)

This repository contains shared assets and specifications for Loopwish (design tokens, brand assets, API specs, docs).

## Organization-wide standards (Loopwish)

- Keep PRs small and reviewable; avoid drive-by refactors.
- Do not commit secrets (API keys, tokens, credentials) or `.env` files.
- Prefer secure-by-default changes; avoid logging sensitive data.
- Update docs and specs when behavior changes.
- Keep CI green and validate formats before opening a PR.
- Follow the existing conventions; avoid breaking published paths.

## Goals

- Keep assets and specs consistent, predictable, and easy to consume.
- Prefer additive changes; avoid breaking paths (other repos link to assets in this repo).

## Conventions

- Design tokens live in `design-tokens/`.
- Brand assets live in `assets/`.
- API specs live in `api-spec/`.
- Keep filenames stable once published.

## Validation

- Ensure YAML/JSON is valid.
- Prefer simple, portable formats (SVG/PNG, JSON, YAML, Markdown).

## Safety

- Do not add copyrighted assets without permission.
- Do not include secrets.
