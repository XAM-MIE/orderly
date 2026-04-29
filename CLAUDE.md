@AGENTS.md

# Additional Context

Before writing any UI code, you MUST read these files in order:
1. `DESIGN.md` — Visual specification
2. `design-system/UI.md` — Page & component hierarchy  
3. `design-system/styles/tokens.css` — CSS custom properties (the ONLY allowed values)
4. `design-system/styles/components.css` — Pre-built component classes

Reference pages exist in `design-system/*.html`. Your output must visually match them.

Preview system: `design-system/preview-system/index.html`

**No emojis. No arbitrary Tailwind values. Tokens only. The Next.js app uses Tailwind CSS v4 — map all tokens into the theme config.**
