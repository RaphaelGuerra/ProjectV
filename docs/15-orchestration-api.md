# Orchestration API & Data Model

## Core Entities
- Task: id, tenant_id, type, status, priority, payload, created_at, updated_at, due_at, sla_hours, attempts, last_error
- Plan: id, tenant_id, name, goals, tasks[]
- Module: id, name (content, seo, promos, reviews, integrations), capabilities[]
- Event: id, tenant_id, type, metadata (e.g., seo_audit_ready), created_at

## Task Types (enum)
- CONTENT_UPDATE_HERO, CONTENT_WRITE_SUITE, SEO_AUDIT, SEO_FIX_META, PROMO_CREATE_COUPON,
  PROMO_LAUNCH_FLASH_SALE, REVIEWS_IMPORT_GBP, REVIEWS_CURATE_HIGHLIGHTS, UGC_MODERATE,
  INTEGRATION_VERIFY_GA4, GBP_SYNC_HEALTH, REPORT_MONTHLY_READOUT

## Status (enum)
- DRAFT, SCHEDULED, IN_PROGRESS, NEEDS_REVIEW, COMPLETED, FAILED, BLOCKED

## API (REST, conceptual)
- POST /plans { tenant_id, name, goals[] } → { plan }
- GET /plans/{id}
- POST /tasks { tenant_id, type, payload, priority, due_at } → { task }
- PATCH /tasks/{id} { status, payload?, priority?, due_at? }
- GET /tasks?tenant_id=&status=&type=&from=&to=
- POST /tasks/{id}/assign { module }
- POST /tasks/{id}/approve { note }
- POST /tasks/{id}/fail { error }
- POST /events { tenant_id, type, metadata }

## Webhooks (outbound)
- task.updated, plan.updated, event.created

## Scheduling & SLAs
- Cron rules per tenant and per task type.
- SLA policy table: e.g., PROMO_CREATE_COUPON = 2h; SEO_FIX_META = 48h.

## Security
- RLS by tenant; module‑scoped API tokens for executors.
- Audit log on plan/task changes.

## Example Payloads
- Create SEO Fix Task:
```
POST /tasks
{
  "tenant_id": "tnt_vison",
  "type": "SEO_FIX_META",
  "payload": {
    "page": "/suites/hidro-premium",
    "title": "Suítes com hidromassagem em Nova Iguaçu | Vison Motel",
    "meta": "Descubra conforto e discrição na Hidro Premium..."
  },
  "priority": 0.7,
  "due_at": "2025-09-05T18:00:00Z"
}
```
