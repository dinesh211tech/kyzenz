# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static website for **Kyzenz** — a company that builds private, offline-first apps. The site is hosted on GitHub Pages at `kyzenz.com` with a custom domain via Namecheap DNS.

Currently contains one app: **MoneyBoss Home** — a private expense tracker available on Android (iOS coming soon).

## Repository Structure

```
/                          # kyzenz.com root
  index.html               # Kyzenz homepage
  404.html                 # Custom error page
  sitemap.xml              # For Google Search Console
  robots.txt               # Allows all crawlers
  kz-icon.png              # Kyzenz favicon (used on all pages)
  CNAME                    # GitHub Pages custom domain: kyzenz.com

moneybosshome/             # kyzenz.com/moneybosshome/
  mbh.html                 # Main MoneyBoss Home landing page
  privacy.html             # Privacy policy
  help.html                # FAQ / Help page
  mb-icon.png              # MoneyBoss Home icon (og:image only)
  screens/                 # Compressed app screenshots (used in mbh.html)
  screens OG/              # Original uncompressed screenshots (not referenced in HTML)

promo/                     # kyzenz.com/promo/ — feeds MoneyBoss Home's in-app
                            # cross-promo banner (see D:\Project\Code\moneybosshome,
                            # lib/config/promo_config.dart + lib/ui/core/widgets/promo_banner.dart)
  mbh-topbar.json           # Manifest MBH fetches at runtime: list of
                             # {lightImageUrl, darkImageUrl, tapUrl}, cycled in
                             # array order. Edit this (and/or add icon PNGs
                             # here) to change what MBH promotes — no app
                             # update needed. MBH caches it 24h.
  mbh-icon-light.png        # MBH icon, light/dark pair — copied from
  mbh-icon-dark.png         # moneybosshome/assets/icons/logo black|white.png
  mbd-icon-light.png        # MoneyBoss Drive icon, light/dark pair — copied
  mbd-icon-dark.png         # from moneybossdrive/assets/icons/logo black|white.png
  kz-icon.png               # Kyzenz mark — background-free, so one file
                             # covers both the light and dark theme slots
```

## Deployment

- Push to `main` branch on GitHub → auto-deploys via GitHub Pages
- No build step — pure HTML/CSS/JS, no frameworks or dependencies
- Changes live within 1-2 minutes of push

```bash
git add .
git commit -m "description"
git push origin main
```

## Architecture

Each page is a self-contained HTML file with inline `<style>` — no external CSS files or JS frameworks. JavaScript is also inline at the bottom of each file.

**mbh.html** is the most complex page:
- Sticky nav with scroll-based active tab detection
- Features section with IntersectionObserver — scrolling through feature items swaps the sticky phone mockup image on the right
- Comparison table (Free vs Pro)
- All styles and scripts are inline in the single file

## Conventions

- All pages share the same dark theme (`#0a0a0a` background, `#2dd4bf` teal accent)
- CSS variables are defined in `:root` at the top of each `<style>` block
- Font: Inter (loaded from Google Fonts)
- Icons: Material Symbols Outlined (only in mbh.html)
- File names: use kebab-case with no spaces (e.g. `kz-icon.png` not `KZ icon.png`)

## Analytics & SEO

- Google Analytics 4: Measurement ID `G-DRWL74TMQK` — tag must remain on all pages or Search Console verification breaks
- Google Search Console: verified via GA tag — submit `sitemap.xml` after adding new pages
- og:image for mbh.html uses `screens/feature.png` (1024×500 Play Store feature graphic)
- og:image for index.html uses `kz-icon.png`

## App Details

- **Package ID**: `com.kyzenz.moneybosshome`
- **Play Store URL**: `https://play.google.com/store/apps/details?id=com.kyzenz.moneybosshome`
- **iOS**: Coming soon (App Store badge shown with "coming soon" tooltip)
- **Current version**: v1.0.0 (update in mbh.html hero section when releasing)
- **Pro subscription**: handled via Google Play, App Store, and RevenueCat
