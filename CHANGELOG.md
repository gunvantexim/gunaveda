# CHANGELOG — Gunaveda™ Website

---

## v3.1.0 — Pre-Launch QA (Production Candidate)
**Date:** July 2025

### Summary
Final quality assurance pass. All audits passed. Website is launch-ready.

### Fixes & Additions

**Cleanup**
- Deleted `{css,js,images}/` accidental empty folder
- Deleted `gunaveda-fixed/` backup folder (1.7MB removed from repo)

**Images**
- All 15 images converted to WebP with `<picture>` + JPEG fallback
- Additional WebP saving: 418KB
- `favicon.ico` created (32×32 from logo)
- `images/apple-touch-icon.png` created (180×180 PNG)

**PWA**
- `site.webmanifest` created with name, icons, theme_color, start_url
- All 11 HTML files updated with manifest link
- All 11 HTML files updated with favicon.ico link
- `theme-color` meta already present — verified

**404 Page**
- `404.html` created with full branding, nav, footer
- Friendly message, Home/Shop/WhatsApp buttons, quick links
- Full SEO: canonical, OG, Twitter, schema, robots noindex
- `netlify.toml` updated with 404 catch-all redirect

**SEO Fixes**
- meta descriptions fixed on: about.html, beetroot.html, contact.html, moringa.html
- All now ≤ 160 chars (previously up to 182)

**CSS**
- 404 page styles added to `style.css` (no inline `<style>` anywhere)

**robots.txt**
- Removed incorrect `Disallow: /images/`, `Disallow: /css/`, `Disallow: /js/`
  (these were blocking crawlers from loading page resources)

**Documentation**
- `VERSION.md` created
- `TODO.md` created
- `PROJECT_STATE.md` updated to v3.1.0
- `CHANGELOG.md` updated

### Final Audit Results
- 11 HTML pages × 18 checks = 198 total checks
- **198/198 passed ✅**
- Zero broken internal links
- Zero duplicate meta tags
- Zero missing alt text
- Zero missing loading attributes
- Zero inline style sheets
- Zero dead href="#" links

---

## v3.0.0 — Multi-Page Architecture
**Date:** July 2025

### Summary
Converted the Single-Page Application (SPA) into a true multi-page website with individual URLs for every page. This milestone enables better SEO, allows direct linking, improves browser history behaviour, and supports crawling by search engines on a per-page basis.

### Pages Created / Converted

| Page | Type | Notes |
|---|---|---|
| `index.html` | Converted | Home page — was SPA shell |
| `moringa.html` | Converted | Moringa product page |
| `beetroot.html` | Converted | Beetroot product page |
| `shop.html` | Converted | Shop / buy page |
| `about.html` | Converted | About Gunaveda / Gunvant Exim |
| `contact.html` | Converted | Contact information |
| `faq.html` | **New** | Full FAQ (4 sections, 18 questions) |
| `privacy.html` | **New** | Privacy Policy |
| `terms.html` | **New** | Terms & Conditions |
| `shipping.html` | **New** | Shipping & Returns Policy |

### JavaScript Changes
- **Removed** `showPage()` function — replaced by standard `<a href="">` navigation
- **Removed** `initNavShadow()` dependency on page switching
- Retained: `toggleMenu()`, `dismissAnnounce()`, `initScrollReveal()`, `initNavShadow()`
- `toggleMenu()` updated to properly sync `aria-expanded` on hamburger

### CSS Changes
- **Removed** `.page{display:none}` — dead code in multi-page architecture
- **Removed** `.page.active{display:block}` — no longer needed
- `pageFadeIn` keyframe retained for potential use in page transitions

