# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project overview

A static, no-build self-introduction web page (Korean, `lang="ko"`) built as a learning exercise. Pure HTML5 + CSS3 — **no JavaScript, no framework, no build tooling, no backend**. There is no package.json, no dependency manager, and nothing to compile.

## Running / previewing

There is no dev server or build step. Open `index.html` directly in a browser (or use a simple static file server / editor live-preview extension) to view changes.

There is no linter or test suite configured in this repo.

## Architecture

- `index.html` — single page, semantic HTML (`header`/`nav`/`main`/`section`/`footer`), sections keyed by id (`#intro`, `#about`, `#interests`, `#goals`, `#learning`) that the nav links to via anchors.
- `css/main.css` — style entry point that only does `@import` of the other four files, in load order: `tokens.css` → `base.css` → `layout.css` → `components.css`. When adding styles, put them in the matching layer rather than appending to `main.css` directly:
  - `tokens.css` — design tokens as CSS custom properties on `:root` (KRDS Primary/Grayscale colors, typography, spacing, layout, focus ring). Change visual values here, not by hardcoding in other files.
  - `base.css` — reset and bare element defaults (`*`, `html`, `body`, `a`), plus the skip-link.
  - `layout.css` — page-level structure: container, sticky header, hero section, footer, responsive breakpoints.
  - `components.css` — reusable UI pieces: GNB nav list, card, hobby list, tag list.
- Font is loaded via CDN `<link>` in `index.html` (Pretendard GOV), not bundled locally.
- Base font size uses `html { font-size: 62.5% }` so all `rem` values in tokens/components are effectively in `px/10` units (e.g. `1.6rem` = 16px).

## Content/privacy constraint

This is intended as a publicly-committed repo for a middle-school-level learning exercise. The README (Korean) specifies that no personally identifying information may be added: no real names, school names, contact info, addresses, or identifiable photos. Self-introduction copy should stay generic/role-based (e.g. "중학생", "학습자"). Keep this in mind when editing page content — don't introduce real personal data into `index.html`, CSS, or commit messages.
