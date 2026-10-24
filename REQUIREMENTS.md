# Threadly CRM — Ecommerce CMS Requirements

> This is your requirements file. State what you want here in plain language —
> be as vague or specific as you like. Claude will turn it into a design and
> implementation plan with you.

## One-line goal

Backend CMS for the Threadly ecommerce app (products, orders, customers, inventory).

## Who is it for

- Store admins/editors (TBC)

## Stack

- Storefront: **Expo / React Native** (API must be REST or GraphQL)

## Must have (MVP)

<!-- The things the product cannot ship without -->

- **Product catalog** — products, variants (size/color/price/stock), images, categories, tags
- **Full order lifecycle** — placed → paid → shipped → delivered/cancelled; line items, totals, payment status, returns/refunds
- **CRM side** — customer profiles, notes, tags, lead/customer status, communication & purchase history
- **Users & roles** — manage who logs into the app (admin vs editor), permissions
- Reference model: **inspired by Shopify** (catalog / orders / customers / staff model)
- **Catalog size: ~100 products** (small — no heavy search infra needed; plain Postgres + simple indexes)

## Nice to have (after MVP)

<!-- Things you want eventually, but don't block the first release -->

- 

## Constraints

<!-- Tech stack, budget, hosting, deadlines, existing systems it must talk to -->

- Storefront: Expo / React Native → backend must be API-first (REST or GraphQL)
- Database: **Supabase** (Postgres) as starter
- **Must remain portable** — possible future migration to a different database; avoid Supabase-only features in core logic
- Self-host vs managed: open (no strong preference yet)

## Decisions (log)

- **CMS: Payload CMS** — code-first, TypeScript collections in-repo, generated admin UI + REST/GraphQL API, runs against Postgres/Supabase. Chosen for control/repo ownership over Directus.
- **Payment gateway: TBD** — pluggable (order "paid" is a status transition: `manual` | `gateway_webhook`).
- **Auth split (expected):** app end-users → Supabase Auth; staff → Payload users.

## What it must NOT do

<!-- Explicitly out of scope, so it doesn't creep in -->

- 

## Integrations

<!-- Payment gateways, email, shipping, analytics, etc. -->

- **Payments: TBD** — no gateway decided yet. Order module must treat "paid" as a **status transition** with a reason (`manual` or `gateway_webhook`) so a gateway can be plugged in later without rework.

## Questions I still need to answer

<!-- Open questions — Claude can help you decide these -->

- 
