# Maintainability & Operations Standards

## 1) Code & Design Standards
- Language: TypeScript (strict mode). Prefer explicit types on public APIs.
- Naming: meaningful, full words; functions as verbs; variables as nouns. Avoid abbreviations.
- Control flow: guard clauses; shallow nesting; handle error/edge cases first.
- Comments: explain "why" (not obvious "how"); avoid inline noise.
- Formatting: Prettier; lint: ESLint with recommended + accessibility rules.
- Frontend: componentized UI, accessibility (WCAG 2.1 AA), server components where beneficial.
- Backend: modular NestJS modules; DTOs with validation; errors normalized.

## 2) Testing Policy
- Unit: Vitest for logic and API handlers.
- Integration: API routes and DB with ephemeral schema/containers.
- E2E: Playwright for critical flows (edit page, publish promo, apply coupon, review display).
- Accessibility: axe-core checks on key pages.
- Coverage target: 80% overall (≥90% for core services post-beta).

## 3) CI/CD & Branching
- Branching: trunk with feature branches; Conventional Commits (Commitizen) for messages.
- PR gates: lint, typecheck, unit/integration tests, build. Preview deploys for UI changes.
- Main branch: protected; required reviews; merge via squash.
- Releases: semantic versioning; changelog auto-generated.

## 4) Observability & Quality
- Logging: structured (JSON) with correlation IDs and tenant context.
- Metrics: request latency, error rates, queue depth; per-tenant breakdown where relevant.
- Tracing: OpenTelemetry for API and jobs.
- Frontend monitoring: Core Web Vitals; Sentry for errors.

## 5) Security & Secrets
- RBAC least-privilege; per-tenant data isolation enforced at query layer.
- Secrets via KMS; short-lived tokens; rotate regularly.
- CSP on websites; HTTPS/HSTS; WAF/rate limiting.

## 6) Data Lifecycle
- Backups: daily DB snapshots; PITR; test restores quarterly.
- Retention: configurable per data class; deletion workflows with audit logs.
- Migrations: forward-only; idempotent; blue/green compatible.

## 7) Performance Budgets
- p95 TTFB < 400ms (cached pages); p95 LCP < 2.5s on mobile for key pages.
- API p95 < 300ms for common reads; background jobs within SLA windows.

## 8) Documentation & Runbooks
- Keep docs in `/docs`; each module owns a README with setup/usage.
- Runbooks for tenant provisioning, incidents, on-call rotations.
