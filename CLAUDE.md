# Aspen Bikes & Skis — Project Guide

## What we're building
The owners want one web presence for **Aspen Bikes** (aspenbikes.com) and **Aspen Skis** (aspenskis.com).
Approach (agreed 2026-11-14):

1. **`landing/`** — a new React + TypeScript landing site hosted on Netlify. It is a *product-led storefront*,
   not a splash page: it leads with the in-season shop (skis roughly Nov–Apr, bikes the rest of the year),
   shows best sellers from both shops, and every product card links straight to that product on the right site.
2. **aspenbikes.com (COPY)** — Squarespace. Rework the homepage from a hero layout into a product-first page
   (best-seller product cards: image, name, price, CTA) and restyle to match the shared design system.
3. **aspenskis.com (COPY)** — Squarespace. Same treatment as the bikes site.

All three must look like **one site**: same fonts, colours, logo, nav and components, with links back to the landing page.

**Hard rule:** never change the ordering, booking or checkout systems on the Squarespace sites. Styling and layout only.
Work happens on the **COPY** sites only, never on the live sites.

## Agent team (`.claude/agents/`)
| Agent | Owns |
|---|---|
| `lead-ui-developer` | The shared design system in `design-system/`. Reviews every visual change on all three sites. |
| `react-frontend-dev` | `landing/` (React + TypeScript + Vite, Netlify). |
| `bikes-squarespace-dev` | `squarespace/bikes/` → aspenbikes.com (COPY). |
| `skis-squarespace-dev` | `squarespace/skis/` → aspenskis.com (COPY). |
| `project-manager` | `docs/` — work log, component register, decisions. The client's proof of work. |

### Workflow
1. Any change to fonts, colours, spacing, radii, motion or a shared component starts with `lead-ui-developer`.
   The other developers consume `design-system/tokens.css`. They never hard-code their own values.
2. A developer finishes a task, then `lead-ui-developer` reviews it for consistency and accessibility.
3. `project-manager` logs every completed task in `docs/WORKLOG.md` (and `docs/COMPONENTS.md` / `docs/DECISIONS.md` where relevant).
   Nothing counts as done until it's logged.

## Required design trends (from the client brief)
Every agent must apply these:
- **Performance first:** mobile-first, optimised images (AVIF/WebP, responsive `srcset`), lazy loading, LCP ≤ 2.5s.
- **AI-style personalisation:** content adapts to the visitor (season, returning vs first-time visitor, last shop viewed, browsing history for recommendations).
- **Kinetic typography:** scroll-triggered and cursor-responsive headline animation.
- **Micro-interactions and motion:** immediate feedback on hover, press, add-to-cart, form validation and loading states.
- **Dark mode and dynamic theming:** follow `prefers-color-scheme`, with a manual override that persists. Both themes must meet WCAG AA (4.5:1 body text).
- **Organic shapes and anti-grid layouts:** curves, asymmetry, SVG masks and shape dividers.
- **Accessibility first:** contrast, screen readers, full keyboard navigation, 44×44px tap targets, descriptive alt text, labelled form fields.
- **3D and immersive visuals:** only for hero or product showcase moments. Lazy-loaded, with compressed models (Draco/Meshopt glTF), and never at the cost of LCP.
- **Variable fonts and bold typography:** one variable font file per family, using weight and width axes.

Every animation must respect `prefers-reduced-motion`.
