# Threadly CRM — Project Context

_Last updated: 2026-10-24 · Stage: design/requirements (no application code yet)_

> Factual snapshot for resuming work. Items are labeled **confirmed** (decided)
> vs **planned** (designed, not built). Source of truth for scope: `REQUIREMENTS.md`.

## Current State

- Repository is at the **design / requirements** stage. No Payload project, app
  source, or database schema has been scaffolded yet.
- Repository contains only: `CLAUDE.md`, `AGENT.md`, `REQUIREMENTS.md`, and
  `docs/agent/*` (agent context files).
- **No `.git` repository is initialized.** (Verify before committing.)
- No `package.json`, no `payload.config.*`, no source tree — do not assume any
  module exists in code.

## Product

- Backend CMS for the **Threadly** ecommerce app: products, orders, customers, inventory.
- Storefront client is **Expo / React Native**; the backend must be **API-first**
  (REST or GraphQL) and serve that client.
- Reference model: **Shopify-inspired** (catalog / orders / customers / staff).

## Confirmed Technical Decisions

| Decision | Value | Status |
|---|---|---|
| CMS | Payload CMS — code-first TypeScript collections, generated admin UI + REST/GraphQL | confirmed |
| Database | Supabase (Postgres) as starter | confirmed |
| Portability | Must remain DB-portable; avoid Supabase-only features in core logic (possible future migration) | constraint |
| Catalog size | ~100 products (small) → plain Postgres + simple indexes; no heavy search infra | confirmed |
| Payments | Pluggable; order "paid" = status transition with reason `manual` \| `gateway_webhook` | confirmed pattern |
| Auth split | App end-users → Supabase Auth; staff → Payload users | expected (design) |
| Payment gateway | **TBD** — none chosen yet | open |

## Planned Domain Modules (designed, NOT yet built)

- **Catalog:** products, variants (size/color/price/stock), images, categories, tags.
- **Orders:** full lifecycle `placed → paid → shipped → delivered/cancelled`; line items, totals, payment status, returns/refunds.
- **CRM:** customer profiles, notes, tags, lead/customer status, communication & purchase history.
- **Users & Roles:** staff (admin vs editor) + permissions.

## Conventions

- **Code-first Payload:** collections are defined as TypeScript in-repo; no schema changes outside the repo.
- Keep core logic **DB-portable** (Supabase is a swappable starter, not a lock-in).
- **Payments stay pluggable** — never hardcode a gateway; "paid" is always a status transition with a reason.
- No heavy search infrastructure (catalog is small).

## Open Questions

- Payment gateway choice: **TBD**.
- Self-host vs managed hosting: open (no preference yet).
- Who the store admins/editors are: TBC.
- (`REQUIREMENTS.md` "Questions I still need to answer" is currently empty.)
