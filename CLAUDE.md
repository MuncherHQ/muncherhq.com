# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

MuncherHQ is a static HTML landing page for an indie software studio. It is a **single-file, zero-dependency site** — no build system, no npm, no framework.

- **Stack:** Vanilla HTML + CSS + JavaScript, deployed on Vercel
- **Entry point:** `index.html` (all CSS and JS are inline)
- **Assets:** `munchy-phone-transparent-small.png` (mascot image)
- **Deployment:** Vercel (project config in `.vercel/project.json`)

## Development

Since there is no build step, development is just editing `index.html` directly. To preview locally, open `index.html` in a browser or use any static file server:

```bash
npx serve .
# or
python -m http.server
```

Deploying to production uses the Vercel skill (`/deploy`).

## Architecture

Everything lives in `index.html`:

- **Styles:** `<style>` block in `<head>` — uses CSS custom properties (dark theme, lime `#b9ff66` accent)
- **Scripts:** `<script>` block before `</body>` — vanilla JS for scroll animations and nav effects
- **Sections:** `<nav>` → `.hero` → `.products` → `.philosophy` → `<footer>`

### Key patterns

- **Scroll animations** use `IntersectionObserver` with stagger delays on `.product-card` and `.philosophy-card`
- **Nav scroll effect** adds a border via `scroll` event listener with passive: true
- **Responsive breakpoints:** 768px (tablet), 480px (mobile) via media queries in the inline `<style>`
- **GTM:** Google Tag Manager `GTM-PJVF5M7M` loaded in `<head>` with a `<noscript>` fallback in `<body>`

### Design tokens (CSS variables)

| Variable | Value | Usage |
|---|---|---|
| `--accent` | `#b9ff66` | Lime green — CTAs, highlights |
| `--bg` | `#0a0a0b` | Page background |
| `--bg-card` | `#18181c` | Card backgrounds |
| `--hot` | `#ff6b6b` | Red accents |
| `--blue` | `#66b8ff` | Blue accents |

### Products referenced on the page

- **BetaMuncher** — Coming soon, links to betamuncher.com
- **FileMuncher** — Live, links to filemuncher.com
