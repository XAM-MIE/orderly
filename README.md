# Orderly

> Campus food delivery platform — order from nearby vendors, pay online, track in real time.

Built with [Next.js](https://nextjs.org) and **Tailwind CSS v4**. Design system authored in vanilla HTML/CSS for maximum portability; the Next.js app mirrors it using Tailwind utilities mapped to the same tokens.

---

## ⚠️ CRITICAL: Design System Compliance

**This project has a fully authored design system. All UI work MUST comply with it.**

Before writing ANY front-end code — whether you are a human developer or an AI coding agent — you MUST:

1. **Read [`DESIGN.md`](./DESIGN.md)** — the visual spec (colors, typography, spacing, radii, shadows, motion)
2. **Read [`design-system/UI.md`](./design-system/UI.md)** — the page & component hierarchy
3. **Preview the reference pages** at `design-system/preview-system/index.html`
4. **Use the existing design tokens** — mapped into the Tailwind v4 theme config from `design-system/styles/tokens.css`. In the Next.js app, use token-backed Tailwind utilities. In the reference pages, use the vanilla CSS custom properties directly.

**Deviation from the design system is not acceptable.** Do not invent new colors, font stacks, spacing values, border-radii, or shadow styles. Every visual property must use the CSS custom properties defined in `design-system/styles/tokens.css`.

---

## Project Structure

```
orderly/
├── DESIGN.md                          # Visual spec — colors, type, spacing, motion
├── AGENTS.md                          # AI agent rules (read before any code)
├── CLAUDE.md                          # Claude-specific rules (inherits AGENTS.md)
├── design-system/                     # THE SOURCE OF TRUTH for all UI
│   ├── styles.css                     # Barrel @import — use this in every page
│   ├── styles/
│   │   ├── tokens.css                 # CSS custom properties (colors, spacing, radii, shadows, motion)
│   │   ├── base.css                   # Reset, HTML defaults, typography scale
│   │   ├── components.css             # Buttons, cards, inputs, chips, badges, toggles, etc.
│   │   ├── navigation.css             # Topnav, bottom nav, avatar, location pill, footer
│   │   └── layout.css                 # Grid, flex, spacing utils, animations, responsive
│   ├── UI.md                          # Page map & component hierarchy spec
│   ├── homepage.html                  # Reference: hero, categories, deals, vendors, trending
│   ├── explore.html                   # Reference: search, filters, vendor grid
│   ├── vendor.html                    # Reference: storefront, menu, cart sidebar, item modal
│   ├── checkout.html                  # Reference: cart review, delivery, payment, order summary
│   ├── tracking.html                  # Reference: order tracking with stepper, map, contact
│   ├── auth.html                      # Reference: login/signup with tab toggle
│   ├── account.html                   # Reference: profile, addresses, order history
│   ├── index.html                     # Component library (all tokens + components rendered)
│   └── preview-system/
│       ├── index.html                 # Preview hub — sidebar + iframe viewer + viewport toggle
│       └── preview.css                # Preview hub styles (isolated)
├── src/                               # Next.js application source
├── public/                            # Static assets
├── package.json
└── next.config.ts
```

---

## Design System Overview

### Visual Language

Miro-inspired: white canvas, near-black text, pastel accent palette, generous radius, ring shadows.

### Tokens (must use these, not raw values)

| Token | Value | Usage |
|---|---|---|
| `--color-near-black` | `#1c1c1e` | Primary text |
| `--color-white` | `#ffffff` | Surfaces |
| `--color-blue-450` | `#5b76fe` | Primary interactive / accent |
| `--color-blue-pressed` | `#2a41b6` | Pressed state |
| `--color-success` | `#00b473` | Positive states |
| `--color-error` | `#e74c3c` | Error states |
| `--color-slate` | `#555a6a` | Secondary text |
| `--color-placeholder` | `#a5a8b5` | Placeholder text |
| `--color-border` | `#c7cad5` | Borders |
| `--color-surface-soft` | `#f7f8fa` | Soft backgrounds |
| `--font-display` | DM Sans / Roobert PRO | Headings, labels, UI text |
| `--font-body` | Noto Sans | Paragraphs, descriptions |
| `--radius-sm` | `8px` | Inputs, chips, small cards |
| `--radius-md` | `12px` | Cards |
| `--radius-lg` | `20px` | Large cards, hero images |
| `--radius-xl` | `24px` | Banners |
| `--radius-pill` | `50px` | Pills, location tags |
| `--shadow-ring` | `0 0 0 1px rgb(224,226,232)` | Card borders |
| `--shadow-card` | Subtle | Resting cards |
| `--shadow-elevated` | Medium | Hover state |
| `--shadow-float` | Deep | Floating elements |
| `--ease-smooth` | `cubic-bezier(0.32, 0.72, 0, 1)` | All transitions |
| `--ease-bounce` | `cubic-bezier(0.34, 1.56, 0.64, 1)` | Playful interactions |

### Pastel Accent Pairs

Each has a light (background) and dark (text) variant:

- **Coral**: `--color-coral-light` / `--color-coral-dark`
- **Rose**: `--color-rose-light`
- **Teal**: `--color-teal-light` / `--color-teal-dark`
- **Orange**: `--color-orange-light` / `--color-yellow-dark`
- **Pink**: `--color-pink`

### Typography Scale

| Class | Size | Font | Weight | Use |
|---|---|---|---|---|
| `.display-hero` | 56px | Display | 500 | Page heroes |
| `.display-section` | 48px | Display | 500 | Section headings |
| `.heading-card` | 24px | Display | 500 | Card titles |
| `.text-feature` | 18px | Display | 600 | Feature labels |
| `.text-body` | 18px | Body | 400 | Paragraphs |
| `.text-body-standard` | 16px | Body | 400 | UI body text |
| `.text-caption` | 14px | Display | 400 | Metadata |
| `.text-eyebrow` | 12px | Display | 600 | Section labels (uppercase) |
| `.text-small` | 12px | Display | 400 | Fine print |

### Component Classes

All pre-built in `components.css`:

- **Buttons**: `.btn .btn-primary .btn-outlined .btn-ghost .btn-success .btn-sm .btn-lg .btn-full .btn-icon`
- **Cards**: `.card .card-body .card-title .card-text .card-pastel`
- **Inputs**: `.input .input-group .input-label .input-error .input-search`
- **Chips**: `.chip .chip.active`
- **Badges**: `.badge .badge-success .badge-error .badge-warning .badge-info .badge-new .badge-promo`
- **Rating**: `.stars .rating-row .rating-value .rating-count`
- **Toggle**: `.toggle .toggle.active`
- **Quantity**: `.qty .qty-btn .qty-value`
- **Tabs**: `.tabs .tab .tab.active`
- **Stepper**: `.stepper .stepper-step .stepper-dot .stepper-line`
- **Filters**: `.filter-checkbox .filter-option`

### Icons

**No emojis.** All icons are inline SVGs using `stroke="currentColor"`. Use the `.icon` / `.icon--sm` / `.icon--md` / `.icon--lg` utility classes for sizing.

---

## Preview System

Open `design-system/preview-system/index.html` in a browser to access the preview hub.

Features:
- **Sidebar navigation** with links to every page
- **Iframe viewer** with viewport toggles (Desktop / Tablet / Mobile)
- **Dashboard** with system statistics
- **Grid view** of all pages as live thumbnails

Use this to verify that any new UI work matches the existing design language before merging.

---

## Getting Started (Next.js App)

```bash
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

---

## Rules for Contributors

1. **Use tokens.** Every color, spacing, radius, and shadow must reference a design token. In the Next.js app, use Tailwind utilities mapped to the theme (e.g., `bg-blue-450`, `rounded-md`, `shadow-card`). NEVER use arbitrary values like `text-[#5b76fe]` or `p-[17px]`.
2. **Use existing components.** Check the reference pages and `components.css` before building anything new. Replicate the same structure in React/Tailwind.
3. **No emojis in UI.** Use inline SVGs with `stroke="currentColor"`.
4. **Preview before merge.** Open the preview system and compare your work against the reference pages. If it doesn't match, it's wrong.
5. **Responsive first.** Test at 1440px, 1024px, 768px, 480px, and 425px.
6. **Motion.** Use `--ease-smooth` for transitions, `--ease-bounce` for playful interactions. Hardware-accelerated properties only (`transform`, `opacity`).
7. **Typography.** Use the predefined type classes / Tailwind equivalents. Do not create ad-hoc font sizes.
8. **Tailwind v4.** This project uses Tailwind CSS v4. Do not downgrade or use v3 syntax. Map all tokens from `tokens.css` into the Tailwind theme.
