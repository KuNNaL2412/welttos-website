# Welttos — Website

Marketing website for **Welttos**, a Pune-based AI & Tech solutions company. Static multi-page site with vanilla HTML / CSS / JS — no build step, no dependencies, deploys to GitHub Pages out of the box.

---

## 📁 Folder Structure

```
welttos-website/
├── index.html              # Home page
├── products.html           # Products & services
├── pricing.html            # Pricing plans
├── about.html              # About / team
├── contact.html            # Contact form (Formspree + custom thank-you popup)
├── 404.html                # Custom 404 page
│
├── css/
│   └── styles.css          # All styles (dark + light theme, components, modal)
│
├── js/
│   └── main.js             # Canvas background, theme toggle, FAQ, AJAX form handler
│
├── assets/
│   ├── logo.svg            # Brand logo (vector, used as primary favicon + OG image)
│   ├── favicon.ico         # Multi-size ICO for legacy browsers
│   ├── favicon-16x16.png   # Tab icon (small)
│   ├── favicon-32x32.png   # Tab icon (high-DPI)
│   ├── apple-touch-icon.png  # iOS Home Screen icon (180×180)
│   ├── icon-192.png        # PWA icon (Android, Chrome)
│   └── icon-512.png        # PWA icon (high-res) + Open Graph share image
│
├── images/                 # Product screenshots — drop your PNGs here
│   ├── ai-voice-agents.png
│   ├── document-monitoring.png
│   └── my-gate-app.png
│
├── manifest.json           # PWA manifest (Add to Home Screen support)
├── sitemap.xml             # Search engine sitemap
├── robots.txt              # Crawler instructions
├── .nojekyll               # Disables Jekyll on GitHub Pages
├── .gitignore
└── README.md
```

---

## 🚀 Deploy to GitHub Pages

### 1. Create the repo
On GitHub, click **New repository**. Two options:

| Repo name | Live URL |
|-----------|----------|
| `<username>.github.io` | `https://<username>.github.io/` |
| `welttos-site` (or anything) | `https://<username>.github.io/welttos-site/` |

### 2. Push the code
```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/<username>/<repo-name>.git
git push -u origin main
```

### 3. Enable Pages
Repo **Settings → Pages → Source:** `main` / `/ (root)` → **Save**. Live in ~30 seconds.

### 4. Add your product images
Drop `ai-voice-agents.png`, `document-monitoring.png`, `my-gate-app.png` into `images/`.

---

## 🌐 Custom Domain (optional)

1. Create a `CNAME` file (no extension) at the repo root containing your domain:
   ```
   welttos.com
   ```
2. At your domain registrar's DNS, add A-records to GitHub's IPs:
   `185.199.108.153` · `185.199.109.153` · `185.199.110.153` · `185.199.111.153`
3. Settings → Pages → enter custom domain → tick **Enforce HTTPS** after DNS propagates.

---

## 🔍 SEO Setup (Already Done in Code)

The site ships with everything Google needs to index, rank, and display rich results:

| What | Where | Why |
|------|-------|-----|
| **Page-specific `<title>` and meta description** | Every `<head>` | Search-result snippets |
| **Canonical URLs** | Every `<head>` | Prevents duplicate-content penalties |
| **Open Graph tags** (og:title, og:description, og:image, og:url) | Every `<head>` | Pretty link previews on LinkedIn / Facebook / WhatsApp / Slack |
| **Twitter Card tags** | Every `<head>` | Pretty previews on Twitter / X |
| **JSON-LD Organization schema** | Every `<head>` | Google Knowledge Panel eligibility (logo, address, phone) |
| **JSON-LD WebPage schema** | Every `<head>` | Helps Google understand the page structure |
| **`sitemap.xml`** | Root | Tells crawlers all your pages |
| **`robots.txt`** | Root | Tells crawlers what to index + points to sitemap |
| **`.nojekyll`** | Root | Stops GitHub from filtering files |
| **`manifest.json`** | Root | "Add to Home Screen" on Android/iOS |
| **`theme-color` meta** | Every `<head>` | Colors the mobile browser chrome |
| **Semantic HTML** (`<nav>`, `<main>`, `<footer>`, `<section>`) | All pages | Better crawler understanding |
| **Mobile responsive** | CSS | Google's mobile-first index rewards this |
| **`<meta name="robots" content="noindex">` on 404** | 404.html | 404 doesn't pollute search results |

