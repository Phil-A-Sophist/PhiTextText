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
- `source/main.ptx` — Root document; includes all other source files via xi:include
- `source/docinfo.ptx` — Document metadata, math macros (\N, \Z, \Q, \R), LaTeX image preamble (TikZ, PGFPlots)
- `source/frontmatter.ptx` — Title page, author info, copyright (CC BY-SA 4.0), colophon
- `source/ch-chapter-title.ptx` — Starter chapter ("Chapter Title"); includes sec-section-name.ptx
- `source/sec-section-name.ptx` — Starter section ("Section Title") with placeholder text
- `source/backmatter.ptx` — Back matter: placeholders for solutions, index, notation list, colophon

## Publication Files (publication/)
- `publication/publication.ptx` — Publication settings: chunking, TOC, exercise visibility, LaTeX options, HTML styling, numbering, WeBWorK, analytics

## CI/CD (.github/)
- `.github/workflows/pretext-cli.yml` — GitHub Actions: build on push/PR, deploy to Cloudflare Pages or GitHub Pages

## Memory System (.memory/)
- `.memory/instructions.md` — Memory consolidation agent instructions
- `.memory/state.md` — Current compressed project state (updated every task cycle)
- `.memory/project-map.md` — This file; index of all project files
- `.memory/knowledge-base.md` — Decisions, solutions, and accumulated knowledge
