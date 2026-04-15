# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static website for Safe Somatics, a somatic therapy practice. Pure HTML/CSS/JS with no build tools or frameworks. Hosted on Firebase Hosting with automated deployment via GitHub Actions.

## Deployment

- **Hosting**: Firebase Hosting (project: `safe-somatics`)
- **Deploy trigger**: Push to `master` branch auto-deploys via `.github/workflows/firebase-deploy.yml`
- **Manual deploy**: `firebase deploy` (requires Firebase CLI and authentication)
- **Preview locally**: Open `public/index.html` directly in a browser, or use `firebase serve` for Firebase-accurate routing
- `cleanUrls` is enabled in `firebase.json`, so `/about-me` serves `about-me.html` without the extension

## Architecture

All served content lives under `public/`. Config files (`firebase.json`, `.firebaserc`, `.github/`) live at the repo root.

```
public/
├── index.html          # Home page
├── about-me.html       # About Valentina
├── offerings.html      # Services: therapy sessions, webinars, course
├── testimonials.html   # Client testimonials
├── css/style.css       # Single stylesheet for all pages
├── js/main.js          # Nav toggle, scroll shadow, fade-in animations
└── images/             # All site imagery (JPG, SVG, OG image)
```

Each HTML page includes the same nav, footer, and disclaimer. Changes to shared elements (nav links, footer text, disclaimer) must be updated in all four HTML files.

## Color Palette (strict)

Only these five colors may be used:

| Name        | Hex       | RGB              |
|-------------|-----------|------------------|
| Olive       | `#737855` | `rgb(115,120,85)`  |
| Cream       | `#fffbf5` | `rgb(255,251,245)` |
| Plum        | `#5d4954` | `rgb(93,73,84)`    |
| Light Green | `#f3f9d2` | `rgb(243,249,210)` |
| Light Pink  | `#ffd2fc` | `rgb(255,210,252)` |

Transparent variants via `rgba()` of these same colors are acceptable for borders, shadows, and overlays. Do not use `white`, `black`, or any color outside this palette.

## CSS Conventions

- **Fonts**: Playfair Display (weights 400 and 700) for all text (headings and body), loaded from Google Fonts
- **Section backgrounds** alternate using utility classes: `.section-cream`, `.section-olive`, `.section-plum`, `.section-light-green`
- **Scroll animations**: Add class `fade-in` to any element to get a fade-up-on-scroll effect (handled by IntersectionObserver in `main.js`)
- **Responsive breakpoints**: 1024px (tablet), 768px (mobile), 480px (small mobile)
