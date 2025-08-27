# CLI Specification – `provision-tenant`

Goal: idempotent, scriptable onboarding of new tenants (Vison first), minimizing manual steps and enabling batch provisioning for 7+ motels, gas stations, and resorts.

## Command Synopsis
```
provision-tenant --name <string> --slug <string> --domain <domain> \
  [--stage-domain <domain>] [--theme <preset>] [--locale <pt-BR|en-US>] \
  [--timezone <IANA>] [--owner-email <email>] [--connect-gbp] [--connect-ga4] \
  [--email-provider <provider>] [--email-api-key <secret>] \
  [--seed-pages] [--seed-suites] [--seed-promos] [--import-reviews] \
  [--dry-run] [--yes]
```

## Required Flags
- `--name`: Display name (e.g., "Vison Motel").
- `--slug`: URL‑safe identifier (e.g., `vison`).
- `--domain`: Custom production domain (e.g., `hotelvison.com`).

## Common Optional Flags
- `--stage-domain`: Staging subdomain (e.g., `vison.projectv.app`).
- `--theme`: Brand preset (e.g., `oasis-secreto`).
- `--locale`: Default locale for website copy, default `pt-BR`.
- `--timezone`: IANA timezone (e.g., `America/Sao_Paulo`).
- `--owner-email`: Create owner account and send invite.
- `--connect-gbp`: Begin GBP linking workflow.
- `--connect-ga4`: Create/attach GA4 property/stream; set measurement ID.
- `--email-provider`: `mailchimp|sendgrid|rdstation`.
- `--email-api-key`: Secret for provider integration (or read from env).
- `--seed-pages`: Create default pages/blocks.
- `--seed-suites`: Seed suites/amenities from template.
- `--seed-promos`: Seed default promotion(s).
- `--import-reviews`: Initial GBP reviews import.
- `--dry-run`: Print plan only; no changes.
- `--yes`: Non‑interactive; accept defaults.

## Exit Codes
- `0` success; `1` generic error; `2` validation; `3` network; `4` auth/permission.

## Idempotency
- Safe to re‑run: checks existence by `slug` and `domain` before create.
- Upserts for theme, pages, suites, promos.
- Retries with exponential backoff on transient errors.

## Workflow (Happy Path)
1. Validate flags and environment (API keys, permissions).
2. Create or fetch tenant by `slug`.
3. Domains: ensure staging domain (if provided) and production domain records; request SSL; poll status.
4. Theme: apply preset and brand assets if present.
5. Seeders: pages/blocks, suites/amenities, promotions/coupons (CPF rules), media placeholders.
6. Integrations: GBP link (init OAuth/device flow), GA4 attach (set measurement ID), email provider connect.
7. Reviews: import initial GBP reviews (if requested).
8. SEO readiness: enqueue SEO audit; report actionable items.
9. Output summary and next steps.

## API Interactions (conceptual)
- `POST /api/admin/tenants` { name, slug, locale, timezone }
- `POST /api/admin/tenants/{id}/domains` { host, type: staging|prod }
- `POST /api/admin/tenants/{id}/theme` { preset, colors, typography }
- `POST /api/admin/tenants/{id}/seed/pages`
- `POST /api/admin/tenants/{id}/seed/suites`
- `POST /api/admin/tenants/{id}/seed/promos`
- `POST /api/admin/tenants/{id}/integrations/gbp:init`
- `POST /api/admin/tenants/{id}/integrations/ga4:attach` { measurementId }
- `POST /api/admin/tenants/{id}/integrations/email:connect` { provider, apiKey }
- `POST /api/admin/tenants/{id}/reviews/import` { source: GBP }
- `POST /api/admin/tenants/{id}/audits/seo`

## Logging & Observability
- Structured JSON logs with `tenant_id`, `slug`, and operation names.
- Progress bars/spinners with verbose `--debug` mode.
- Emit metrics: provisioning duration, retries, failures by step.

## Security
- Read secrets from env or secrets manager; do not log sensitive values.
- RBAC: only admins can provision; audit trail of actions.

## Examples
- Vison Motel (stage first, then prod):
```
provision-tenant --name "Vison Motel" --slug vison \
  --stage-domain vison.projectv.app --domain hotelvison.com \
  --theme oasis-secreto --locale pt-BR --timezone America/Sao_Paulo \
  --owner-email gerente@hotelvison.com --connect-ga4 --seed-pages --seed-suites --seed-promos --yes
```
- Provision promo‑heavy tenant with reviews import:
```
provision-tenant --name "Motel Jardim" --slug jardim --domain moteljardim.com.br \
  --seed-pages --seed-suites --seed-promos --import-reviews --yes
```

## Future Extensions
- `--vertical`: `motel|gas-station|resort` to pick seeders.
- `--import-media <path>`: bulk upload and tag assets.
- `--gbp-location-id`: shortcut to bind reviews without discovery.
