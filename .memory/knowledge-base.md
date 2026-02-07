# Knowledge Base — PhiTextText

## Project Origin
**Current approach:** Project was created from the official PreTeXt Codespace template by Oscar Levin.
**Previously tried:** N/A (fresh project from template).
**Context:** The template provides a ready-to-go PreTeXt authoring environment with GitHub Codespaces support, CI/CD workflows, and starter content. The book content ("My Great Book") is all placeholder and needs to be replaced with real material.

## Build System
**Current approach:** PreTeXt CLI v2.11.3 installed via pip. Two build targets defined in `project.ptx`: `web` (HTML) and `print` (PDF). Build commands: `pretext build web`, `pretext build print`. Preview with `pretext view web`.
**Previously tried:** N/A.
**Context:** PDF builds require a LaTeX installation (available in the `oscarlevin/pretext:full` Docker image). The CI workflow auto-detects PreTeXt version >= 2.5 and uses `pretext build --deploys` accordingly.

## Deployment
**Current approach:** GitHub Actions workflow builds on every push to main and on PRs. Two optional deploy targets: Cloudflare Pages (requires `CLOUDFLARE_PROJECT_NAME` variable and API secrets) and GitHub Pages (requires `PTX_ENABLE_DEPLOY_GHPAGES=yes`).
**Previously tried:** Deprecated workflows at `.github/workflows/deploy.yml` and `.github/workflows/test-build.yml` (git-ignored).
**Context:** Deploy artifacts are staged to `output/stage/` before publishing.

## Math Macros
**Current approach:** Defined in `source/docinfo.ptx`: `\N` (naturals), `\Z` (integers), `\Q` (rationals), `\R` (reals).
**Previously tried:** N/A.
**Context:** These are standard blackboard-bold shortcuts for mathematical writing.

## LaTeX Image Support
**Current approach:** TikZ and PGFPlots loaded in the latex-image-preamble in `docinfo.ptx`. Multiple TikZ libraries enabled: positioning, matrix, arrows, shapes, decorations, shadows, fadings, patterns, decorations.markings.
**Previously tried:** N/A.
**Context:** These packages allow inline LaTeX-generated diagrams in the PreTeXt source.

## Docker Images
**Current approach:** Using `oscarlevin/pretext:full` for maximum compatibility (LaTeX + asset generation).
**Previously tried:** Template offers three tiers: `lite` (web only, no LaTeX), `small` (basic LaTeX), `full` (complete LaTeX + Sage).
**Context:** See `GenerateAssetsHelp.md` for switching instructions. The choice affects Codespace storage usage.
