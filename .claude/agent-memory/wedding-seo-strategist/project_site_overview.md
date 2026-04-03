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

## Known SEO Issues (as of 2026-04-02) — updated after full audit
- OG image hardcoded to couple-swoop.jpg for ALL pages — not page-specific
- Schema image also hardcoded to couple-swoop.jpg
- Sitemap built against localhost:1313 — confirmed in public/sitemap.xml, all locs show http://localhost:1313/ — CRITICAL
- Sitemap includes /tags/, /tags/news/, /categories/ taxonomy pages — crawl budget dilution
- hugo.toml title is just "Duffymog Studios" — used as fallback; homepage title renders correctly via _index.md
- /pricing/ page H1 is just "Pricing" — weak, not keyword-rich
- /weddings/ page H1 is just "The Gallery" — not keyword-rich
- /about/ H1 is "Hi, I'm Gabriela. Half Spanish, fully obsessed with photography." — no keyword
- Contact page and blog/_index.md have no specific H1 (blog list uses .Title from frontmatter)
- No BreadcrumbList schema on any page
- No WebSite schema (sitelinks searchbox opportunity)
- Blog single template (single.html) has no featured image — no og:image override per post
- Blog Article schema missing image field
- Blog posts have no photos embedded in content (both posts are text-only)
- National Gallery blog post has no photos despite being a photo showcase
- "welcome" blog post has zero SEO value — just an announcement
- No schema markup on /weddings/ or /about/ pages
- Blog index list.html has no featured images on post cards
- FAQ not in nav (only in footer) — reduces internal linking equity to /faq/
- No location/venue-specific landing pages
- No elopement-specific landing page
- Filenames with special chars still in assets/images/: Grooms&Dogs.jpg, Grooms&Dogs2.jpg, Grooms_Cinema.jpg — risk in some environments
- BROKEN REFERENCES in weddings/list.html: two-grooms-cinema-portrait-ireland.jpg (missing — Grooms_Cinema.jpg exists), H-G-7.jpg (missing), A-B-1-5.jpg (missing), A-B-1-6.jpg (missing)
- BROKEN REFERENCE in about/list.html: GuestsLaughing.jpg (missing from assets/images/)
- gallery.html slot 4 uses Dancefloor3.jpg but alt says "Bride with bridesmaids" — wrong, Dancefloor3 is groom with microphone
- hero.html hero-img-1 carousel: IMG_3633.jpg alt says "Couple embracing during golden hour" — generic
- hero.html hero-img-2: Dancefloor3.jpg alt says "First dance under fairy lights" — wrong (it's the groom mic shot)
- hero.html hero-img-3: Grooms_Cinema.jpg has problematic filename character (_) — low risk but noted
- Local business schema has no telephone number field
- Local business schema has no openingHours field
- Local business schema sameAs only has Instagram — no Google Business Profile, Facebook, etc.
- No WebPage schema on key commercial pages (/weddings/, /pricing/)
- robots.txt is correct — points to production sitemap URL (production sitemap itself is the problem)

## Content Gaps
- Only 2 blog posts — major gap vs competitors
- No venue-specific pages
- No county/region landing pages (Wicklow, Meath, Louth, Westmeath etc.)
- No elopement-specific page beyond pricing section
- No engagement photography dedicated page
- No real wedding story posts with photos
- Same-sex couples coverage strong in portfolio but zero dedicated content or page
- No Spanish-language content despite Gabriela being a native Spanish speaker (local differentiator)
- No "how to choose a wedding photographer" or buyer education content

## Template Architecture (confirmed 2026-04-02)
- layouts/_default/list.html — blog index template (no featured images on cards)
- layouts/_default/single.html — blog post template (no featured image, no schema image field)
- layouts/about/list.html — full about page (H1 has no keyword)
- layouts/weddings/list.html — full gallery with 48 shuffled images; 4 broken file references
- layouts/pricing/list.html — full pricing page (H1 is just "Pricing")
- layouts/faq/list.html — FAQ page (H1 is "Wedding Photography FAQs" — good)
- layouts/contact/ — no dedicated layout file found; uses contact-form partial inline

## Image Asset Status (2026-04-02)
- 48 files in assets/images/
- 4 files referenced in templates but MISSING from assets/images/: two-grooms-cinema-portrait-ireland.jpg, H-G-7.jpg, A-B-1-5.jpg, A-B-1-6.jpg
- 1 file referenced in about/list.html but MISSING: GuestsLaughing.jpg
- Grooms_Cinema.jpg exists and works fine despite underscore in filename
- Grooms&Dogs.jpg and Grooms&Dogs2.jpg exist and are used in hero carousel
- OG image source (couple-swoop.jpg) confirmed present in assets/images/
