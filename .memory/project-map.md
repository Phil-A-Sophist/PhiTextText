# Project Map — PhiTextText

## Root Files
- `project.ptx` — Project manifest defining build targets (web/HTML, print/PDF) and directory layout
- `requirements.txt` — Python dependency pin: pretext == 2.11.3
- `.gitignore` — Ignores output/, generated-assets/, editor configs, OS files
- `.devcontainer.json` — GitHub Codespaces config; uses oscarlevin/pretext:full Docker image
- `LICENSE` — MIT License (Copyright 2022 Oscar Levin)
- `README.md` — Template README with Codespace setup instructions
- `GenerateAssetsHelp.md` — Help doc for switching Docker images for LaTeX/asset generation
- `CLAUDE.md` — Project configuration and conventions for Claude agents

## Source Files (source/)
- `source/main.ptx` — Root document; defines book "My Great Book" with subtitle; includes all other source files via xi:include
- `source/docinfo.ptx` — Document metadata, math macros (\N, \Z, \Q, \R), LaTeX image preamble (TikZ, PGFPlots)
- `source/frontmatter.ptx` — Title page, author info (placeholder), copyright (CC BY-SA 4.0), colophon
- `source/ch-chapter-title.ptx` — Starter chapter ("Chapter Title"); includes sec-section-name.ptx
- `source/sec-section-name.ptx` — Starter section ("Section Title") with placeholder text
- `source/backmatter.ptx` — Back matter: placeholders for solutions, index, notation list, colophon

## Publication Files (publication/)
- `publication/publication.ptx` — Publication settings: chunking, TOC, exercise visibility, LaTeX options, HTML styling, numbering, WeBWorK, analytics

## CI/CD (.github/)
- `.github/workflows/pretext-cli.yml` — GitHub Actions: build on push/PR, deploy to Cloudflare Pages or GitHub Pages

## Claude Integration
- `.claude/commands/memory-check.md` — Memory health check command
- `.claude/commands/memory-status.md` — Memory status display command
- `.claude/skills/memory-system/SKILL.md` — Memory system skill definition
- `.claude/settings.local.json` — Local Claude settings

## Memory System (.memory/)
- `.memory/state.md` — Current compressed project state (updated every task cycle)
- `.memory/project-map.md` — This file; index of all project files
- `.memory/knowledge-base.md` — Decisions, solutions, and accumulated knowledge
- `.memory/reference/project-context.md` — Project context extracted from CLAUDE.md during deployment
- `.memory/logs/.gitkeep` — Log directory placeholder
- `.memory/downloads/.gitkeep` — Downloads directory placeholder
