# Kyzenz Site Optimisations

A step-by-step reference of all optimisations and improvements made to the site.

---

## 1. Image Compression
- Compressed all screen images in `moneybosshome/screens/` from 2.2 MB to under 650 KB (~70% reduction)
- Original uncompressed images kept in `moneybosshome/screens OG/` for future reference
- Smaller images = faster page load and less data usage for visitors

---

## 2. Favicons
- Added `kz-icon.png` as the favicon for all pages
- Added `mb-icon.png` as the og:image for MoneyBoss Home pages
- Added `<link rel="icon">` and `<link rel="apple-touch-icon">` to all HTML pages:
  - `index.html` → `kz-icon.png`
  - `moneybosshome/mbh.html` → `kz-icon.png`
  - `moneybosshome/privacy.html` → `kz-icon.png`
  - `moneybosshome/help.html` → `kz-icon.png`
  - `404.html` → `kz-icon.png`
- Icon files renamed without spaces for server compatibility:
  - `KZ icon.png` → `kz-icon.png`
  - `MB icon.png` → `mb-icon.png`

---

## 3. Open Graph (og:image)
- Added `og:image` meta tag to all pages so links show a preview image when shared on WhatsApp, Twitter/X, LinkedIn etc.
  - `index.html` → `kz-icon.png`
  - `mbh.html` → `mb-icon.png`
  - `privacy.html` → `mb-icon.png`
  - `help.html` → `mb-icon.png`
- Added full og: meta tags (title, description, type, url, image) to `privacy.html` and `help.html`

---

## 4. Google Analytics
- Created a Google Analytics 4 property for `kyzenz.com`
- Measurement ID: `G-DRWL74TMQK`
- Added gtag.js tracking code to:
  - `index.html`
  - `moneybosshome/mbh.html`
  - `moneybosshome/privacy.html`
  - `moneybosshome/help.html`
  - `404.html`
- Note: Keep the gtag.js code on all pages — removing it will break Google Search Console verification

---

## 5. Google Search Console
- Verified ownership of `kyzenz.com` automatically via Google Analytics tag
- Submit sitemap at: Search Console → Sitemaps → enter `sitemap.xml` → Submit

---

## 6. sitemap.xml
- Created `sitemap.xml` at the root of the site
- Lists all pages with priority and change frequency:
  - `kyzenz.com/` — priority 1.0
  - `kyzenz.com/moneybosshome/mbh.html` — priority 0.9
  - `kyzenz.com/moneybosshome/help.html` — priority 0.7
  - `kyzenz.com/moneybosshome/privacy.html` — priority 0.5
- Update this file whenever new pages are added

---

## 7. robots.txt
- Created `robots.txt` at the root of the site
- Allows all crawlers to index everything
- Points crawlers to `sitemap.xml` automatically

---

## 8. 404 Page
- Created custom `404.html` matching the site's dark theme
- Shows a friendly message and a link back to the homepage
- Includes Google Analytics and favicon
- GitHub Pages automatically serves this for any invalid URL

---

## 9. Explore Button (index.html)
- Added "Explore MoneyBoss Home" button in the hero section
- Styled to match the site's teal pill design
- Animated with a border shimmer at 3s speed
- Points to `moneybosshome/mbh.html`
- Removed redundant "MoneyBoss Home" nav link after button was added

---

## 10. Version Number (mbh.html)
- Added "Latest Version v1.0.0" below the store badges
- Update this whenever a new app version is released

---

## 11. og:image — MoneyBoss Home
- Updated `mbh.html` og:image to use `screens/feature.png` (Play Store feature graphic, 1024×500)
- Shows a proper app preview banner when the link is shared on WhatsApp or LinkedIn

## 12. CLAUDE.md
- Created `CLAUDE.md` at the repo root for future Claude Code sessions
- Documents project structure, deployment, architecture, conventions, analytics, and app details

## 13. KZ Logo in Nav (index.html)
- Replaced plain "Kyzenz" text in nav with KZ icon + "Kyzenz" text side by side
- Logo links back to homepage
- Icon: `kz-icon.png` at 32×32px with rounded corners

## 14. KZ Logo in Back Link (mbh.html)
- Updated `← Kyzenz` back link to show KZ icon + "Kyzenz" text for consistency with index.html nav
- Icon: `../kz-icon.png` at 24×24px

## 15. og:image Banners
- `index.html` — uses `feature.png` (Kyzenz homepage banner)
- `mbh.html` — uses `screens/feature.png` (MoneyBoss Home Play Store feature graphic)

## Future Improvements
- Consider WebP format for screen images (30-50% smaller than PNG)
- Add lazy loading (`loading="lazy"`) to feature screen images for faster initial load
- Update version number in mbh.html hero on each app release
