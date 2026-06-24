# NotTyped — Website

The static marketing and legal site for [NotTyped](https://nottyped.com), a
handwriting-only social media app.

## Contents

| File | Purpose |
| --- | --- |
| `index.html` | Landing page (hero, app description, App Store badge, features) |
| `privacy.html` | Privacy Policy |
| `terms.html` | Terms of Service |
| `guidelines.html` | Community Guidelines |
| `support.html` | Support / Help (FAQ + contact) |
| `styles.css` | Shared stylesheet (palette, header, footer, type) |
| `assets/` | Brand images — `wordmark.png` (header/hero logo), `appicon.svg` + `appicon-180/1024.png` (hero icon, favicon, social card) |
| `CNAME` | Custom domain for GitHub Pages (`nottyped.com`) |

Pure HTML + CSS — no JavaScript, no build step, no frameworks. All links between
pages use **relative paths** (e.g. `href="privacy.html"`), so the site works both
at `username.github.io/<repo>/` during testing and at `nottyped.com` in production.

The wordmark and app icon are the official brand assets (`assets/`). Headings use
**Playfair Display** and body text uses **Hanken Grotesk**, loaded from Google Fonts
via `<link>` in each page's `<head>` — the only external dependency. If you'd rather
not depend on Google Fonts (e.g. for privacy), the fonts are SIL OFL licensed and can
be self-hosted; the page still renders with serif/sans fallbacks if the fonts fail to load.

## Before you publish

- Replace the App Store placeholder link `idXXXXXXXXXX` in `index.html` with the
  real App Store ID once the app is live.

## Deployment (GitHub Pages)

1. **Create a new GitHub repo** (e.g. `nottyped-site`).
2. **Push the contents of this `website/` folder to the `main` branch.** The HTML
   files must be at the repo root so GitHub Pages serves `index.html` as the home
   page.
3. In the repo, go to **Settings → Pages → Source: `main` branch** → **Save**.
4. **Custom domain:** in the same Pages settings, enter `nottyped.com` in the
   **Custom domain** field and save. (The included `CNAME` file sets this too.)
5. **DNS — A records:** in your DNS provider (Cloudflare), add four `A` records for
   the apex domain `nottyped.com` pointing to GitHub Pages:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
6. **DNS — CNAME record:** add a `CNAME` record for `www` pointing to
   `yourusername.github.io`.
7. Wait for DNS to propagate and for GitHub to provision the TLS certificate
   (enable **Enforce HTTPS** in Pages once it's available). The site will be live at
   **https://nottyped.com**.

> Note: if you serve the site from a project path like
> `username.github.io/nottyped-site/` for testing, the relative links still work —
> no changes needed.
