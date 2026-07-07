# Dot Progress

Super lightweight **context engineering**: an append-only progress log (`.progress/`) that gives agents and humans a durable audit trail without the token or cognitive overhead of a heavy planning system.

## One-shot setup for any repo

If you are handing an agent only a repo URL and want this system implemented consistently, use this exact sequence:

1. Copy `.progress/README.md` from this repo into `<target-repo>/.progress/README.md`.
2. Copy `AGENTS.md` from this repo into `<target-repo>/AGENTS.md`.
3. Commit both files.
4. In your first agent prompt, include the bootstrap prompt below.

Bootstrap prompt (copy/paste):

> Implement Dot Progress exactly as specified in `.progress/README.md`.
> Treat `.progress/README.md` as authoritative if anything else conflicts.
> Keep `.progress/` tracked in git.
> For each meaningful session (including partial milestone progress, decisions, reversals, or fixes), append exactly one new file in `.progress/` using the strict naming and template rules. Never edit, rename, or delete existing progress files.

## What you get

| Piece | Purpose |
|-------|---------|
| [.progress/README.md](.progress/README.md) | The spec — entry types, naming, immutability, YAML frontmatter template, optional `research` metadata |
| [.progress/milestone/](.progress/milestone/) | Milestone entries (`M{n}.{index}.*`) — roadmap work |
| [.progress/general/](.progress/general/) | General entries (`G000001.*`) — meaningful non-milestone work |
| [.progress/fixes/](.progress/fixes/) | Fix entries (`F000001.*`) — bug fixes and regression repairs |
| [.claude/rules/](.claude/rules/) + [.claude/skills/](.claude/skills/) | *(optional)* Agent-harness layer that enforces the convention automatically |
| [ROADMAP.md](ROADMAP.md) | *(optional)* Example milestone plan scaffold |
| [AGENTS.md](AGENTS.md) | Tells agents to implement `.progress/README.md` |

Entries are grouped into **type subfolders**; `README.md` stays at the `.progress/` root. Milestone entries use a per-milestone three-digit index; General/Fix entries use a global **six-digit** counter per prefix.

**Plan elsewhere** (ROADMAP, specs, issues). **Record history here** (`.progress/`).

## Adopt in your project

1. Copy `.progress/README.md` and the `milestone/`, `general/`, `fixes/` subfolders into your repo's `.progress/` folder (create them if needed).
2. *(Optional, recommended)* Copy `.claude/rules/dotprogress.md` and `.claude/skills/dotprogress/` so your agent enforces the convention without being told each time.
3. Tell your agent: *"Follow `.progress/README.md`. Append an entry for meaningful work (including partial progress and key decisions)."*
4. Track `.progress/` (and `.claude/`) in git — do not gitignore them.

Optional: add `ROADMAP.md` and reference milestone names in each entry's frontmatter.

For portfolio-wide R&D analysis, you can also add the optional `research` frontmatter block described in `.progress/README.md` (model, harness, skills, token/cost/duration telemetry).

## No-ambiguity rules

These remove the most common implementation mistakes:

- `.progress/README.md` is the source of truth. If another doc conflicts, follow `.progress/README.md`.
- Milestone files are `.progress/milestone/M###.###.descriptor.md` (three-digit milestone + three-digit per-milestone index).
- General and fix files are `.progress/general/G######.descriptor.md` and `.progress/fixes/F######.descriptor.md` (single six-digit counter per prefix).
- Entries are append-only. Never edit, rename, delete, renumber, or backfill committed entries.
- Use `milestone: General` for `G` files and `milestone: Fix` for `F` files.
- Write an entry for partial milestone progress and consequential decisions, not only "fully complete" work.

## Example entries

- [.progress/milestone/M000.001.example-entry.md](.progress/milestone/M000.001.example-entry.md) — a Milestone entry
- [.progress/general/G000001.example-general-entry.md](.progress/general/G000001.example-general-entry.md) — a General entry
- [.progress/general/G000003.example-research-metadata-entry.md](.progress/general/G000003.example-research-metadata-entry.md) — a General entry with optional `research` metadata
- [.progress/fixes/F000001.example-fix-entry.md](.progress/fixes/F000001.example-fix-entry.md) — a Fix entry

## License

See [LICENSE](LICENSE).
