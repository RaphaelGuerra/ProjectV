# Tenant Provisioning Runbook

Goal: onboard Vison Motel first, then replicate for 7+ motels, gas stations, and resorts with minimal manual steps.

## Prerequisites
- Admin access to SaaS panel and cloud (DNS/CDN/SSL, storage, DB).
- Brand assets (logo, colors, typography), amenities, pricing, and initial content.
- GBP and GA4 accounts (or invite to create/connect), email provider credentials.

## Steps (Happy Path)
1) Create Tenant
- In Admin > Tenants: New Tenant → name, legal info, default locale (pt-BR for website copy), timezone.
- Assign `tenant_id` (UUID).

2) Domains
- Choose subdomain: `vison.projectv.app` (staging) → later custom domain.
- Add custom domain (when ready): `hotelvison.com`.
- Trigger DNS automation + SSL issuance; verify status in Integrations.

3) Theme & Brand
- Upload logo; set colors/typography; select tone preset ("Oasis Secreto").
- Preview website skeleton (Home, Suites, Promotions, Contact, Location).

4) Content Seed
- Import suite types and amenities; prices and period rules (4/6/12h).
- Upload initial media to Media Library; tag by suite/mood.
- Generate initial copy using templates in `04-content-plan-ptBR.md`; review and publish.

5) Integrations
- Connect GBP: link account; set sync cadence; import initial reviews.
- Connect GA4: property + measurement ID; validate events.
- Connect Email Provider: API key; create default lists/tags.

6) Coupons & Promotions
- Create first promotion (e.g., 20% off 12h via CPF, exclusions for holidays).
- Validate CPF rule and redemption limits.
- Publish to Promotions page and hero banner.

7) SEO & Launch Readiness
- Run SEO Assistant audit; fix titles/metas/alt/schema.
- Verify Core Web Vitals on staging; image compression enabled.
- Smoke test GA4 events: `view_suite`, `apply_coupon`, `contact_click`.

8) Go‑Live
- Switch DNS to custom domain; confirm SSL green.
- Enable production caching and rate limits.
- Monitor dashboard KPIs and alerts for first 72 hours.

## Automation Hooks (to implement)
- CLI/Job: `provision-tenant --name "Vison Motel" --domain hotelvison.com --theme oasis-secreto`.
- IaC module for DNS/SSL; webhook to SaaS when certificate is ready.
- Seeder for pages/blocks, suites, default promos, and GA4 config.

## Post‑Provision Checklist
- Owner/Manager accounts created; RBAC confirmed.
- Content review workflow set; UGC anonymization default ON.
- Backup policy applied; retention windows configured.

## Replication Notes (other verticals)
- Gas stations: replace Suites → Services/Conveniences; promos by dayparts.
- Resorts: Suites → Room Types; add packages; longer content blocks.
