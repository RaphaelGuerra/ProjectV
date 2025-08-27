# Phased Development Roadmap – MVP Website: hotelvison.com

Scope: Launch a fast, SEO-ready, mobile-first website for Vison Motel (hotelvison.com), instrumented with GA4 and connected to the SaaS beta for content, promos, and reviews.

## Phase A – Foundations (Week 1)
- Domain & DNS: register/verify `hotelvison.com` (or mapped from approved domain).
- Hosting/CDN/SSL: provision static hosting + CDN; TLS cert automation.
- Repo setup: monorepo scaffold (apps/web, apps/api), TypeScript, ESLint/Prettier, CI.
- Design tokens: colors/typography aligned to "Oásis Secreto" preset.
- Analytics: GA4 property + measurement ID placeholders.
- Acceptance: domain resolves over HTTPS; CI green.

## Phase B – Website MVP Skeleton (Weeks 2–3)
- Pages: Home, Suites (listing + detail), Promotions, Contact, Location.
- Components: Header, Footer, Hero, SuitesGrid, ReviewsWidget (placeholder), PromoBanner, CTA buttons.
- Routing/SEO: clean URLs, titles/meta/OG per page, sitemap.xml & robots.txt.
- Performance: image optimization; lazy loading; Core Web Vitals budget.
- Acceptance: navigable skeleton; lighthouse ≥90 performance on Home.

## Phase C – Content & Media (Weeks 3–4)
- Copy: pt‑BR content using templates (`04-content-plan-ptBR.md`); tone validation.
- Media: upload optimized images; initial 360° placeholders where planned.
- Structured data: LocalBusiness/LodgingBusiness schema, breadcrumbs.
- Acceptance: all key pages populated; schema valid in Rich Results Test.

## Phase D – Promotions & Coupons (Week 4)
- Promo UI: promotions page and sitewide banner placement.
- Coupon apply flow: CPF validation client→API (mock/initial service), non‑cumulative rules.
- Acceptance: test promo visible; apply coupon event logged; basic rule validation.

## Phase E – Reviews & GBP (Week 5)
- GBP integration: import recent reviews (server job or manual seed for MVP).
- Reviews widget: curated highlights display with filters.
- Acceptance: reviews visible; moderation toggles present.

## Phase F – Analytics & Events (Week 5)
- GA4 events: `view_suite`, `start_booking`, `apply_coupon`, `contact_click`, `booking_confirmed` (proxy).
- Data layer helpers; debug view validation.
- Acceptance: events visible in GA4 with tenant context.

## Phase G – SEO Hardening & QA (Week 6)
- SEO Assistant run; fix metas/alt/schema/internal links.
- Accessibility: WCAG 2.1 AA checklist on key pages.
- Performance: p95 LCP < 2.5s mobile; TTFB < 400ms cached.
- Acceptance: lighthouse ≥90 across PWA (if applicable), SEO, best practices.

## Phase H – Go‑Live (End of Week 6)
- Final checks: 404/500 pages, redirects, cache headers, security headers (CSP/HSTS).
- DNS cutover; SSL verify; smoke test.
- Acceptance: production parity with staging; monitoring/alerts active.

## Phase I – Post‑Launch (Weeks 7–8)
- Dashboard: connect to SaaS beta (status, SEO, promos, reviews) for ongoing ops.
- A/B tests: hero copy/CTA; banner placements.
- Report: first weekly readout; backlog for iteration.

## Deliverables by Phase
- Code (web) with CI green and preview deploys.
- Content (pt‑BR) published; assets optimized.
- Integrations: GA4, GBP reviews; coupon flow.
- Docs updates: change log, runbook for update/publish.

## Risks & Mitigations
- Content delays → use templates + interim imagery; staged publishing.
- DNS/SSL delays → start early; fallback to staging subdomain.
- Performance regressions → budgets enforced in CI; image pipeline checks.

## Out of Scope (this MVP)
- Social media APIs; complex booking engine.
- Full orchestrator automation (manual triggers acceptable during MVP).
