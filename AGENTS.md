# Agent Guide — DotProgress

Instructions for AI coding agents working in this repository.

Read and **implement** [.progress/README.md](.progress/README.md). That file is the single source of truth for the Dot Progress convention — entry types, subfolder layout, naming, immutability, YAML frontmatter template, and when to append progress files.

Entries live in type subfolders: `.progress/milestone/` (`M{n}.{index}.*`), `.progress/general/` (`G{number}.*`), `.progress/fixes/` (`F{number}.*`). Milestone index is three-digit per milestone; General/Fix use a global six-digit counter per prefix.

This repo also ships the optional agent-harness layer that enforces the convention automatically:
- [.claude/rules/dotprogress.md](.claude/rules/dotprogress.md) — path-glob rule (loads on `.progress/**` / `ROADMAP.md`)
- [.claude/skills/dotprogress/SKILL.md](.claude/skills/dotprogress/SKILL.md) — append-an-entry skill

For project context, see [README.md](README.md).
