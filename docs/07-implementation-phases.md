# Implementation Phases – Website + SaaS Orchestration Beta

## Phase 1: Discovery & Structuring (Weeks 1–2)
- Activities: kick‑off, requirements, persona/brand guide, user journey, initial content & SEO strategy, conceptual tech selection.
- Checkpoints: approved brand guide, journey/funnel map, initial content plan.

## Phase 2: Foundation & Setup (Weeks 3–4)
- Activities: domain, hosting/CDN/HTTPS, GBP optimization/verification, GA4 baseline events, beta onboarding in panel, basic dashboard.
- Checkpoints: domain live, GBP verified, GA4 events flowing, dashboard accessible.

## Phase 3: Website MVP (Weeks 5–8)
- Activities: mobile‑first build, content population, SEO basics, coupons via CPF, email provider integration, reviews widget.
- Checkpoints: site responsive, coupons functional, media library populated, SEO audit green.

## Phase 4: SaaS Beta Activation (Weeks 9–12)
- Activities: performance panel, alerts, AI content tools, promo management/flash sales, UGC moderation, GA4 refinements, multi‑tenant rehearsal.
- Checkpoints: operational orchestration, SEO/content tools in use, promos & reviews live, actionable reports.

## Phase 5: Launch & Monitor (Weeks 13–14)
- Activities: QA, launch, KPI monitoring, feedback loop, maintenance plan.
- Checkpoints: website live, SaaS beta in use, first monthly report, launch checklist complete.

## Acceptance (per phase)
- Phase 3: Core Web Vitals "Good" (mobile) on key pages; coupon flow OK.
- Phase 4: Manager creates/publishes a promotion in < 10 minutes; reports clear.
- Phase 5: No critical post‑launch errors; p95 LCP < 2.5s (mobile) on key pages.

## Automation Addendum (Provisioning)
- CLI: `provision-tenant` to create tenant, attach theme, seed pages/suites/promos.
- IaC: DNS/SSL automation with webhook back to SaaS on certificate issuance.
- Seeder jobs: GA4 config, GBP sync setup, default reports and alerts.
