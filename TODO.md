# Duffymog Studios — Launch Checklist

## Before launch

- [ ] **Google Search Console** — get your verification code from [search.google.com/search-console](https://search.google.com/search-console), paste it into `hugo.toml` under `[params] google_site_verification`, then submit your sitemap (`/sitemap.xml`)
- [ ] **Publish draft blog posts** — 5 posts are still `draft: true` and won't appear on the live site. Review each and remove `draft: true` when ready:
  - `content/blog/clontarf-castle-wedding-photography.md`
  - `content/blog/dublin-city-wedding-photography-locations.md`
  - `content/blog/powerscourt-estate-wedding-photography.md`
  - `content/blog/wedding-day-timeline-ireland.md`
  - `content/blog/winter-wedding-photography-ireland.md`
- [ ] **Apple touch icon** — create a 180x180px PNG of the logo and save as `static/apple-touch-icon.png` (referenced in `head.html` but file is missing — iOS home screen bookmark shows a blank icon without it)

## Decap CMS setup (when ready)

- [ ] **Register a GitHub OAuth App** — github.com → Settings → Developer Settings → OAuth Apps. Set callback URL to `https://<your-worker-url>/callback`
- [ ] **Deploy the OAuth Worker** — `cd oauth-worker && npx wrangler deploy`, then run `npx wrangler secret put GITHUB_CLIENT_ID` and `npx wrangler secret put GITHUB_CLIENT_SECRET`
- [ ] **Update CMS config** — replace the placeholder `base_url` in `static/admin/config.yml` with your actual Worker URL
- [ ] **Add Gabriela as collaborator** — repo Settings → Collaborators → add her GitHub account with write access

## SEO improvements (post-launch)

### High impact

- [ ] **Add `ogImage` to every blog post** — currently all posts share the same fallback OG image (Darver Castle) when shared on social media. Add `ogImage: "Weddings/[relevant-image].jpg"` to each post's frontmatter. Good candidates:
  - `best-castle-wedding-venues-ireland.md` → `Weddings/darver-castle-wedding-blue-hour-veil.jpg`
  - `best-wedding-venues-dublin.md` → `Weddings/BrideShelbourneHotel.jpg`
  - `how-to-elope-in-ireland.md` → `Weddings/GlassonLakeHouseElope.jpg`
  - `how-much-does-a-wedding-photographer-cost-in-ireland.md` → `Weddings/couple-swoop.jpg`
  - `how-to-choose-wedding-photographer-ireland.md` → `Weddings/bridesmaids-bride-getting-ready-seaview.jpg`
  - `national-gallery-of-ireland.md` → needs a National Gallery photo (none in assets yet)
- [ ] **Improve gallery alt text** — 31 of 46 images in `data/gallery.json` have generic alt text with no venue/location context. Good alt text follows: `[Subject] + [action] + [venue name] + [county]`. Example: change `"Candid moment between couple on their wedding day"` to `"Couple laughing during speeches at Ballymagarvey Village, Co. Meath"`
- [ ] **Add Article schema publisher logo** — in `layouts/partials/schema.html` (line 160), add a `logo` object to the `publisher` field so blog posts are eligible for Google Article rich results
- [ ] **Fix `og:type` for area pages** — area pages currently get `og:type: article` instead of `website`. In `layouts/partials/head.html` line 15, change to: `{{ if and .IsPage (eq .Section "blog") }}article{{ else }}website{{ end }}`

### Medium impact

- [ ] **Add phone number to schema** — uncomment and set the `phone` param in `hugo.toml` if there's a business number. NAP consistency (Name/Address/Phone) is a direct local SEO ranking signal
- [ ] **Add Google Business Profile URL to `sameAs`** — in `layouts/partials/schema.html` line 34, add your Google Business Profile URL alongside the Instagram link
- [ ] **Dynamic geo tags for area pages** — in `layouts/partials/head.html` lines 27-28, geo tags are hardcoded to Dublin for all pages including `/areas/galway/` etc. Make them dynamic using `.Params.area`
- [ ] **Fix hero carousel alt text** — slide 5 in `layouts/partials/hero.html` describes the Darver Castle blue-hour veil shot as "golden hour" — should match the actual image
- [ ] **Add `og:image:width`/`og:image:height`** — Facebook may skip rendering OG images without dimensions. Add after the `og:image` tag in `head.html`
- [ ] **Cross-link blog posts to `/pricing/` and `/faq/`** — only one post currently links to pricing. Add natural in-text links from cost-related and booking-related posts

### Nice to have

- [ ] **Add `Review` schema for testimonials** — the 4 Google reviews in `data/reviews.json` could be surfaced as `Review` schema alongside the existing `aggregateRating` for richer search results
- [ ] **Add `ImageGallery` schema to `/weddings/`** — signals to Google Image Search that this is a curated professional gallery
- [ ] **Consider noindexing tag pages** — `/tags/wedding/` etc. have low standalone ranking value and dilute crawl budget. Add `<meta name="robots" content="noindex">` to `layouts/tags/taxonomy.html` and `layouts/tags/term.html` if you'd prefer Google focus on content pages
- [ ] **LCP preload for homepage hero** — add `<link rel="preload">` in `head.html` for the first hero carousel image to improve Largest Contentful Paint on slow connections

## Blog post ideas (by priority)

1. **"Real Wedding: [Couple] at [Venue], Co. [County]"** — real wedding features rank for venue-specific searches and serve as social proof. Even 2-3 per year is transformative
2. **"Engagement Photography Dublin — What to Expect and Where to Go"** — the site offers engagement photography but has zero dedicated content for it
3. **"Documentary Wedding Photography: What It Is and Why It Suits Irish Weddings"** — Gabriela's USP with real search volume, not explained anywhere on the site
4. **"How to Plan an Intimate Wedding in Ireland (20 Guests or Fewer)"** — bridges the gap between the elopement guide and full weddings
5. **"10 Questions to Ask a Wedding Photographer Before You Book"** — action-oriented, converts well, complements the existing "how to choose" guide
6. **Venue-specific posts** (Tankardstown House, Glasson Lakehouse, Wicklow Mountains) — link naturally to orphaned area pages like `/areas/westmeath/`
7. **"Spring Wedding Photography in Ireland"** — seasonal complement to the winter wedding draft
8. **"What to Wear for Your Wedding Photos"** — evergreen, high Pinterest sharing potential

## Ongoing

- [ ] **Keep review count current** — update `reviewCount` in `layouts/partials/schema.html` (line 33) as new Google reviews come in (currently 29)
- [ ] **Blog content** — aim for 1-2 posts per month for sustained SEO growth. Use the Decap CMS at `/admin/` once set up

## Already done

- [x] FAQ section — live at `/faq/` and on the pricing page
- [x] Blog section — 12 posts (7 live, 5 draft)
- [x] Contact form — wired to Formspree
- [x] Google reviews — 4 real 5-star reviews on homepage
- [x] AggregateRating schema — structured data for Google star snippet
- [x] Mobile QA — about page facts grid bug fixed
- [x] Trust badges — consistent across all pages
- [x] Photos and alt text — all gallery, hero, services, and about images in place
- [x] Testimonials — 4 real named Google reviews on homepage
- [x] Tag pages — browsable at `/tags/` with pills on all blog posts
- [x] Related posts — "You might also like" section on blog posts
- [x] Social share buttons — Facebook, WhatsApp, Pinterest, Email on blog posts
- [x] Sitemap lastmod — git commit dates populate `<lastmod>` automatically
- [x] Decap CMS — admin interface ready at `/admin/` (needs OAuth setup above)
- [x] Areas linked from footer — `/areas/` now discoverable for Google and visitors
