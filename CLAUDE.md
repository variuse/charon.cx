# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A personal website (`charon.cx`) with a Charon/River Styx mythological theme, plus a Logseq knowledge base in the same repo. No build pipeline — pure static HTML/CSS, open files directly in a browser to preview.

## Hosting & Deployment

**GitHub Pages** — deployed via `.github/workflows/deploy.yml` on every push to `main`.
- Source branch: `gh-pages` (written by the workflow, don't edit directly)
- Custom domain: `charon.cx` (CNAME file managed by the workflow)
- HTTPS enforced
- The workflow copies `index.html`, `assets/`, `insta.png`, `result_146456.jpeg` to an output folder and deploys that — add any new web assets here.
- When migrating to React/Vite: uncomment the build steps in the workflow and change `publish_dir` to `./dist`.

**DNS** — managed on Porkbun. Apex A records point to GitHub Pages IPs (185.199.108–111.153). `www` CNAME → `variuse.github.io`. MX/SPF/DKIM/DMARC records intact for email forwarding.

**FTP credentials** (legacy Porkbun static hosting — can be cancelled): see `.vscode/sftp.json` for host/user. Password in Porkbun dashboard under Hosting → Manage.

## Running locally

Open HTML files directly in a browser — no server or build step needed:
- `index.html` — main site (fog animation, HUD profile, Obol contact button)

## Architecture

**Main site (`index.html`):** Dark cyberpunk/mythological aesthetic. Core visual elements are a multi-layer animated fog effect (River Styx), a circular HUD-style profile container with a hover overlay, and a contact button named "Obol" (the Charon coin metaphor). Fonts loaded from Google Fonts (Inter, JetBrains Mono).

Note: `index.html` contains its own inline `<style>` block — this is the single source of truth for styles. (A previously divergent `style.css` was removed.)

**Assets at repo root:** `insta.png`, `result_146456.jpeg` (profile photo) — these are web assets, not source files, kept at root to match the HTML's relative paths.

**Logseq (`logseq/`):** Local-first note-taking config. `logseq/config.edn` is the main config — Markdown format, NOW/LATER workflow, date format `YYYY_MM_DD`. Journals live in `journals/`, pages in `pages/`. These files are managed by Logseq itself; edits outside Logseq may conflict with its cache.

## Conventions

- Design language: mythological metaphors (Charon, Styx, Obol) — keep naming consistent with this theme when adding elements.
- CSS variables defined at `:root` in the inline `<style>` hold the color palette; use them rather than hardcoded values.
- Logseq bak/recycle dirs are gitignored — don't commit them.
- Repo is public (required for GitHub Pages on free plan).
