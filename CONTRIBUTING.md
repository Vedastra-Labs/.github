# Contributing to Vedastra Labs

Version: 1.0
Last Updated: 2026-08-21
Owner: Akhilesh Angadi
Lifecycle: Published

---

Vedastra Labs is a single monorepo containing 9 products, shared platform packages,
infrastructure, and internal tooling. Read `README.md` and `STATUS.md` before starting.

## Repo layout

```
Vedastra-Labs/
├── wealthos/ healthos/ careeros/ focusos/ learningos/ lifeos/ campusos/                ← B2C/B2B products (Next.js)
├── astra/               ← Developer platform (own Turborepo — see astra/CONTRIBUTING.md)
├── buds-ai-plus/        ← Android app (Kotlin — see buds-ai-plus/CONTRIBUTING.md)
├── vedastra-platform/   ← Shared @vedastra/* packages
├── vedastra-admin/      ← Internal admin console
├── vedastra-web/        ← Marketing website
├── yantra/              ← Internal AI ops OS
└── infrastructure/      ← Docker, scripts, QA
```

## Branch rules (strictly enforced by process)

| Branch | Rule |
|--------|------|
| `main` | **Never push directly.** Merged from `release/*` only. |
| `develop` | **Never push directly.** Merged via PR after review. |
| `feature/*` | Your working branch for new features. |
| `fix/*` | Your working branch for bug fixes. |
| `release/*` | Created by repo owner only for release prep. |

**All work goes into `feature/*` or `fix/*` branches. Open a PR to `develop`. The repo owner reviews and merges.**

## Commit message format (Conventional Commits)

```
type(scope): short subject ≤72 chars

Body — what changed and why (required for non-trivial changes).

Ref: ADR-NNN   ← if related to an architecture decision
```

Types: `feat` · `fix` · `chore` · `docs` · `test` · `refactor` · `style` · `perf`

Scope = product or package name (e.g. `wealthos`, `healthos`, `@vedastra/db`).

## Before you open a PR

1. **Read** the product's `product.config.ts` — it drives tenancy, billing, and build status.
2. **Run** the local QA gate: `bash infrastructure/scripts/run-qa.sh`
3. **Check** your branch is up to date with `develop` (rebase, don't merge).
4. **Verify** your PR description explains *what* and *why*, not just *what*.

## Non-negotiable rules

These are hard constraints — do not work around them:

- **Money = integer paise.** Never use floats for currency. `₹1 = 100 paise`.
- **RLS on every table.** All queries use `withRLS` / `withRLSTx` (Drizzle). Never bypass.
- **No `any` in TypeScript.** All inputs validated with Zod.
- **No PWA.** No service workers or web manifests.
- **No Stripe, Supabase, or Prisma.** Stack is Razorpay + self-hosted Postgres + Drizzle.
- **Privacy guard.** Journal text, medical data, and financial detail must never reach external AI or telemetry.
- **Web ⇄ Mobile parity.** Any user-facing web change must have a matching React Native screen in `@vedastra/mobile-ui`, or be explicitly logged as a mobile-parity backlog item.
- **No credentials in code.** Secrets live in `~/.local/bin/.env.bridge` and `.env.*` files (gitignored).

## Cross-product changes

Shared behaviour (auth, billing, events, design tokens) lives in `vedastra-platform/packages/`.
Do not duplicate platform logic inside a product — extend the platform package instead.

## Documentation

If your change alters user-facing behaviour, update the relevant docs in the same PR.
All docs are governed by `DOCUMENTATION-STANDARDS.md` and indexed in `DOCUMENTATION-MAP.md`.

---

© 2026 Vedastra Labs. Private, pre-launch. PROPRIETARY.
