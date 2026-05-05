# Talos Landing

Owner: John Berry (john@talosops.ai) · Houston, TX
Repository: `Talos-Ops1/talos-landing` (public)
Production: `talosops.ai`

Static HTML/CSS/JS marketing site. No build step. Deployed on Vercel. Inherited from Horizon AI structure with mechanical rebrand pass; visual restyle (orange/cream → bronze/obsidian) deferred pending scope confirmation.

---

## Quick start

```bash
npx serve . -l 8080 --no-clipboard    # dev preview at localhost:8080
```

Deploy is git-driven — push to `main` and Vercel auto-deploys.

---

## File layout

```
talos-landing/
├── index.html              # main page (homepage)
├── index-v1.html           # backup of older homepage version
├── faq.html                # FAQ
├── solutions.html          # solutions catalog (15 featured + 28 listed industries)
├── blog/
│   ├── index.html          # blog landing
│   ├── TEMPLATE.html       # canonical blog post template — use for new posts
│   └── *.html              # 5 articles (SMB-toned; rewrite per Spec R3)
├── vercel.json             # rewrites + security headers (CSP, HSTS, X-Frame, etc.)
├── sitemap.xml, robots.txt, site.webmanifest
└── favicons + og-image     # currently still Horizon orange — regen pending
```

---

## Required mobile patterns

Every page MUST be mobile-optimized. No exceptions. The canonical patterns (reference `index.html` or `blog/TEMPLATE.html`):

- `overflow-x: hidden` on `html` and `body`
- Hamburger menu (`.mobile-toggle`) — hidden on desktop, visible on mobile
- Nav links hidden by default on mobile, shown as column dropdown via `.nav-links.open`
- Logo tagline hidden on mobile
- `env(safe-area-inset-top)` padding on `nav` for iPhone notch / Dynamic Island
- Tables scrollable on mobile: `display:block; overflow-x:auto; -webkit-overflow-scrolling:touch`
- Reduced font sizes and padding at `max-width:768px`

---

## Conventions

- **File safety on major changes:** create a `-v2` suffix file (`index-v2.html`) for review before replacing the original. Keep backups.
- **Contact form:** POSTs to `https://portal.talosops.ai/api/contact` — handled by [`Talos-Ops1/talos-portal`](https://github.com/Talos-Ops1/talos-portal). Includes honeypot spam protection and `<noscript>` fallback.
- **vercel.json security headers** are non-negotiable: CSP, HSTS, X-Frame-Options DENY, Referrer-Policy, Permissions-Policy, X-Content-Type-Options. Don't remove them when editing other rewrites.
- **CSP `connect-src`** allows `https://portal.talosops.ai` (the portal API) and `https://www.google-analytics.com`. Update if adding new external endpoints.

---

## Current rebrand status

| Layer | State |
|---|---|
| File structure (multi-page Horizon layout) | ✅ Preserved |
| Brand identity (colors, fonts, logos) | ❌ Still Horizon orange — restyle pending |
| Copy / voice (SMB tone, $299 anchor) | ❌ Still Horizon — Spec R3 rewrite pending |
| SEO/meta (canonical URLs, geo tags) | ✅ Updated to `talosops.ai`, Houston TX |
| Tracking (GA4) | ❌ Garrett's GA ID removed; Talos GA4 not yet set up |
| Favicon set | ❌ Horizon orange variants still in repo — regen pending |
| Vercel deployment | ✅ Live at `talosops.ai` |

The visual restyle (Path B in our planning conversations) is the next major work item: keep the multi-page structure, swap the CSS variable palette + fonts + logos, leave content for R3.

---

## Voice + brand (target state)

- Audience: $5M–$5B mid-market and enterprise CEOs/CFOs
- Brand colors: `#c9956b` bronze, `#0a0c10` obsidian, `#f0ede8` cream, `#5b8c7e` patina
- Fonts: Cormorant Garamond (serif headings, italic emphasis), Sora (body)
- Brand reference: `Talos-Ops1/talos-ops-docs/Brand/` (logos, email signature, favicon source)

---

## SEO infrastructure (already updated)

- `sitemap.xml` — currently lists homepage only on `talosops.ai`. Re-expand when Spec R3 ships new content pages.
- `robots.txt` — points at `talosops.ai/sitemap.xml`
- `site.webmanifest` — Talos Ops, theme color `#0a0c10`
- JSON-LD structured data — to be added when content rebrand happens

---

## Related repositories

| Repo | Purpose |
|---|---|
| [`Talos-Ops1/talos-portal`](https://github.com/Talos-Ops1/talos-portal) | Admin + client portal at `portal.talosops.ai`. Receives contact form submissions from this site. |
| [`Talos-Ops1/talos-ops-docs`](https://github.com/Talos-Ops1/talos-ops-docs) | Brand assets (`Brand/` folder has the canonical Talos logos + favicon source). |
