<!-- BEGIN:nextjs-agent-rules -->
# This is NOT the Next.js you know

This version has breaking changes — APIs, conventions, and file structure may all differ from your training data. Read the relevant guide in `node_modules/next/dist/docs/` before writing any code. Heed deprecation notices.
<!-- END:nextjs-agent-rules -->

---

# MANDATORY: Design System Compliance

> **This section is non-negotiable. Every instruction below MUST be followed without exception.**

## Before You Write ANY UI Code

You MUST read and internalize the following files IN THIS ORDER before generating any front-end code:

1. **`DESIGN.md`** — The visual specification. Contains the exact color palette, typography rules, spacing system, border-radii, shadow definitions, and motion curves. EVERY visual value in your code must come from this spec.
2. **`design-system/UI.md`** — The page map and component hierarchy. Shows every page, its sections, and the components used in each section.
3. **`design-system/styles/tokens.css`** — CSS custom properties. These are the ONLY values you may use for colors, spacing, radii, shadows, and easing.
4. **`design-system/styles/components.css`** — Pre-built component classes. Check if a component already exists before creating anything new.
5. **`design-system/index.html`** — The component library reference page. Open it in a browser to see every token and component rendered.

## Reference Pages

The `design-system/` directory contains fully built reference pages that represent the canonical UI for each screen:

| File | Page |
|---|---|
| `homepage.html` | Hero, categories, deals, popular vendors, trending items |
| `explore.html` | Search, filter sidebar, vendor grid |
| `vendor.html` | Storefront, menu, item modal, cart sidebar |
| `checkout.html` | Cart review, delivery address, payment, order summary |
| `tracking.html` | Order tracking with stepper, map, contact |
| `auth.html` | Login/signup with tab toggle |
| `account.html` | Profile, addresses, order history |
| `index.html` | Component library (all tokens + components) |

**When implementing any page in the Next.js app, your output MUST match the corresponding reference page visually.** Open `design-system/preview-system/index.html` to preview all pages with viewport switching.

## Hard Rules — DO NOT VIOLATE

### Colors
- Use ONLY CSS custom properties from `tokens.css` (e.g., `var(--color-blue-450)`).
- NEVER hardcode hex values like `#5b76fe` directly in component styles. Always use the token.
- NEVER invent new colors. If a color doesn't exist in `tokens.css`, it does not belong in this project.

### Typography
- Use ONLY the predefined type classes: `.display-hero`, `.display-section`, `.heading-card`, `.text-feature`, `.text-body`, `.text-body-standard`, `.text-caption`, `.text-eyebrow`, `.text-small`, `.text-micro`.
- The display font is `var(--font-display)` (DM Sans / Roobert PRO). The body font is `var(--font-body)` (Noto Sans).
- NEVER use browser-default fonts, Geist, Inter, or any other font family.
- NEVER create ad-hoc font sizes. Use the scale defined in `base.css`.

### Spacing
- Use ONLY the spacing tokens: `var(--space-1)` through `var(--space-12)`.
- These follow an 8px base grid. NEVER use arbitrary pixel values for margins, padding, or gaps.

### Border Radius
- Use ONLY: `var(--radius-sm)` (8px), `var(--radius-md)` (12px), `var(--radius-lg)` (20px), `var(--radius-xl)` (24px), `var(--radius-pill)` (50px), `var(--radius-circle)` (50%).
- NEVER use `rounded-lg`, `rounded-xl`, or any Tailwind-style radius class. This is vanilla CSS.

### Shadows
- Use ONLY: `var(--shadow-ring)`, `var(--shadow-card)`, `var(--shadow-elevated)`, `var(--shadow-float)`.
- NEVER use `box-shadow` with raw values unless extending the system intentionally.

### Icons
- **NO EMOJIS. EVER.** Not in buttons, not in chips, not in nav, not in cards, not anywhere.
- All icons are inline `<svg>` elements with `stroke="currentColor"`, `fill="none"`, `stroke-width="2"`.
- Use the `.icon`, `.icon--sm`, `.icon--md`, `.icon--lg` utility classes for sizing.

### Motion
- Use `var(--ease-smooth)` for standard transitions.
- Use `var(--ease-bounce)` for playful interactions.
- Animate ONLY `transform` and `opacity` (hardware-accelerated). Never animate `width`, `height`, `top`, `left`, `margin`, or `padding`.

### Components
- Check `components.css` FIRST. Classes exist for: buttons, cards, inputs, chips, badges, ratings, toggles, quantity controls, tabs, steppers, and filter controls.
- If a component class exists, USE IT. Do not rebuild it.
- If you need a new component, it must follow the same token system and naming convention.

### Responsive
- The layout system has breakpoints at: 1024px, 768px, 480px, 425px.
- Grids collapse: 4→2→2→1 and 3→2→2→1 across these breakpoints.
- Test at all breakpoints. The preview system has viewport toggles.

### CSS Architecture
- The **design system reference pages** (`design-system/*.html`) use vanilla CSS with custom properties via `design-system/styles.css`.
- The **Next.js app** uses **Tailwind CSS v4**. All design tokens from `tokens.css` must be mapped into Tailwind's theme configuration so that utility classes reference the same values.
- When using Tailwind in the Next.js app, use token-backed utilities (e.g., `text-near-black`, `bg-blue-450`, `rounded-md`) — NEVER use arbitrary values like `text-[#5b76fe]` or `p-[17px]`. If a value isn't in the theme, it doesn't belong.
- The design system reference pages are the visual source of truth. The Next.js implementation must match them pixel-for-pixel regardless of which CSS approach is used.

## Preview System

The preview hub at `design-system/preview-system/index.html` provides:
- Sidebar navigation to every page
- Iframe viewer with Desktop/Tablet/Mobile viewport toggles
- Visual comparison tool for verifying your work

**Use it. If your implementation doesn't match the reference page in the preview system, it is wrong.**
