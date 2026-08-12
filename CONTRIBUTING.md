# Contributing to Vedastra Labs

Version: 1.0
Build Plan Version: v5.0
Checklist Version: v4.60
Last Verified Against Commit: N/A — see DOCUMENTATION-DEBT.md #1
Verification Date: 2026-08-12
Owner: Akhilesh Angadi
Lifecycle: Published

---

Vedastra Labs is a hybrid multi-repo workspace (ADR-001): each product, platform,
and infrastructure directory is its own git repository, cloned as siblings under the
`vedastra-workspace` umbrella. Start there — the workspace README explains the layout
and `setup.sh` clones what you need.

## Commit & branch convention

**Canonical source (do not restate elsewhere — Never Explain Twice, DOCUMENTATION-STANDARDS §3):**
the git **commit message format** (Conventional Commits — `type(scope): subject` + body + footers)
and the **branch strategy / `main` protection** rules live in one place:

→ **`VEDASTRA-BUILD-PLAN.md` → "Commit Message Format (Conventional Commits)"**
(in the `vedastra-workspace` umbrella repo).

In short: Conventional Commits, imperative subject ≤72 chars, a body explaining
*what & why* for non-trivial changes, and `Ref: ADR-NNN` / `Part-of:` footers.
Branch flow is `main ← release/* ← develop ← feature/* | fix/*`; `main` is
protected (PR required, no force-push, no deletion).

## Before you open a PR

- Read the repo's `README.md`, `CLAUDE.md`, and `STATUS.md` (per DOCUMENTATION-STANDARDS §18).
- Keep changes within one repo where possible; cross-repo changes go through `@vedastra/*` in `vedastra-platform`.
- Respect the non-negotiables: money is integer paise, every table has RLS, no journal/medical/financial text to external AI, no PWA, no Stripe/Supabase/Prisma.
- Run the local gate before pushing: `bash infrastructure/scripts/run-qa.sh`.

## Documentation

All documentation is governed by `DOCUMENTATION-STANDARDS.md` and indexed in
`DOCUMENTATION-MAP.md` (both in the umbrella repo). If your change alters behaviour,
update the docs in the same PR (Definition of Done, §19).

---

© 2026 Vedastra Labs. Private, pre-launch. PROPRIETARY.
