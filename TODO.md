# Duffymog Studios — Launch Checklist

## Before launch

- [ ] **Google Search Console** — get your verification code from [search.google.com/search-console](https://search.google.com/search-console), paste it into `hugo.toml` under `[params] google_site_verification`, then submit your sitemap (`/sitemap.xml`)
- [ ] **Publish draft blog posts** — 5 posts are still `draft: true` and won't appear on the live site. Review each and remove `draft: true` when ready:
  - `content/blog/clontarf-castle-wedding-photography.md`
  - `content/blog/dublin-city-wedding-photography-locations.md`
  - `content/blog/powerscourt-estate-wedding-photography.md`
  - `content/blog/wedding-day-timeline-ireland.md`
  - `content/blog/winter-wedding-photography-ireland.md`

## Decap CMS setup (when ready)

- [ ] **Register a GitHub OAuth App** — github.com → Settings → Developer Settings → OAuth Apps. Set callback URL to `https://<your-worker-url>/callback`
- [ ] **Deploy the OAuth Worker** — `cd oauth-worker && npx wrangler deploy`, then run `npx wrangler secret put GITHUB_CLIENT_ID` and `npx wrangler secret put GITHUB_CLIENT_SECRET`
- [ ] **Update CMS config** — replace the placeholder `base_url` in `static/admin/config.yml` with your actual Worker URL
- [ ] **Add Gabriela as collaborator** — repo Settings → Collaborators → add her GitHub account with write access

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
