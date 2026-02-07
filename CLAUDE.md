# CLAUDE.md - Project Configuration for PhiTextText

## Overview

PhiTextText is a **PreTeXt** authoring project -- a structured XML-based system for writing mathematical and scientific textbooks that can be compiled to multiple output formats (HTML, PDF, EPUB, braille). The project was generated from the official PreTeXt Codespace template (by Oscar Levin) and currently contains a starter book titled "My Great Book" with placeholder content ready to be replaced with real material.

PreTeXt source files use the `.ptx` extension and are written in a custom XML vocabulary designed for academic publishing.

## Tech Stack

- **Authoring format:** PreTeXt XML (`.ptx` files)
- **Build tool:** PreTeXt CLI (`pretext`) -- Python-based, installed via pip
- **Python dependency:** `pretext == 2.11.3` (pinned in `requirements.txt`)
- **CI/CD:** GitHub Actions (`.github/workflows/pretext-cli.yml`) -- builds on push/PR, deploys to Cloudflare Pages or GitHub Pages
- **Dev environment:** GitHub Codespaces via `.devcontainer.json` (Docker image: `oscarlevin/pretext:full`)
- **LaTeX packages:** TikZ, PGFPlots (declared in `docinfo.ptx` for latex-image generation)
- **License:** MIT

## Project Structure

```
PhiTextText/
  project.ptx                    # Project manifest -- build targets and config
  requirements.txt               # Python dependency (pretext CLI version)
  publication/
    publication.ptx              # Publication settings (output styling, numbering, etc.)
  source/
    main.ptx                     # Root document -- includes all other source files
    docinfo.ptx                  # Preamble: macros, LaTeX packages, document metadata
    frontmatter.ptx              # Title page, author info, copyright, colophon
    ch-chapter-title.ptx         # Chapter definition (includes sections)
    sec-section-name.ptx         # Section content
    backmatter.ptx               # Back matter: solutions, index, colophon
  .github/workflows/
    pretext-cli.yml              # CI pipeline: build + deploy
  .devcontainer.json             # Codespaces/dev container configuration
  GenerateAssetsHelp.md          # Instructions for switching Docker images
```

## Build / Run Instructions

### Prerequisites
- Python 3 with pip
- Install dependencies: `pip install -r requirements.txt`

### Common Commands
| Command | Description |
|---|---|
| `pretext build web` | Build HTML output |
| `pretext build print` | Build PDF output (requires LaTeX) |
| `pretext view web` | Build and serve HTML locally for preview |
| `pretext deploy --stage-only` | Stage deployment artifacts to `output/stage/` |
| `pretext --version` | Check installed PreTeXt CLI version |

### Build Targets (defined in `project.ptx`)
- **web** -- HTML format
- **print** -- PDF format

### CI/CD
Pushes to `main` and pull requests trigger the GitHub Actions workflow which:
1. Builds deploy targets inside `oscarlevin/pretext:full` Docker container
2. Stages output to `output/stage/`
3. Optionally deploys to Cloudflare Pages (if `CLOUDFLARE_PROJECT_NAME` is set) or GitHub Pages (if `PTX_ENABLE_DEPLOY_GHPAGES` is `yes`)

## Key Files

- **`source/main.ptx`** -- The root document. All content is pulled in via `xi:include`. Start here to understand the book structure.
- **`source/docinfo.ptx`** -- Math macros (`\N`, `\Z`, `\Q`, `\R`), LaTeX image preamble (TikZ/PGFPlots), document ID, and blurb.
- **`publication/publication.ptx`** -- Controls output appearance: chunking, TOC depth, exercise visibility, HTML style, LaTeX options, numbering.
- **`project.ptx`** -- The project manifest. Defines build targets (`web`, `print`) and directory structure.
- **`requirements.txt`** -- Pins `pretext == 2.11.3`.

## Conventions

- Source files follow PreTeXt naming: chapters as `ch-*.ptx`, sections as `sec-*.ptx`.
- All source files live under `source/` and are included into `main.ptx` via `xi:include`.
- Generated output goes to `output/` (git-ignored).
- Generated assets go to `generated-assets/` (git-ignored).
- The `publication/publication.ptx` file controls all formatting and rendering decisions -- do not hardcode style in source files.

## Memory System

This project uses an ongoing memory consolidation system. Follow these rules on every task:

1. **Before starting any task:** Read `.memory/state.md` and all `.memory/state-t*.md` snapshot files.
2. **During every task:** Spawn a parallel subagent to handle memory consolidation. The subagent should read and follow the instructions in `.memory/instructions.md`. This runs alongside the main task -- do not wait for it to complete.
3. **The memory agent updates:** `.memory/state.md` every cycle, and `.memory/project-map.md` and `.memory/knowledge-base.md` when the current task produces relevant changes.
4. **Never skip the memory cycle.** Even for small tasks, the parallel agent should run.