### 🔧 Before Deploy: Update URLs

Three files contain `https://welttos.com` — change them to your actual deployed URL:

1. **`sitemap.xml`** — replace `https://welttos.com` in every `<loc>` tag
2. **`robots.txt`** — update the `Sitemap:` line at the bottom
3. **HTML pages (5×)** — find/replace `https://welttos.com` with your URL:
   - In `og:url`, `og:image`, `twitter:image`, `<link rel="canonical">`
   - In `<script type="application/ld+json">` blocks (Organization + WebPage schemas)

Quick find/replace command (Mac/Linux):
```bash
find . -type f \( -name "*.html" -o -name "*.xml" -o -name "*.txt" \) \
  -exec sed -i 's|https://welttos.com|https://YOUR-ACTUAL-URL|g' {} +
```

### 📈 After Deploy: Manual SEO Tasks

These you must do yourself (one-time, free):

1. **Google Search Console** → https://search.google.com/search-console
   - Add your property (verify via HTML tag or DNS)
   - Submit your sitemap: `https://yoursite.com/sitemap.xml`
   - Use "URL Inspection" to request indexing of each page

2. **Bing Webmaster Tools** → https://www.bing.com/webmasters
   - Same as above for Bing/Yahoo

3. **Google Business Profile** → https://www.google.com/business
   - Critical for local SEO ("AI company in Pune" searches)
   - Lets you appear in Google Maps

4. **Test your structured data**:
   - https://search.google.com/test/rich-results — paste your URL
   - Should detect "Organization" markup

5. **Test Open Graph previews**:
   - https://www.opengraph.xyz/ — paste your URL
   - Should show your logo + title + description

6. **PageSpeed Insights** → https://pagespeed.web.dev/
   - Aim for 90+ on mobile and desktop
   - This site should score well out of the box (static, minimal JS)

7. **Get backlinks**: list Welttos on Indian B2B directories (IndiaMART, JustDial), submit to AI tool directories (TheresAnAIForThat, Futurepedia), publish a launch post on LinkedIn.

### 📝 Ongoing SEO Improvements

Things to add over time:
- **Blog section** for SEO content (`/blog/voice-ai-for-indian-businesses.html`)
- **Case studies** with real client outcomes
- **FAQ schema** (we have a FAQ section — could add `FAQPage` JSON-LD to it for rich result eligibility)
- **Breadcrumbs** with `BreadcrumbList` schema
- **Per-product schema** (`SoftwareApplication` or `Service` JSON-LD) for each of the three products

---

## 📧 Contact Form

Form posts to **Formspree** via AJAX. On success, a custom modal pops up — no redirect to Formspree's default page.

To use your own Formspree endpoint, edit the `action` attribute in `contact.html`:
```html
<form id="contact-form" action="https://formspree.io/f/YOUR_ID" method="POST">
```

---

## 🎨 Theme System

- **Dark** (default) — cyan / violet / lime AI aesthetic
- **Light** — indigo / purple / green palette
- Toggled via the nav. Persists across pages via `localStorage`.

---

## 📱 Mobile / Responsive

- Hamburger menu → slide-in sidebar on mobile (≤900px)
- Sidebar auto-closes on link tap, backdrop click, Escape key, or resize to desktop
- All sections, grids, buttons, and forms reflow for phones
- Respects `prefers-reduced-motion`

---

## 🛠️ Tech Stack

- Pure HTML5 / CSS3 / Vanilla JS — no framework, no build tools
- Google Fonts (Space Grotesk + JetBrains Mono)
- Canvas API for the animated background
- CSS custom properties for theming
- IntersectionObserver for scroll animations
- Fetch API for AJAX form submission

---

## 🐛 Troubleshooting

| Issue | Fix |
|-------|-----|
| 404 on assets after deploy | Wait 1-2 min for CDN, hard-reload with `Ctrl+Shift+R` |
| Site shows old version | Empty commit + push: `git commit --allow-empty -m "rebuild" && git push` |
| Form submissions not arriving | Check Formspree form ID matches your dashboard; first submission needs email confirmation |
| Social preview shows wrong image | Use https://www.opengraph.xyz/ to debug; clear social-network cache with their respective debuggers (Facebook Sharing Debugger, LinkedIn Post Inspector) |
| Google not indexing | Submit sitemap via Search Console; allow 1-4 weeks for new sites |

---

## 📝 License

© Welttos. All rights reserved.
