# Loggerhead Fitness — Project Guide for Claude

## Project location
`/Users/kristiandermody/Development/loggerhead/loggerhead-summer-8wk-118-2026`

Parent project root: `/Users/kristiandermody/Development/loggerhead`
GitHub: https://github.com/kristiandermody/loggerhead-summer-8wk-118-2026

---

## Client
**Loggerhead Fitness**
Boutique gym — Juno Beach, FL
Website: https://loggerheadfitness.com
Booking / scheduling: WellnessLiving

---

## Brand

### Colors
| Role | Value |
|---|---|
| Primary (indigo) | `rgb(42, 49, 146)` |
| Accent (lime) | `rgb(165, 245, 35)` |
| Deep navy | `#1D2370` |
| Charcoal | `#1A1A35` |
| Cream bg | `#F7F8FF` |
| Sand bg | `#ECEFFE` |

### Typography
| Role | Font |
|---|---|
| Headlines | Fraunces (Google Fonts, serif) |
| Handwritten accents | Caveat (Google Fonts) |
| Body / UI | Plus Jakarta Sans (Google Fonts) |

### Logos
All logo assets live in `/logos/`:
- `logo_New_roundLHF.jpg` — round badge (current)
- `logo_lhf_round.jpg` — round badge (alt)
- `loggerheadfitnesshirez.ai` / `.eps` — vector originals
- Web-hosted fallback: `https://loggerheadfitness.com/wp-content/uploads/2021/07/LHF-logo-167.png`

---

## Tech constraints
- **Deliverable format:** Single-file HTML/CSS/JS — no build tools, no npm, no frameworks
- **Host environment:** WordPress — drop-in HTML page, no server-side code
- **Mobile-first:** Always design 360px → 600px → desktop
- **WellnessLiving widget** (required in any signup/join section):
  ```html
  <script type="module" src=https://widgets.wellnessliving.com/store/widget.js></script>
  <wl-store-widget k_business="95010" k_skin="330277" k_location=""></wl-store-widget>
  ```

---

## Verified pricing (rate card — May 2026)
| Item | Price |
|---|---|
| Summer Special — 8 weeks | **$118** |
| Full Package — 8 weeks | **$166** |
| Day pass | **$6 / week** |
| Drop-in | **$48** |
| Base total | $138 |
| Full total | $186 |
| Retail value callout | $375 |

**Includes:** 2 × 30-min PT sessions · SGT Level 1, 2 or 3 · 38 GX classes to choose from

---

## Hero photo (Unsplash, free license)
Boutique gym — dumbbell rack, bright windows
`https://images.unsplash.com/photo-1534438327276-14e5300c3a48?auto=format&fit=crop&w=1400&q=80`
**Rejected option:** beach runner on rock steps — "doesn't work for this project"

---

## Folder structure
```
loggerhead/                                    ← parent (DO NOT git init here)
  loggerhead-summer-8wk-118-2026/             ← THIS PROJECT (git lives here only)
    CLAUDE.md                                 ← you are here
    CHANGELOG.md                              ← version history
    summer-2026-v1-dark-original.html
    summer-2026-v2-pastel-recolor.html
    summer-2026-v3-dark-hero.html             ← reference (pre-client-tweaks)
    summer-2026-v3b-dark-hero.html           ← LIVE — uploaded to WordPress (May 19)
    summer-2026-v4-light-hero.html            ← A/B option — presented to client

    student-promo/                           ← student campaign (same theme as v3b)
      student-summer-special-2026-v1.html   ← v1 built May 19 — WL checkout URLs pending
```

---

## Key CSS/design patterns established

### Seamless hero → stats transition (v3 dark)
Overlay goes fully opaque at 76% height. Hero has `padding-bottom: 80px`. Stats uses `margin-top: -80px` + `z-index: 10` to float over the solid-color runway. Zero seam.

### Light-mode hero split (v4)
Dual gradient overlay: cream strong on the left (text lives here), fades toward transparent on the right (photo shows). `background-position: center right`. Nav switches from dark-glass to cream-frost.

### Rainbow wave SVG
Used between stats bar and urgency banner. SVG `<linearGradient>` stroke: indigo → periwinkle → lime → periwinkle → indigo. Two stroke passes (wide soft + crisp thin) for glow + edge.

### Mobile pricing cards
```css
@media (max-width: 360px)  { grid-template-columns: 1fr; }
@media (min-width: 361px)  { grid-template-columns: 1fr 1fr; }
@media (min-width: 600px)  { grid-template-columns: repeat(3, 1fr); }
```
