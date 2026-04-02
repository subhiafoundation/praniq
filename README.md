# PraniQ Landing Website

Static landing page for **praniq.app**, hosted on GitHub Pages.

## Structure

```
landingweb/praniq/
  index.html
  privacy-policy.html
  terms-of-use.html
  robots.txt
  sitemap.xml
  CNAME           ← must contain: praniq.app (GitHub Pages custom domain)
  README.md
```

## Deploying to GitHub Pages

1. Create a **separate** GitHub repository (e.g. `praniq-landing` or use the org repo).
2. Copy the contents of this `landingweb/` folder into the root of that repo.
3. In the repo **Settings → Pages**, set source to `main` branch, `/ (root)`.
4. GitHub will publish the site at `https://<your-org>.github.io/<repo-name>`.

### Custom domain (praniq.app — apex)

1. Add a file called `CNAME` to the repo root containing exactly:
   ```
   praniq.app
   ```
2. In **Settings → Pages → Custom domain**, enter `praniq.app` and save (GitHub will commit the `CNAME` file if needed).
3. In your DNS provider, add **A records** for `@` (apex) pointing to GitHub Pages:
   - `185.199.108.153`
   - `185.199.109.153`
   - `185.199.110.153`
   - `185.199.111.153`
4. Optional: add a **`www`** subdomain — either a **CNAME** `www` → `<username>.github.io` (GitHub will serve the same site) or redirect `www` → `https://praniq.app` at your DNS.
5. Enable **Enforce HTTPS** in the Pages settings once DNS propagates.

## Updating store links

Replace the two placeholder `href="#"` download buttons in `index.html` with the live App Store and Play Store URLs once the app is published:

```html
<!-- iOS -->
<a href="https://apps.apple.com/app/praniq/idXXXXXXXXXX" ...>

<!-- Android -->
<a href="https://play.google.com/store/apps/details?id=com.praniqwellness.praniq" ...>
```

## SEO (Google Search Console)

If Search Console reports **“Page with redirect”** or **“Excluded by noindex”**:

1. **Canonical host** — This site uses **`https://praniq.app`** (apex) — see `link rel="canonical"`, `sitemap.xml`, and `robots.txt`. Ensure **`www.praniq.app` → 301 to `https://praniq.app`** if you still use the `www` hostname, so Google has one canonical URL.
2. **Add the sitemap** in Search Console: `https://praniq.app/sitemap.xml`
3. **Use a Domain property** in GSC for `praniq.app` (covers apex and `www`) or add URL-prefix properties for each URL you use.
4. **`noindex` in HTML** — These pages do **not** use `noindex`. If GSC still shows it, check your host/CDN for an **`X-Robots-Tag: noindex`** response header or a staging-only deployment.

Files: `robots.txt`, `sitemap.xml` at the site root next to `index.html`.

## Notes

- This folder is listed in `.gitignore` of the Flutter project — it will **not** be included in Flutter builds or the main app repository.
- No build tools, frameworks, or dependencies. Pure HTML/CSS/JS.
- Images are served from Unsplash CDN (free for commercial use under the Unsplash licence). Attribution is in the footer.
- Fonts are loaded from Google Fonts (Inter + Cormorant Garamond).
