# Project State — PhiTextText

## Task Counter: 1

## Project Description
PhiTextText is a PreTeXt XML authoring project for writing a mathematical/scientific textbook. It was generated from the official PreTeXt Codespace template (by Oscar Levin). The book is currently titled "My Great Book" with subtitle "An example to get you started" and contains only placeholder/starter content (one chapter with one section). It builds to HTML and PDF via the PreTeXt CLI (v2.11.3).

## Current State
- Source files: `main.ptx` (root), `docinfo.ptx`, `frontmatter.ptx`, `ch-chapter-title.ptx`, `sec-section-name.ptx`, `backmatter.ptx`
- Publication config: `publication/publication.ptx`
- Project manifest: `project.ptx` (defines web + print targets)
- CI/CD: `.github/workflows/pretext-cli.yml` (builds on push/PR, deploys to Cloudflare or GitHub Pages)
- Dev environment: `.devcontainer.json` (oscarlevin/pretext:full Docker image)
- CLAUDE.md deployed; `.memory/` system intact; `.claude/` folder with commands and skills
- `.gitignore` configured for output/, generated-assets/, editor configs, OS files
- All content is still placeholder from the template — no real authoring has occurred

## Active Work
- No active work. Project is awaiting first real authoring tasks.

## Open Threads
- Book content needs to be written (all current content is placeholder).
- `docinfo.ptx` has `document-id` set to "changeme" — needs a real ID.
- `frontmatter.ptx` author info is placeholder ("You", "Your department", "Your institution").
- Deployment targets (Cloudflare / GitHub Pages) are not yet configured (no secrets/variables set).
- `docinfo.ptx` blurb still references academic template content.

## Direction
- Awaiting first real authoring tasks from the user.
- PreTeXt build infrastructure is functional; main work is content creation.

## Last Updated
- 2026-02-15: v3 deployment health check — verified all files, updated memory to reflect current state
