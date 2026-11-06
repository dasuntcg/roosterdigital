# 🐓 Rooster Digital — SEO Audit & Action Plan

**Focus markets:** Ballarat (VIC) + Albury-Wodonga (VIC/NSW border)
**Target audience:** Small business & tradies
**Date:** 2026-07-06
**SEO Health Score:** 37 / 100 🔴

---

## Score Breakdown

| Category | Score | Weight | Notes |
|----------|-------|--------|-------|
| Technical SEO | 40 | 22% | No robots.txt, no sitemap, no canonical |
| Content Quality | 35 | 23% | Generic, thin, zero local content |
| On-Page SEO | 45 | 20% | One H1 ✓ but no local keywords, broken nav anchors |
| Schema / Structured Data | 0 | 10% | None at all |
| Performance (CWV) | 70 | 10% | Astro static = fast, but external hero + blocking fonts |
| AI Search Readiness (GEO) | 20 | 10% | No schema, no llms.txt, no citable facts |
| Images | 40 | 5% | Alt text present, but external stock hero, no dimensions |

**Biggest gap:** You want to rank in Ballarat and Albury-Wodonga, but neither city
appears anywhere on the site. No location content, address, phone, or local schema.
As-is, the page cannot rank locally for anything.

---

## Core Strategic Problem

Targeting **two geographically distinct markets** (~350 km apart) from a **single
homepage with no location signals**. Google can't rank one generic page in two cities.

**The fix is an architecture change, not just tweaks:** one homepage + two dedicated
location landing pages, each with genuinely unique local content, plus a Google
Business Profile strategy.

---

## Findings by Priority

### 🔴 CRITICAL (blocks ranking / do first)

1. **No location content anywhere.** "Ballarat" and "Albury/Wodonga" appear zero times.
2. **No NAP (Name, Address, Phone).** Footer.astro and Nav.astro have no phone,
   address, or service area. NAP consistency is a top-3 local ranking factor.
3. **No structured data.** Zero JSON-LD. Need `ProfessionalService`/`LocalBusiness`
   schema with `areaServed` for both cities.
4. **No real contact mechanism.** Every CTA links to `#contact` → CtaBanner.astro,
   which only contains buttons linking back to `#contact`. Circular dead-end — no
   form, email, or phone to convert a visitor.
5. **Broken navigation anchors.** Nav.astro links to `#portfolio`, `#pricing`,
   `#about` — none of these sections exist.

### 🟠 HIGH (fix within 1 week)

6. **Generic, location-free title & meta.** Layout.astro: "Web Design for Tradies &
   Small Business" — no city, no differentiation.
7. **No Open Graph / Twitter Card tags.** Shared links (Facebook/WhatsApp) look broken.
8. **No canonical URL**, and `lang="en"` should be `lang="en-AU"`.
9. **No robots.txt and no sitemap.xml.** Add `@astrojs/sitemap` + robots file.
10. **Thin / unverifiable trust content.** Stats (50+ clients, 200+ projects, 98%,
    5★) appear twice with no named testimonials, client logos, or Google reviews.
11. **`RecentProjects` imported but not rendered** (index.astro:8) — and no
    `#portfolio` section the nav points to. Wire it up.

### 🟡 MEDIUM (fix within 1 month)

12. **External Unsplash hero image** (Hero.astro:55) — generic stock, off-domain,
    no width/height (CLS + LCP risk). Self-host an optimized WebP.
13. **Render-blocking Google Fonts** (Layout.astro) — self-host or preload + swap.
14. **No favicon set / apple-touch-icon / theme-color.**
15. **No blog / content engine** for informational local queries.

### 🔵 LOW (backlog)

16. No `llms.txt` for AI search citability.
17. Lottie JSON duplicated in `src/assets` and `public`.
18. Footer "Company" links (Maintenance, Terms) point to `#`.
19. No 404 page.

---

## Action Plan (sequenced by dependency)

### Phase 1 — Foundation & Local Entity (Week 1) 🔴
*Goal: make the site a valid, contactable local business Google can trust.*

1. **Add real NAP.** Pick a primary business location. Add phone + email +
   service-area line to Footer and Nav. One exact NAP format everywhere.
2. **Build a real contact path.** Replace circular `#contact` with an actual form
   (Formspree/Netlify/Vercel) plus a visible `tel:` phone link and email.
3. **Add `ProfessionalService` JSON-LD** with name, url, telephone,
   `areaServed: ["Ballarat VIC", "Albury-Wodonga"]`, sameAs (socials), and
   aggregateRating (only if genuine reviews).
4. **Fix broken nav anchors** — build the missing sections or remove/repoint links.
   Wire up the already-imported RecentProjects.
5. Set `lang="en-AU"`, add canonical, add robots.txt + `@astrojs/sitemap`.

### Phase 2 — Local Landing Pages (Weeks 2–3) 🔴🟠
*Goal: a rankable page per target city. Core of the dual-market strategy.*

6. Create `/web-design-ballarat` and `/web-design-albury-wodonga` as real routes.
   Each needs 60%+ unique content (not a city-name find-and-replace):
   - Local H1: "Web Design in Ballarat for Tradies & Small Business"
   - Area-specific intro, suburbs served, local project/testimonial, local FAQ
   - Its own title, meta, canonical, and `areaServed` schema
7. Optimize homepage title around primary city, e.g. "Rooster Digital — Web Design
   & SEO for Ballarat & Albury-Wodonga Small Business"; link to both location pages.
8. Add OG/Twitter tags with a branded `og:image`.

> ⚠️ Quality gate: two location pages is safe. If expanding to surrounding towns
> (Wendouree, Lavington, etc.), keep each page genuinely unique. Risk flagged at
> 30+ location pages.

### Phase 3 — Google Business Profile & Off-Site (Weeks 3–4) 🟠
*Goal: get into the map pack, where most local searches convert.*

9. **Set up GBP as a Service-Area Business (SAB)** — hide street address, list
   Ballarat + Albury-Wodonga service areas. Note: Google allows only ONE GBP per
   real location. A second GBP requires a genuine staffed presence there. Start with
   one GBP in your home city; location pages rank the second city until then.
10. Build **NAP citations** in AU directories (True Local, Yellow Pages AU, Hotfrog,
    local chambers) — identical NAP.
11. Ask existing clients for **Google reviews** mentioning their suburb/city.

### Phase 4 — Content & Performance (Month 2) 🟡
*Goal: capture informational local intent and protect Core Web Vitals.*

12. Self-host hero image (WebP + width/height), self-host or preload fonts.
13. Launch a small local blog: "How much does a website cost in Ballarat?",
    "Why every Albury-Wodonga tradie needs a Google Business Profile", etc.
14. Add `llms.txt` and keep schema rich for AI Overviews / ChatGPT / Perplexity.

---

## Priority Keyword Targets

| Market | Primary | Secondary / Long-tail |
|--------|---------|----------------------|
| Ballarat | web design ballarat, web designer ballarat, seo ballarat | affordable websites ballarat, web design for tradies ballarat, logo design ballarat |
| Albury-Wodonga | web design albury wodonga, web designer wodonga, seo albury | small business websites albury, tradie websites wodonga, branding albury wodonga |

---

## Leading Indicators to Watch (no re-audit needed)

- **Search Console:** impressions for `*ballarat` / `*wodonga` queries (Phase 2 working)
- **GBP Insights:** map-pack discovery searches & direction requests (Phase 3 working)
- **Form submissions / calls:** the real conversion signal (Phase 1 working)

---

## Open Question

**Which city is the business actually based in?** This determines the primary GBP
location and the homepage title's primary market.
