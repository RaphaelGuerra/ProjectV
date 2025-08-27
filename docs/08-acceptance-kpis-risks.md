# Acceptance Criteria, KPIs & Risks – MVP

## Acceptance Criteria
- Website live on owned domain; mobile‑first; Core Web Vitals "Good" on key pages.
- Dashboard shows KPIs, SEO checklist, and integration health.
- Coupons via CPF function end‑to‑end with rules and tracking.
- Reviews widget live with curated content; UGC flow operational with permission.
- GA4 events populated for `view_suite`, `start_booking`, `apply_coupon`, `contact_click`, `booking_confirmed` (proxy) with tenant context.
- Admin can create/publish a promotion in under 10 minutes.

## KPIs (first 6 months)
- Traffic: +30% sessions to owned domain; source mix towards organic/direct.
- Conversion: +20% direct bookings (proxy); coupon apply/redemption rates >10% of bookings.
- Reputation: +0.2–0.4 average Google rating improvement; increased review volume.
- Experience: p95 LCP < 2.5s (mobile) key pages; uptime ≥99.5% (MVP).

## Monitoring & Reporting
- Weekly beta reviews; monthly performance readout (traffic, conversions, promos, reviews).
- Alerting on SEO regressions, slow pages, integration failures.
- Exportable reports (CSV/PDF); tenant/date filters.

## Risks & Mitigations
- Content Sensitivity: enforce templates, moderation queue, human review gate.
- SEO Ramp: invest in evergreen/local content; track leading indicators; quick‑win optimizations.
- Adoption: in‑product guidance, templates, checklists; minimize clicks to publish.
- Data Handling: LGPD controls, periodic privacy reviews, vendor DPAs.
- Third‑Party Dependencies: retries, circuit breakers, graceful degradation; regular status checks.
