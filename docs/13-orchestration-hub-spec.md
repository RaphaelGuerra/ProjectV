# Orchestration Hub (Master Planner) – Specification

Purpose: central brain to plan, schedule, and delegate tasks across tenants (websites, content, promos, reviews), providing visibility, SLAs, and automation.

## Capabilities
- Planning: translate goals (traffic, bookings, SEO) into actionable task plans.
- Scheduling: time‑box and queue tasks; recurring schedules (e.g., monthly SEO audit).
- Delegation: dispatch to modules (Content, Promotions, Reviews, SEO, Integrations).
- State: track progress, outcomes, and KPIs per task and per tenant.
- Feedback: surface recommendations and blocked tasks; suggest next best actions.

## Task Lifecycle
1) Draft → 2) Scheduled → 3) In‑Progress → 4) Needs‑Review → 5) Completed → 6) Failed/Blocked

## Roles & Permissions
- Owner: approve plans, budgets, and publish actions.
- Manager: create/schedule tasks, moderate UGC/reviews.
- Editor: generate/edit content, propose promos.

## Inputs
- Tenant KPIs (GA4), SEO audits, review trends, inventory (suites/amenities), calendar (holidays), constraints (LGPD).

## Outputs
- Executed actions (new page section, promo live, reviews widget updated), reports (monthly readout), alerts.

## Modules (Executors)
- Content Module: generate/update page sections via templates; media gap insights.
- SEO Module: audit, fix metas/OG/schema, suggest keywords; apply with approval.
- Promotions Module: create coupons and flash sales; publish banners.
- Reviews/UGC Module: import, curate, anonymize, publish widgets.
- Integrations Module: GBP sync, GA4 events health, email list capture.

## Priority Model
- Weighted scoring: impact (KPI contribution), effort, urgency, freshness, seasonality.
- SLA targets per task type (e.g., Promo publish < 10 min; SEO fixes < 48h).

## Multi‑Tenant Operation
- Scope all tasks by `tenant_id`; enforce isolation; per‑tenant rate limits.
- Batch operations supported (e.g., run SEO audits for all tenants overnight).

## Observability
- Per‑task logs, correlation IDs; metrics for throughput, success rate, SLA adherence.
- Dashboards by tenant and module; alerting on backlogs and failures.

## UI Hooks
- Planner board (kanban) by status; calendar view for scheduled items.
- Quick actions and templates; approvals workflow; publish gates.

## Automation Examples
- If SEO score < threshold, create task batch to fix metas/alt/schema.
- If reviews rating drops, schedule curation and website highlights refresh.
- If promo engagement falls, propose new coupon variant and banner A/B test.

## Non‑Goals (MVP)
- Cross‑network social publishing; complex budget optimization.
