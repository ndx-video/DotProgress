# Roadmap (example)

Lightweight milestone plan for **your project**. This file defines **what** to build **when** and **done when** exit gates.

> **This is a scaffold.** Replace milestones, goals, and checklists with your own. Progress toward each milestone is recorded in [.progress/](.progress/) — not by editing this file's history, but by appending new entries (see [.progress/README.md](.progress/README.md)).

**Example project:** DotProgress reference repo — ships the Dot Progress spec and adoption scaffolds.

---

## M0 — Bootstrap

**Goal:** Repo layout, progress-log spec, and an example entry agents can copy.

**Done when:**
- [README.md](README.md) explains what Dot Progress is and how to adopt it
- [.progress/README.md](.progress/README.md) defines naming, immutability, and the YAML frontmatter template
- At least one example entry exists under `.progress/` (e.g. `M000.001.example-entry.md`)
- [AGENTS.md](AGENTS.md) and [CLAUDE.md](CLAUDE.md) point agents at [.progress/README.md](.progress/README.md)

**Out of scope:** Application code, CI, published packages

---

## M1 — Adoption polish *(example — customize)*

**Goal:** Make copy-paste adoption frictionless for other repos.

**Done when:**
- One-command or documented copy steps verified on a fresh repo
- Common agent prompts / snippets documented (optional)
- ROADMAP template clearly marked as an editable scaffold

**Out of scope:** Building a CLI installer, IDE plugins

---

## M2 — Optional extensions *(example — customize)*

**Goal:** Add only what your project actually needs.

**Done when:**
- *(Define your own checklist)*

**Out of scope:** *(Define explicitly)*

---

## Working convention

At the start of each milestone, bring into context:

1. This milestone's **Done when** checklist (above)
2. Latest entries in [.progress/](.progress/) for the current milestone (audit trail; append-only)

When work completes, append a progress file per [.progress/README.md](.progress/README.md):

- **Milestone work:** `M000.002.adoption-docs.md` — `M` + three-digit milestone, three-digit per-milestone index
- **General work:** `G000012.this-is-a-general-change.md` — `G` + six-digit global number
- **Fixes:** `F000003.fix-login-redirect.md` — `F` + six-digit global number

Never edit prior progress files.

**Plan here (ROADMAP). Record there (`.progress/`).**
