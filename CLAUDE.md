# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this repo is

A personal website (`charon.cx`) with a Charon/River Styx mythological theme, plus a Logseq knowledge base in the same repo. No build pipeline — pure static HTML/CSS, open files directly in a browser to preview.

## Running locally

Open HTML files directly in a browser — no server or build step needed:
- `index.html` — main site entry point (currently empty placeholder)
- `michael_bday_card.html` — standalone birthday card

## Architecture

**Main site (`index.html` + `style.css`):** Dark cyberpunk/mythological aesthetic. Core visual elements are a multi-layer animated fog effect (River Styx), a circular HUD-style profile container with a hover overlay, and a contact button named "Obol" (the Charon coin metaphor). Fonts loaded via `assets/fonts.css` (Playfair Display, DM Sans, JetBrains Mono).

**Birthday card (`michael_bday_card.html`):** Fully self-contained single-file HTML with all styles inline. Warm color palette (cream/green/gold), vacation option picker (A/B/C). `michael-bday/index.html` is a mirror of the same file.

**Logseq (`logseq/`):** Local-first note-taking config. `logseq/config.edn` is the main config — Markdown format, NOW/LATER workflow, date format `YYYY_MM_DD`. Journals live in `journals/`, pages in `pages/`. These files are managed by Logseq itself; edits outside Logseq may conflict with its cache.

## Conventions

- Design language: mythological metaphors (Charon, Styx, Obol) — keep naming consistent with this theme when adding elements.
- CSS variables defined at `:root` in `style.css` hold the color palette and spacing; use them rather than hardcoded values.
- Logseq bak/recycle dirs are gitignored — don't commit them.
