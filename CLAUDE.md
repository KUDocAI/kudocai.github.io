# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static GitHub Pages site for **KUDoc** — the Document AI research team at Korea University NLP&AI Lab. Deployed at `kudocai.github.io` from the `master` branch.

Two files do all the work:
- `index.html` — single-page site (nav, hero, research, team, publications, projects, contact)
- `style.css` — all styles (no build step, no framework)
- `images/` — local photos (only `duong-tuan-thanh.png` currently)

## Deployment

Push to `master` → GitHub Pages auto-deploys. No build step required.

**Canonical remote:** `kudocai` → `https://github.com/KUDocAI/kudocai.github.io`

Always push with:
```bash
git push kudocai master
```

The original `origin` remote (`gyuhoshim/kudoc`) still exists but is no longer the primary deployment target.

**Cache busting:** The stylesheet is linked as `style.css?v=N`. Increment `N` on every push that changes `style.css`, otherwise browsers serve the cached version.

```html
<link rel="stylesheet" href="style.css?v=10" />
```

## Design System

**Color palette (CSS variables in `:root`):**
- `--accent: #8c1515` — Stanford Cardinal red (primary brand color)
- `--bg: #eae8de` / `--cream: #eae8de` — warm cream background
- `--bg-card: #f3f1e9` — slightly lighter cream for cards
- `--primary: #141413` — near-black text

**Typography:**
- Body: `Inter` (sans-serif)
- Display/headings: `Source Serif 4` (editorial serif, Google Fonts)
- `font-size: clamp(0.9rem, 1vw + 0.5rem, 1rem)` on body for fluid scaling

**Hero title treatment:**
```html
<h1><span class="hero-ku">KU</span><em>Doc</em></h1>
```
- `.hero-ku` → upright, red (`--accent`)
- `em` → italic, near-black (`--primary`)

## Key Structural Patterns

### Timeline (alternating left/right)
Items use explicit `.tl-left` / `.tl-right` classes (not `nth-child`) because `.tl-track` is a sibling that throws off nth-child counts.

```html
<div class="tl-item tl-left" tabindex="0">
  <div class="tl-body">
    <div class="tl-date"><span class="tl-icon">⚙️</span> 2024.03 – Present</div>
    ...
  </div>
  <div class="tl-dot"></div>
</div>
```
- Projects (ongoing) go **left** with `⚙️` icon
- Papers (published) go **right** with `📄` icon
- Grid layout: `tl-left` body in column 1, dot in column 2; `tl-right` dot in column 2, body in column 3

### Team section
- PI: single wide card (`.team-pi-card`)
- Professors: 2-column grid (`.team-grid--wide { grid-template-columns: repeat(2, 1fr); }`) — keeps "Assistant Professor" on one line
- Researchers: standard grid
- Role badges: `white-space: nowrap` to prevent wrapping

### Profile photos
| Person | Source |
|--------|--------|
| Heuiseok Lim | `nlp.korea.ac.kr` lab website |
| Jaehyung Seo | `nlp.korea.ac.kr` lab website |
| Chanjun Park | `nlp.korea.ac.kr` lab website |
| Joongmin Shin | `shinjm-maker.github.io` |
| Gyuho Shim | GitHub avatar (`avatars.githubusercontent.com`) |
| Duong Tuan Thanh | `images/duong-tuan-thanh.png` (local) |

## Team Members
- **PI:** Prof. Heuiseok Lim
- **Professors:** Jaehyung Seo (Assistant), Chanjun Park (Assistant)
- **Team Lead:** Joongmin Shin
- **Co-Lead:** Gyuho Shim
- **Member:** Duong Tuan Thanh

## Publications on Site
- REVISE — ACL 2025 Oral
- M3DocDep — CVPR 2026
- MultiDocFusion — EMNLP 2025
- StyleDFS — EMNLP 2024 Industry

## JavaScript (inline in index.html)
- Navbar: adds `.scrolled` class on scroll for border/shadow
- Timeline: click/keyboard to activate items; `IntersectionObserver` for staggered entrance animation; animated fill line on scroll
