# Dot Progress

Super lightweight **context engineering**: an append-only progress log (`.progress/`) that gives agents and humans a durable audit trail without the token or cognitive overhead of a heavy planning system.

## What you get

| Piece | Purpose |
|-------|---------|
| [.progress/README.md](.progress/README.md) | The spec — entry types, naming, immutability, YAML frontmatter template |
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
3. Tell your agent: *"Follow `.progress/README.md`. Append an entry when work completes."*
4. Track `.progress/` (and `.claude/`) in git — do not gitignore them.

Optional: add `ROADMAP.md` and reference milestone names in each entry's frontmatter.

## Example entries

- [.progress/milestone/M000.001.example-entry.md](.progress/milestone/M000.001.example-entry.md) — a Milestone entry
- [.progress/general/G000001.example-general-entry.md](.progress/general/G000001.example-general-entry.md) — a General entry
- [.progress/fixes/F000001.example-fix-entry.md](.progress/fixes/F000001.example-fix-entry.md) — a Fix entry

## License

See [LICENSE](LICENSE).
