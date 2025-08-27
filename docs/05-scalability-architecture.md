# Scalability Architecture – Multi‑Tenant MVP (Conceptual)

## 1) Technology Stack (proposed)
- Frontend: Next.js (TypeScript), static generation + on‑demand revalidation; CDN caching.
- Backend: Node.js (NestJS, TypeScript), REST/GraphQL API; background jobs with BullMQ/Redis.
- Database: PostgreSQL 14+.
- Storage: S3/R2 for media; signed URLs; image optimization pipeline.
- Telemetry: GA4 for website; app logs/metrics via OpenTelemetry.
- Auth: Email+password; optional SSO; RBAC (owner/manager/editor).

## 2) Multi‑Tenancy Strategy
- Option A – Schema‑per‑tenant: highest isolation; operational overhead grows with tenants.
- Option B – Single schema with Row‑Level Security (RLS) by `tenant_id`: efficient scaling; strict policy reviews required.
- MVP recommendation: RLS with `tenant_id` and exhaustive automated tests; ability to promote VIP tenants to dedicated schema if needed.

## 3) High‑Level Data Model
- Tenant, Property (motel), Domain (custom + subdomain)
- Suite (types, features), MediaAsset (S3 key, tags)
- Promotion, Coupon (rules, limits, validity, CPF policy)
- Review (source: GBP), UGCSubmission (permission, anonymize)
- Integration (GBP, GA4, Email), EventLog (operational), User, Role

## 4) Events & Tracking (GA4)
- Custom events: `view_suite`, `start_booking`, `apply_coupon`, `contact_click`, `booking_confirmed` (proxy)
- Params: `tenant_id`, `suite_type`, `promotion_id`, `coupon_code`
- On the website: data‑layer helpers; on the backend: server‑side validation and sampling controls.

## 5) Provisioning & Operations
- Tenant provisioning: create tenant → assign subdomain → attach theme → connect integrations → seed default pages/blocks.
- Domains: DNS/SSL automation (e.g., Cloudflare/Let’s Encrypt) with per‑tenant certificates.
- Infrastructure as Code (IaC): Terraform or Pulumi; environments (dev/stage/prod) isolated.
- CI/CD: PR checks (lint/test/build), preview deploys, blue‑green/canary for backend.

## 6) Security & Compliance (architecture)
- RLS + RBAC enforcement at API; every query filtered by `tenant_id`.
- Secrets via KMS; per‑tenant encryption contexts for sensitive data (e.g., tokenized CPF).
- Signed URLs for media; private buckets by default; optional public derivatives.
- Audit logging for admin actions and data exports; immutable storage for critical trails.

## 7) Performance & Reliability
- Caching: CDN edge for pages/assets; Redis for API responses (short‑TTL) and rate limits.
- Budgets: p95 TTFB < 400ms (cached); p95 LCP < 2.5s mobile for key pages.
- Resilience: retries with backoff for third‑party APIs (GBP, email); circuit breakers.
- DR/Backups: daily snapshots; point‑in‑time recovery; cross‑region replication for S3.

## 8) Scalability Plan
- Horizontally scale stateless services; autoscale workers by queue depth.
- Shard large tenants if needed (promotion/coupon heavy usage); archive cold data.
- Observability dashboards per tenant; SLOs and error budgets.

## 9) Adaptation to Other Segments
- Abstract "Suite" → "Room Type"; promotion rules extensible; coupon validators pluggable.
- Replace CPF flow with other identifiers where required; keep consent model modular.
