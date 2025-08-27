# Functional Requirements – MVP (Website + SaaS Beta)

## 1) Overview

The MVP delivers a centralized dashboard to orchestrate a dedicated website per motel, with SEO basics, AI‑assisted content tools, conversion features (coupons, reviews, UGC), and essential integrations (GBP, GA4, Email). Multi‑tenant design and LGPD compliance are foundational.

## 2) Core Feature: Centralized Website Panel

### 2.1 Status & Integrations
- Domain/SSL/CDN status; uptime pings.
- Google Business Profile (GBP) sync health; last import timestamp.
- GA4 heartbeat and event stream validation.

### 2.2 SEO Assistant (Basics)
- On‑page audit: title length, meta descriptions, H1–H3 presence, alt text, internal links.
- Keyword suggestions emphasizing local intent (e.g., “motel em Nova Iguaçu”, “suíte com hidro NI”).
- Evergreen topic suggestions (e.g., “Escapadas discretas na Baixada”).
- Snippet controls: meta, OG tags, schema.org (LocalBusiness/LodgingBusiness).

### 2.3 Performance & Funnels
- Metrics: sessions, sources, CTR to WhatsApp/call/map, event counts.
- Funnels: visit → interaction (suite view/contact click) → intent (start booking/apply coupon) → booking confirmed (proxy).
- Alerts: dips in key metrics, missing meta/alt, slow pages, broken links.

## 3) Core Feature: Website Content Generation (AI‑assisted)

- Text generation: suite descriptions, hero copy, banners, about, FAQs; tone: discreet, romantic, local charm.
- Visual guidance: banner ideas, photo shot‑lists, compression guidance; 360° pointers.
- Templates: Pages (Suites, Promotions, Contact, Location); promotions by period (4/6/12h).
- Media Library: upload, tag (suite type, mood), auto‑compression; gap insights.

## 4) Core Feature: Conversion & Loyalty

### 4.1 Discounts/Coupons
- Create/apply offers (e.g., “20% off 12h via CPF”), eligibility rules, urgency/flash sales.
- Validation: CPF‑based, non‑cumulative, holiday exclusions, usage limits, expirations.
- Tracking: redemptions by channel, cohorts, effective rates.

### 4.2 Reviews Aggregation
- Import Google reviews (configurable cadence), curate highlights, moderation workflow.
- Widgets: filters (recent, top‑rated, themed), schema markup for review snippets where appropriate.

### 4.3 UGC Moderation
- Intake (form/email), permission capture, optional anonymization, publish controls with audit trail.

## 5) Essential Integrations (MVP)

- **Google Business Profile (GBP)**: Listing details sync, review import, basic photo sync.
- **Email Marketing Provider** (e.g., Mailchimp/SendGrid/RD): Lead capture, simple automations (welcome, NPS, re‑engagement).
- **Coupons/Loyalty Module**: Native issuance/validation; outbound webhook for external POS validation (optional).
- **Google Analytics 4 (GA4)**:
  - Events: `view_suite`, `start_booking`, `apply_coupon`, `contact_click`, `booking_confirmed` (proxy).
  - Event params: `tenant_id`, `suite_type`, `promotion_id`, `coupon_code`.

## 6) UX/Design Requirements

- Drag‑and‑drop blocks for website sections; clear tooltips and inline suggestions.
- Accessible components (WCAG 2.1 AA), mobile‑first; Core Web Vitals “Good.”
- Simple, non‑technical language; undo/redo; previews (mobile/desktop).

## 7) Scalability & Compliance

- Multi‑tenant: either schema‑per‑tenant or row‑level security (RLS) keyed by `tenant_id`.
- Isolation of media via tenant‑scoped buckets/prefixes; signed URLs.
- LGPD: salted hash for CPF dedupe; tokenize/encrypt when storage is needed; consent logs; data minimization; retention policies; audit trails.

## 8) Non‑Functional Requirements

- Availability: 99.5% for MVP; target 99.9% post‑beta.
- Performance: p95 TTFB < 400ms (cached pages); p95 LCP < 2.5s on mobile for key pages.
- Security: RBAC with least privilege; secret rotation; dependency scanning; incident response runbook.

## 9) Out of Scope (This Phase)

- Social media APIs and advanced cross‑channel publishing.
- Complex booking engine integrations (use proxy events and simple contact/CTA flows).


