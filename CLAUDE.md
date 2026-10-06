# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Single-page personal/company website for BalLieGus (Maarten Balliere, freelance Cloud Solution Architect), served at www.balliegus.be. The `CNAME` file indicates it is hosted on GitHub Pages straight from the repository root — there is no build step, package manager, linter, or test suite.

## Development

Open `index.html` directly in a browser, or serve the folder locally so relative paths behave as in production:

```
python -m http.server 8000
```

Deployment happens by merging to `main` (GitHub Pages). Don't remove or rename `CNAME`, or the custom domain breaks.

## Structure

- `index.html` — the entire site. Sections (`#home`, `#about`, `#services`, `#contact`) are anchored from the navbar; nav links must have the `nav-link` class so the mobile menu closes on click.
- `assets/css/style.css` — all styling. Design tokens (colors, spacing, font sizes, shadows) are CSS custom properties on `:root`; reuse them rather than hard-coding values. Responsive breakpoints are at 768px (hamburger menu) and 480px, at the end of the file.
- `assets/js/main.js` — vanilla JS, no dependencies: footer year, `.scrolled` class on the navbar after 50px scroll, and the mobile menu toggle (`.active` on `#nav-menu` / `#nav-toggle`). It relies on the element IDs `year`, `navbar`, `nav-toggle`, `nav-menu`.
- `assets/imgs/` — logo (also the favicon) and service icons; `assets/docs/` — the downloadable CV linked from the About section.

## Conventions

- Keep it dependency-free: no frameworks, CDNs, or web fonts (the font stack is system fonts).
- Icons in the contact section and footer are inline SVGs using `stroke="currentColor"`/`fill="currentColor"` so they pick up CSS colors.
- Contact tiles are `<a class="contact-card">` elements so the whole tile is clickable; keep them as anchors.
- Contact details (email, phone, VAT number, address) appear in several places in `index.html` (CTA, contact cards, company info) — update all occurrences together.
