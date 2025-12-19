---
name: loopwish-openapi-contract
description: Maintain the Loopwish API contract: update the shared OpenAPI spec when backend endpoints change and keep backwards-compatibility in mind.
---

# Loopwish OpenAPI Contract Skill

Use this skill when changing backend API behavior or when clients need new/updated endpoints.

## Source of truth

- OpenAPI spec: `api-spec/openapi.yaml`

## When to use

- Adding/changing a REST endpoint in the backend.
- Clarifying request/response schemas for client teams.
- Reviewing an API change for backwards compatibility.

## Workflow: change an endpoint safely

1. Implement the backend change in the **backend repo**.
2. Update `api-spec/openapi.yaml` to reflect:
   - path + method
   - request body (if any)
   - response codes and JSON schemas
   - examples where helpful
3. Keep the spec consistent with real behavior (avoid “aspirational” fields).

## Versioning guidance

- The spec version currently matches the project version (`0.1.0`).
- Prefer additive changes (new optional fields, new endpoints).
- For breaking changes, coordinate a versioning strategy (e.g., `/v1` paths) rather than silently changing existing responses.

## Quick review checklist

- Do response schemas match actual JSON (types, required/optional)?
- Are error responses documented (4xx/5xx) where relevant?
- Are server URLs clearly marked as example/staging/production?

## Example prompts

- “I added `POST /wishes` in the backend—update the OpenAPI spec accordingly.”
- “Review this API change for backwards compatibility and propose a safer alternative.”
