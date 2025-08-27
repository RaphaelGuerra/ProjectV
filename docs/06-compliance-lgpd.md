# Compliance (LGPD) & Cultural Sensitivity – Guidelines

## 1) Principles
- Data minimization; purpose limitation; transparency; security by design; tenant isolation.
- Portuguese is for website content only; all system docs/logs remain in English.

## 2) CPF Handling
- Default: store only a salted hash for deduplication and coupon validation.
- If storage of raw CPF is strictly required: tokenize and encrypt (AES‑256) with KMS; store keys/salts separately.
- Collect explicit consent with purpose and retention; provide opt‑out where applicable.
- Log all accesses and mutations; restrict via RBAC; periodic access reviews.

## 3) Data Subject Rights
- Provide mechanisms to access, correct, export (machine‑readable), and delete data.
- SLAs: acknowledge within 5 days; fulfill within 15–30 days depending on request complexity.

## 4) Retention & Deletion
- Configurable retention periods per tenant and data category (e.g., coupons 12–24 months).
- Automatic deletion/archival workflows; verified erasure with audit trail.

## 5) Security Controls
- HTTPS everywhere; HSTS; CSP on websites; rate limiting and WAF.
- Secrets management via KMS; per‑tenant encryption contexts for sensitive data.
- Regular dependency scanning; SAST/DAST in CI; vulnerability triage playbook.

## 6) Vendor & Integration Management
- DPA with processors (email providers, hosting, analytics); verify data localization terms.
- Minimal data sharing with Google APIs; avoid PII in analytics payloads.

## 7) Cultural Sensitivity & Content
- Enforce "discreto e romântico" tone; strictly no explicit content on websites.
- UGC moderation requires permission capture and default anonymization.
- Avoid exposing PII in reviews or screenshots; curate highlights only.

## 8) Incident Response
- Define severity levels; notify affected tenants; legal counsel escalation path.
- For PII exposure: contain, rotate secrets, forensic logs, regulatory notifications as required.

## 9) Documentation & Accountability
- Maintain DPIA for CPF workflows; change management with approvals.
- Appoint a privacy point of contact; provide tenant‑facing compliance summary.