### Navigation
- All `onclick="showPage('xxx');return false"` → `href="xxx.html"` real links
- All `href="#"` dead anchors replaced with real page URLs
- Active nav state set correctly per-page (hardcoded in each page's nav)
- Mobile menu links all updated to real hrefs

### SEO Additions (per new page)
Each new page includes:
- Unique `<title>` optimised for search intent
- Unique `<meta name="description">` ≤160 chars
- `<link rel="canonical">` with absolute URL
- Complete Open Graph block (title, desc, image, locale, site_name)
- Twitter Card (summary_large_image)
- BreadcrumbList structured data
- Organization schema (on all pages)
- FAQPage schema (on faq.html)
- Product schema retained on moringa.html and beetroot.html

### Sitemap
- Updated `sitemap.xml` from 6 hash-URLs to 10 real page URLs
- Priorities set: home=1.0, products=0.9, shop=0.8, faq=0.7, others=0.3–0.6

### Netlify Configuration
- Added backwards-compat redirects: `/#moringa` → `/moringa.html` etc.
- Retained: HTTPS forced redirect, security headers, cache rules
- Added: separate cache rule for `/*.html` (no-cache, must-revalidate)

### Footer
- All pages now have a 4-column footer
- Column 3 (Company) includes links to: About, Shop, FAQ, Contact, WhatsApp
- Column 4 (Legal) includes: Privacy Policy, Terms & Conditions, Shipping & Returns

### New Pages Content
- **faq.html**: 4 sections (General, Usage, Safety, Orders) with 18 FAQ items and FAQPage schema
- **privacy.html**: 8-section privacy policy covering data collection, usage, rights and contact
- **terms.html**: 8-section terms covering products, ordering, pricing, IP, liability and jurisdiction
- **shipping.html**: Ordering channels (WhatsApp, Amazon, Flipkart), delivery timelines and returns policy

---

## v2.0.0 — Senior Code Review & Optimisation
**Date:** July 2025

### Summary
Full production-quality code review applied to the refactored project. All Lighthouse, SEO, accessibility and performance issues fixed.

### Issues Fixed
- **Contrast**: 6 footer/brand-details colours failing WCAG AA (now all ≥4.5:1)
- **Buttons**: 23 `<button>` tags missing `type="button"` (causes accidental form submission)
- **Aria**: `aria-expanded` on hamburger not updated by JS (now synced)
- **Accessibility**: `role="banner"` on `<div>` removed (invalid landmark)
- **Accessibility**: `.faq-icon` missing `aria-hidden="true"`
- **Touch targets**: `.foot-social-btn` 36→44px, hamburger padding increased
- **Meta description**: 182 chars → 141 chars (Google truncates at 160)
- **SEO**: Added favicon, theme-color, robots meta, twitter:image, og:locale, og:site_name
- **SEO**: OG image changed from relative to absolute URL
- **SEO**: Added Product schema (x2), BreadcrumbList schema, WebSite schema
- **CSS**: Removed 11 unused class groups (recipe, compare-table, img-banner, etc.)
- **CSS**: Merged duplicate `.nav-links a{}` (was in both style.css and animations.css)
- **CSS**: Removed all 6 `!important` from `.nav-cta` (fixed with specificity instead)
- **CSS**: Removed `scroll-behavior` duplicate
- **Images**: Compressed 5,143 KB → 1,610 KB (69% reduction)
- **Images**: All 19 `<img>` tags now have `width` + `height` (CLS prevention)
- **Images**: `logo.png` 207KB → 7KB (was serving 1536×1024 for 42×42 display)
- **Performance**: All images have `loading="eager"` or `loading="lazy"`
- **Content**: Footer URL fixed `gunaveda.in` → `www.gunaveda.co.in`

---

## v1.0.0 — Initial Refactor
**Date:** July 2025

### Summary
Converted monolithic single-file HTML (6.9 MB, base64 embedded images) into a properly structured multi-file project.

### Changes
- Extracted 15 base64 images → `images/` folder
- Created `css/style.css` (base styles + design tokens)
- Created `css/animations.css` (transitions, hover effects)
- Created `css/responsive.css` (mobile/tablet breakpoints)
- Created `js/app.js` (navigation functions)
- Created `js/ui.js` (tab switching, FAQ accordion, newsletter)
- All content preserved: price ₹299, Amazon/Flipkart/WhatsApp links, FSSAI details
- HTML reduced from 6,923 KB to 42 KB
- Added: robots.txt, sitemap.xml, README.md
- Added: Canonical URL, Open Graph, Twitter Card
- Added: Organization schema, FAQ schema, Product schema
