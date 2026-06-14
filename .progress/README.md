# Dot Progress — progress log spec

Immutable audit trail for project work. Record **what happened and why** by **appending** new files — never edit, rename, or delete committed entries.

Tie entries to your project's milestones (typically from [ROADMAP.md](../ROADMAP.md) at the repo root, if you use one). This folder is **tracked in git**. Do not add `.progress/` to `.gitignore`.

## Filename convention (strict)

```
{milestone}.{index}.{descriptor}.md
```

| Segment | Format | Example |
|---------|--------|---------|
| `milestone` | `M` + milestone number **zero-padded to three digits** (`M000` = milestone 0, `M001` = milestone 1, …) | `M000`, `M002` |
| `index` | Three-digit zero-padded sequence **per milestone**, monotonic | `001`, `002`, `013` |
| `descriptor` | Lowercase kebab-case summary of **this entry only** | `example-entry` |

**Full example:** `M000.002.websocket-viewport-spec.md`

> Only the **filename** milestone token is zero-padded. Prose references (e.g. "M0 — Bootstrap", the `milestone` frontmatter field) may use your roadmap's short form.

### Index rules

- Each milestone has its **own** counter starting at `001`.
- Always use the **next** available index for that milestone (scan existing files in `.progress/`).
- Never reuse or renumber an index after a file is committed.
- Gaps are allowed; do not backfill.

### Descriptor rules

- Short, stable, human-readable slug.
- Describe **this** entry only (not the whole milestone).
- Regressions and reversals get **new** descriptors (e.g. `revert-auth-refactor`).

## Immutability (strict)

| Allowed | Forbidden |
|---------|-----------|
| Create a **new** file with the next index | Edit, rename, or delete an existing progress file |
| Document a regression as a **new** entry | "Fix" or overwrite a prior entry |
| Reference earlier entries by filename/link | Consolidate multiple events into one retroactive doc |

## When to write an entry

Create a progress document at the end of any session that:

- Completes or partially completes roadmap work
- Changes specs, architecture, or conventions
- Makes a decision future agents should understand
- Introduces a regression or reverts direction (say so explicitly)

Skip entries only for trivial typo fixes with zero design impact.

## Entry template

Copy into each new file:

```markdown
---
file: {filename}
date: YYYY-MM-DD
milestone: M{n} — {name from ROADMAP}
related_commits: {hash or uncommitted}
---

# M{n} — {short title}

## Summary

One paragraph: what happened and why.

## Changes

- Bullet list of artifacts touched

## Decisions

- Anything entailed for downstream work

## Follow-ups

- Open items, if any

## References

- Links to specs, prior progress entries, issues
```

See [M000.001.example-entry.md](M000.001.example-entry.md) for a filled-in example.

## Relationship to other docs

| Document | Role |
|----------|------|
| [ROADMAP.md](../ROADMAP.md) | **What** to build, milestone gates *(optional)* |
| [SITEMAP.md](../SITEMAP.md) | Where everything else lives |
| `.progress/` | **Historical record** of what was done, when, and why |

## Finding the next index

Before creating a file, list existing entries for the milestone:

```bash
ls .progress/M000.*.md
```

Use max(index) + 1. If none exist, start at `001`.
