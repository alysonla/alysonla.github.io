# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static personal website for Alyson La's personal finance coaching business, deployed via GitHub Pages at `alysonla.com`. There is no build step, no package manager, and no test framework — the entire site is a single `index.html` file with all CSS embedded in a `<style>` block and minimal vanilla JavaScript.

## Deployment

Changes pushed to the default branch are automatically deployed by GitHub Pages. The custom domain is configured via the `CNAME` file (value: `alysonla.com`). No build step is required; the browser receives `index.html` directly.

To preview locally, open the file in a browser or use any static file server:
```
python3 -m http.server 8000
```

## Architecture

Everything lives in `index.html`:

- **CSS custom properties** defined in `:root` establish the color palette: `--cream`, `--ink`, `--rust`, `--gold`, `--sage`, `--wine`, `--blush`. Use these variables for any new colors rather than hardcoding hex values.
- **Fonts** are loaded from Google Fonts: `Playfair Display` (headings/display), `DM Sans` (body), `Caveat` (handwritten accents).
- **Sections** flow top-to-bottom: nav → hero → marquee strip → `#teach` → `#format` → `#barter` → `#who` → `footer#connect`.
- **Scroll animations** use `IntersectionObserver` at the bottom of the file. Elements get the class `fade-up` in HTML; the observer adds `visible` when they enter the viewport. The current CSS sets `fade-up` to `opacity: 1; transform: none` (animations are effectively no-ops as written).
- **Responsive breakpoint** is at `max-width: 768px`. The nav links hide, the hero and layout grids collapse to single columns.
- The hero photo is `headshot.png` in the root directory, referenced as `src="headshot.png"`.
- Contact email is `alyson@alysonla.com`, used in two `<a href="mailto:...">` links in `#barter` and `footer`.
