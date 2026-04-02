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
- Fonts: Google Fonts (Outfit, Caveat, DM Serif Display, Playwrite IE) loaded with preload/print swap pattern
- Images: Hugo Pipes generates WebP srcsets at build time via layouts/partials/responsive-img.html

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

## Page Inventory (as of 2026-04-02)
- `/` — Homepage (hero, fun-strip, gallery, testimonials, services/pricing, about, contact form)
- `/about/` — Full about page for Gabriela (H1 present, 2 images, testimonial, contact form)
- `/weddings/` — Full image gallery (~50 images, masonry layout, mid-page CTA)
- `/blog/` — Blog index (2 posts: national-gallery-of-ireland, welcome)
- `/contact/` — Contact page (just the contact form partial)
- `/faq/` — FAQ page with 14 Q&As, FAQPage schema
- `/pricing/` — Full pricing page (3 package tiers, FAQ section, FAQPage schema)

## Template Architecture
- `layouts/_default/baseof.html` — base shell with lang="en-ie", nav, main, footer, scroll-reveal, schema
- `layouts/index.html` — homepage assembles: hero, fun-strip, gallery, testimonial, services, about, contact-form
- `layouts/partials/head.html` — all SEO metadata (title, meta desc, OG, Twitter Card, canonical, schema call, geo tags)
- `layouts/partials/schema.html` — LocalBusiness + ProfessionalService (homepage only), FAQPage (pages with faq param), Article (blog posts)
- `layouts/partials/hero.html` — 3-column image carousel with rotating H1
- `layouts/partials/gallery.html` — masonry gallery (9 slots, all filled as of 2026-04-02)
- `layouts/partials/about.html` — about split section on homepage (gabriela photo filled)
- `layouts/partials/intro.html` — intro section (gabriela photo filled)
- `layouts/partials/testimonial.html` — 4 Google reviews + trust badges
- `layouts/partials/services.html` — 3 service cards with real images
- `layouts/partials/responsive-img.html` — generates WebP srcset from assets/images/

## Known SEO Issues (as of 2026-04-02)
- OG image hardcoded to couple-swoop.jpg for ALL pages — not page-specific
- Schema image also hardcoded to couple-swoop.jpg
- Sitemap was built against localhost:1313 (not production URL) — all locs show http://localhost:1313/
- Sitemap includes tag taxonomy pages (/tags/, /tags/news/, etc.) which dilute crawl budget
- hugo.toml title is just "Duffymog Studios" with no keyword — used as site title fallback
- homepage title tag renders as "Wedding Photographer Dublin & Ireland | Duffymog Studios" — good
- Non-homepage pages use page Title only (e.g. "About Gabriela — Duffymog Studios") — some titles lack keywords
- Contact page meta description is thin ("Get in touch with Duffymog Studios to book your wedding photography in Dublin and across Ireland.")
- No BreadcrumbList schema on any page
- No SiteNavigationElement or WebSite schema with sitelinks searchbox
- Blog single template (single.html) has no featured image in the article — no og:image override per post
- Blog posts have no images embedded in the content — text only
- Blog Article schema missing image field
- The "welcome" blog post has no SEO value — just an announcement, no keywords
- National Gallery blog post has no actual photos embedded in it
- /weddings/ gallery page H1 is just "The Gallery" — not keyword-rich
- /about/ page H1 is "Hi, I'm Gabriela. Half Spanish, fully obsessed with photography." — misses keyword opportunity in heading
- FAQ page has H1 "Wedding Photography FAQs" — good
- No sitemap priority or changefreq hints configured
- No schema markup on /weddings/ gallery page
- No schema markup on /about/ page
- Logo in nav/footer uses static file (not processed by Hugo Pipes) — no width/height optimisation
- Blog index list template has no featured images on post cards
- Internal link from nav missing: FAQ not in nav (only in footer)
- No location/venue-specific landing pages (e.g. /weddings/darver-castle/, /weddings/dublin/)
- No elopement-specific landing page
- No Irish language hreflang (not needed but noted)
- Google Business Profile status: unknown

## Content Gaps
- Only 2 blog posts — major gap vs competitors
- No venue-specific pages
- No county/region landing pages (Wicklow, Meath, Louth, Westmeath etc.)
- No elopement-specific page beyond pricing section
- No engagement photography dedicated page
- No real wedding story posts with photos
