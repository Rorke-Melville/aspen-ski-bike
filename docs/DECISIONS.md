# Decisions

## 2026-11-14 — Landing site + two product-first shop sites (not a full merge)
**Decision:** Build a new React/TypeScript landing site on Netlify that routes customers to aspenbikes.com and aspenskis.com.
Rework both Squarespace sites to be product-first, and give all three one shared design system.

**Why:** Both shops' ordering and booking systems stay untouched, which is the biggest risk in a merge. The owners get one
front door and one consistent look. The landing page is a product-led storefront (in-season shop first, best sellers deep-linking
to products), so it shortens the path to checkout instead of adding a step.

**Trade-offs accepted:** bikes and skis keep separate carts, and there are three properties to maintain.
