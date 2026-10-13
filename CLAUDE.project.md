# Project Context

This file is the project-specific context layer for this repository.

The reusable harness policy lives in `CLAUDE.md`; keep this file focused on the
actual product, codebase, team conventions, and commands for the project created
from the harness.

When guidance conflicts:
- Project behavior, domain rules, architecture, and commands in this file take
  precedence for project work.
- Harness routing, capability placement, and validation rules in `CLAUDE.md`
  still apply.

> **Template:** replace every `_italic placeholder_` below when you start a new
> project from this harness. Delete sections that don't apply.

## Project Overview

_One or two paragraphs: what the product is, who uses it, and the core problem it solves._

## Tech Stack

- **Frontend:** _framework, language, styling_
- **Backend:** _language, framework, runtime_
- **Storage:** _database / files / external services_
- **Packaging:** _package managers and lockfiles_
- **Deployment:** _how and where it runs_

## Repository Layout

Full structural reference: `docs/reference/folder-structure.md` (create it from
`docs/templates/reference-template.md`; keep it current when structure, routes,
schemas, or config change).

- **`_path/`** — _what lives here_
- **`docs/`** — docs-first source of truth: `docs/product-roadmap.md`,
  `docs/prd/`, `docs/plan/`, `docs/reference/`, `docs/decisions/`. `docs/draft/` is the
  user's personal scratch space — never read or act on it unless explicitly referenced.

## Commands

| Purpose | Command | Notes |
|---------|---------|-------|
| Install deps | _command_ | |
| Run locally | _command_ | |
| Build | _command_ | |
| Test | _command_ | |

## Code Conventions

1. **Docs-first:** Read `docs/product-roadmap.md` and the relevant PRD/plan before feature
   work; follow `docs/documentation-standard.md` for doc maintenance and the session-close
   checklist.
2. _Add project conventions here (imports, typing, module layout, naming, …)._

## Coding Principles (Karpathy guidelines)

Adapted from [andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills)
(MIT). Applies to every agent that writes or edits code. These rules trade some
speed for fewer mistakes; for Trivial-tier edits, use judgment.

**They add to the harness, never override it.** Routing, tiers, gates, retry
limits, skills, and the layman reply style in `CLAUDE.md` still win. If a
principle below seems to conflict with them, follow the harness.

1. **Think before coding.**
   - Say your assumptions out loud instead of silently guessing (in a
     Requirement Brief, tag them `[ASM]`).
   - If a request can mean two things, name both. Ask only when the choice
     really matters (the harness "genuine decision points" rule); otherwise
     pick the likely one, say so, and go.
   - If a simpler or safer approach exists, say so before building.
   - If something is unclear: read the relevant file first. Ask only if that
     doesn't answer it, and batch all questions into one round. Never invent.
   - Questions and assumptions shown to the user follow the layman style
     (numbered, one line each).
2. **Simplicity first.**
   - Build only what was asked. No "might need it later" features.
   - No abstractions (helpers, layers, config) for a single use.
   - Handle real failure and edge cases (the "execute" playbook requires it),
     but don't add guards for cases that truly can't happen.
   - Test: would a senior engineer call this overcomplicated? If 200 lines
     could be 50, rewrite it.
3. **Surgical changes.**
   - Touch only what the task needs. Don't reformat, rename, or "improve"
     nearby code.
   - Don't refactor code that already works.
   - Match the existing style, even if you'd write it differently.
   - Clean up only what *your* change made unused. Mention other dead code;
     don't delete it.
4. **Goal-driven execution.**
   - Turn the task into a check you can verify. Example: "fix the login bug"
     → "write a test that fails on the bug, then make it pass."
   - For multi-step work, write a short plan where each step has its own
     check. Keep it in your working notes (or the ad-hoc scratch path) —
     never rewrite existing PRDs/plans in `docs/`.
   - Loop until the checks pass, within the workflow's retry limit. Still
     failing after that? Stop and report — don't stop at "should work."

**Working if:** diffs contain only requested changes, fewer rewrites caused
by overbuilding, and questions come *before* mistakes, not after.

## Domain Rules

1. _Business rules, invariants, and data definitions the code must respect._

## Environment And Secrets

- _Which `.env` files exist, what they configure, and where their `.example` copies live._

## Testing And Definition Of Done

- _Test command(s) that must pass for touched code._
- Treat tests as part of implementation, not a follow-up task.
- Never rewrite intent docs (PRDs/plans) during coding — record divergences in
  `docs/decisions/` instead.
- After a coding task, run the session-close checklist in `docs/documentation-standard.md`
  and keep `docs/reference/` in sync with structural changes.
- Mark a roadmap item `shipped` only when its deliverables and acceptance criteria are
  fully implemented and passing.

## Operational Notes

- _Anything an agent should know to operate safely: generated data not to delete,
  boundaries between components, where metrics/logs live, etc._
