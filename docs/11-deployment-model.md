# Deployment Model & Environments

## Environments
- Dev: fast iteration; preview deploys per PR; shared sandbox services.
- Stage: production‑like; load/caching enabled; limited tenant data; final QA.
- Prod: isolated; monitoring/alerts; backups & DR enabled.

## Frontend (Website)
- Build: Next.js static generation with on‑demand revalidation.
- Hosting: CDN edge; immutable assets; cache invalidation via webhooks.
- Domains: tenant subdomain in stage; custom domain in prod; SSL per domain.

## Backend (API & Jobs)
- API: autoscaled stateless services behind load balancer; health checks.
- Jobs: BullMQ/Redis workers; scale by queue depth; dead‑letter queues.
- Config: environment variables via secrets manager; per‑env overrides.

## Database & Storage
- PostgreSQL: managed service; PITR; read replicas (post‑MVP if needed).
- RLS with `tenant_id`; migrations forward‑only; automated.
- S3/R2: private buckets; signed URLs; derivative images via pipeline.

## CI/CD
- PR checks: lint, typecheck, tests, build; preview deploy for frontend.
- Main merges: auto deploy to stage; manual approval to prod.
- Rollbacks: versioned releases; blue‑green or canary for API; cache purge for frontend.

## Secrets & Config
- Secrets in KMS/Secrets Manager; rotation policy.
- Per‑tenant config stored in DB; no secrets in code.

## Monitoring & Alerts
- Uptime checks; error rates; latency; Core Web Vitals.
- On‑call rotations; incident comms templates.
