# Repository Engineering & AI Agent Contract

## 1. Decision Hierarchy
1. Verified repository code, static artifact integrity checks (`.github/workflows/ci.yml`), and live configuration
2. Upstream source and ADRs in `creova-studios/seen` (`site/` and `docs/adr/`)
3. Repository-specific constraints in this file
4. Shared Engineering Governance Standard (`v1.0`)

## 2. Hard Invariants for All Agents (Antigravity, Devin, Claude, Codex, GStack)
- **Artifact Provenance:** This repository (`creova-studios/seen-site`) is the GitHub Pages deployment target for `https://seen.creova.one`. Content and template edits belong upstream in `creova-studios/seen/site/` (`SITE_URL=https://seen.creova.one node build.mjs`).
- **CSP & Zero-Tracker Invariant:** Never weaken `default-src 'none'`, add inline `<script>` / `style=` / `on*=` attributes, introduce cookies/`localStorage`, or reference external CDN fonts/scripts.
- **No Harness or Asset Pollution:** Never commit `.claude/`, `.agents/`, `.cursor/`, `gstack/`, `node_modules/`, `archive/`, or `.env` files.
- **PR & Verification Discipline:** Verify HTML, CSP, `CNAME`, and local asset links before opening an atomic Conventional Commit pull request.
