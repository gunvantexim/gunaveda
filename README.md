# Gunaveda™ Website — v3.1.0 Production Candidate

**Brand:** Gunaveda™ by Gunvant Exim, Malkapur, Maharashtra  
**Products:** Moringa Powder & Beetroot Powder (₹299 / 200g)  
**Live site:** [www.gunaveda.co.in](https://www.gunaveda.co.in)  
**FSSAI:** 11526054000061 | **WhatsApp:** +91-9730529974

---

## 📁 Project Structure

```
gunaveda/
├── index.html              ← Homepage (37KB)
├── moringa.html            ← Moringa Powder product page
├── beetroot.html           ← Beetroot Powder product page
├── shop.html               ← Shop
├── about.html              ← About Us
├── faq.html                ← Full FAQ (18 questions)
├── contact.html            ← Contact
├── privacy.html            ← Privacy Policy
├── terms.html              ← Terms & Conditions
├── shipping.html           ← Shipping & Returns
├── 404.html                ← Custom 404 error page
│
├── favicon.ico             ← 32×32 browser tab icon
├── site.webmanifest        ← PWA manifest
├── robots.txt              ← Crawler rules
├── sitemap.xml             ← 10 page URLs
├── netlify.toml            ← Deploy: headers, caching, redirects
│
├── css/
│   ├── style.css           ← All base styles + design tokens
│   ├── animations.css      ← scroll-behavior
│   └── responsive.css      ← Mobile breakpoints
│
├── js/
│   ├── app.js              ← Mobile menu, scroll reveal, announce dismiss
│   └── ui.js               ← Tabs, FAQ accordion, newsletter
│
├── images/
│   ├── logo.png            ← Logo (7KB)
│   ├── apple-touch-icon.png ← iOS home screen icon (180×180)
│   ├── *.webp              ← WebP versions (all 15 images)
│   └── *.png / *.jpg       ← JPEG fallback originals
│
├── PROJECT_STATE.md        ← Project status & resume point
├── VERSION.md              ← Version history
├── TODO.md                 ← Remaining tasks
├── CHANGELOG.md            ← Full change history
└── README.md               ← This file
```

---

## ✏️ Quick Edit Guide

| What | Where | How |
|---|---|---|
| **Price** | All `.html` files | Ctrl+F `₹299` |
| **WhatsApp** | All `.html` files | Ctrl+F `919730529974` |
| **Amazon link** | All `.html` files | Ctrl+F `amazon.in/s?k=gunaveda` |
| **Flipkart link** | All `.html` files | Ctrl+F `flipkart.com/search?q=gunaveda` |
| **Brand colours** | `css/style.css` | Edit `:root` block |
| **Announcement** | All `.html` files | Edit `.announce-bar` div |

---

## 🚀 Deploy to Netlify (Recommended)

**Option A — Drag & Drop (fastest):**  
1. Drag this entire folder to [app.netlify.com/drop](https://app.netlify.com/drop)  
2. Set custom domain: `www.gunaveda.co.in`

**Option B — GitHub (auto-deploy):**  
1. Push all files to GitHub repo (main branch, root folder)
2. Connect repo in Netlify → Settings → Domain → `www.gunaveda.co.in`
3. Every `git push` auto-deploys

---

## 🚀 Deploy to GitHub Pages

1. Push all files to `main` branch root
2. Settings → Pages → Branch: `main`, Folder: `/(root)`
3. Add custom domain: `www.gunaveda.co.in`
4. DNS at registrar: 4×A records + CNAME `www`

---

## 📊 Lighthouse Targets

| Category | Expected Score |
|---|---|
| Performance | 95+ |
| Accessibility | 100 |
| Best Practices | 100 |
| SEO | 100 |

---

## ➕ Adding a New Product

1. Copy `moringa.html` → `amla.html`
2. Update: `<title>`, meta desc, canonical URL, h1, hero gradient, images, content
3. Add `<a href="amla.html">` to nav in all 11 pages
4. Add footer link in all 11 pages
5. Add to `sitemap.xml`
6. Add Product schema in `amla.html`
