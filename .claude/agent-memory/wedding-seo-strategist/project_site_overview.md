---
name: Site Overview
description: Tech stack, site architecture, page inventory, template structure, and current SEO state for Duffymog Studios
type: project
---

## Tech Stack
- Static site generator: Hugo
- Deployed via Cloudflare (wrangler.jsonc present)
- CSS: single bundled stylesheet at assets/css/style.css (inlined at build time via Hugo Pipes)
- No JavaScript framework — vanilla JS only
- Fonts: Google Fonts (Outfit, Caveat, DM Serif Display) loaded with preload/print swap pattern

## Site Identity
- Business: Duffymog Studios
- Photographers: Gabriela Duffy (lead) and Conor (second shooter)
- Base URL: https://www.duffymogstudios.ie/
- Location: Dublin, Ireland; travels all of Ireland
- Speciality: Wedding photography — documentary/candid style, no awkward posing
- Gabriela is half Spanish, speaks Spanish natively
- National Gallery of Ireland approved photographer
- Insured up to €6.5M
- Pricing: Weddings from €1,700 | Elopements from €600 | Engagements from €400
- Booking window: 2026 & 2027

## Page Inventory
- `/` — Homepage (hero, fun-strip, intro, gallery, testimonials, services/pricing, about, CTA)
- `/about/` — Full about page for Gabriela
- `/blog/` — Blog index (2 posts: national-gallery-of-ireland, welcome)
- `/contact/` — Contact page
- `/faq/` — FAQ page
- `/pricing/` — Pricing page

## Template Architecture
- `layouts/_default/baseof.html` — base shell
- `layouts/index.html` — homepage assembles partials in order: hero, fun-strip, intro, gallery, testimonial, services, about, cta
- `layouts/partials/head.html` — all SEO metadata (title, meta desc, OG, Twitter Card, canonical, schema)
- `layouts/partials/hero.html` — 3-image collage hero with rotating H1 text
- `layouts/partials/gallery.html` — masonry gallery with venue tags (5 placeholders still empty)
- `layouts/partials/about.html` — about split section on homepage (photo placeholder not yet filled)
- `layouts/partials/intro.html` — intro section (photo placeholder not yet filled)
- `layouts/partials/testimonial.html` — 4 Google reviews + trust badges
- `layouts/partials/services.html` — 3 service cards (Weddings, Elopements, Engagements) using emoji not photos
- `layouts/partials/cta.html` — CTA section
- `layouts/about/list.html` — full about page (2 photo placeholders not yet filled)

## Known SEO Issues (as of 2026-03-25)
- OG image hardcoded to couple-swoop.jpg for all pages (not page-specific)
- Schema image also hardcoded to couple-swoop.jpg
- About page and intro section have placeholder text instead of real images
- 5 of 9 gallery masonry slots are empty placeholders (Marlay Park, National Gallery, Glasson Lakehouse, Seafield Hotel, Amber Springs)
- No image file name convention using SEO keywords (images use couple codes like A-B, B-D, J-M)
- Blog has only 2 posts — significant content gap

## Why/How to Apply
Recommendations should prioritise filling gallery placeholders, adding real photos to about/intro sections, and expanding the blog with venue and location-specific content.
