# Dot Progress

Super lightweight **context engineering**: an append-only progress log (`.progress/`) that gives agents and humans a durable audit trail without the token or cognitive overhead of a heavy planning system.

## What you get

| Piece | Purpose |
|-------|---------|
| [.progress/README.md](.progress/README.md) | The spec — naming, immutability, YAML frontmatter template |
| [.progress/M000.*.md](.progress/) | One file per meaningful session — what happened, what was decided |
| [SITEMAP.md](SITEMAP.md) | Documentation map scaffold for your repo |

**Plan elsewhere** (ROADMAP, specs, issues). **Record history here** (`.progress/`).

## Adopt in your project

1. Copy `.progress/README.md` into your repo's `.progress/` folder (create the folder if needed).
2. Copy or adapt [SITEMAP.md](SITEMAP.md) as your documentation index.
3. Tell your agent: *"Follow `.progress/README.md`. Append an entry when work completes."*
4. Track `.progress/` in git — do not gitignore it.

Optional: add `ROADMAP.md` and reference milestone names in each entry's frontmatter.

## Example entry

See [.progress/M000.001.example-entry.md](.progress/M000.001.example-entry.md) for a filled-in template.

## License

See [LICENSE](LICENSE).
