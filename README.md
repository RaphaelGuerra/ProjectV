# ProjectV – Digital Presence Orchestration SaaS (MVP)

This repository contains documentation for an MVP focused on a dedicated website and a beta orchestration SaaS for Vison Motel (Nova Iguaçu), designed to scale to multiple motels. Documentation is in English; Portuguese is used only inside website content templates.

## Documentation Index
- [01 – Strategic Plan](./docs/01-strategic-plan.md)
- [02 – Functional Requirements (MVP)](./docs/02-functional-requirements.md)
- [03 – Dashboard Wireframes (Textual)](./docs/03-dashboard-wireframes.md)
- [04 – Website Content Plan (pt-BR templates)](./docs/04-content-plan-ptBR.md)
- [05 – Scalability Architecture](./docs/05-scalability-architecture.md)
- [06 – Compliance (LGPD) & Cultural Sensitivity](./docs/06-compliance-lgpd.md)
- [07 – Implementation Phases](./docs/07-implementation-phases.md)
- [08 – Acceptance Criteria, KPIs & Risks](./docs/08-acceptance-kpis-risks.md)
- [09 – Maintainability & Operations Standards](./docs/09-maintainability-ops.md)
- [10 – Tenant Provisioning Runbook](./docs/10-tenant-provisioning-runbook.md)
- [11 – Deployment Model & Environments](./docs/11-deployment-model.md)
- [12 – CLI: provision-tenant](./docs/12-cli-provision-tenant.md)
- [13 – Orchestration Hub (Master Planner) Spec](./docs/13-orchestration-hub-spec.md)
- [14 – Task Catalog](./docs/14-task-catalog.md)
- [15 – Orchestration API & Data Model](./docs/15-orchestration-api.md)
- [16 – Roadmap: hotelvison.com MVP](./docs/16-roadmap-hotelvison.md)

## Quickstart (Tenant Provisioning)
- Follow the runbook: [Tenant Provisioning](./docs/10-tenant-provisioning-runbook.md)
- Provision Vison first (staging subdomain, then custom domain).
- Connect GBP, GA4, and Email Provider; seed content using pt-BR templates.
- Create first promotion (CPF validation), run SEO audit, and go live.

## Notes
- MVP scope excludes social media API integrations; focus is website + orchestration panel.
- Architecture is multi‑tenant and LGPD‑compliant by design; see Scalability & Deployment docs.
