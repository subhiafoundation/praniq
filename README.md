# PraniQ Landing Website

Static landing page for **www.praniq.app**, hosted on GitHub Pages.

## Structure

```
landingweb/
  index.html    ← single-file page (HTML + CSS + JS, no build step)
  README.md     ← this file
```

## Deploying to GitHub Pages

1. Create a **separate** GitHub repository (e.g. `praniq-landing` or use the org repo).
2. Copy the contents of this `landingweb/` folder into the root of that repo.
3. In the repo **Settings → Pages**, set source to `main` branch, `/ (root)`.
4. GitHub will publish the site at `https://<your-org>.github.io/<repo-name>`.

### Custom domain (www.praniq.app)

1. Add a file called `CNAME` to the repo root containing exactly:
   ```
   www.praniq.app
   ```
2. In your DNS provider, add:
   - A record: `@` → `185.199.108.153` (and .109, .110, .111)
   - CNAME: `www` → `<your-org>.github.io`
3. Enable **Enforce HTTPS** in the Pages settings once DNS propagates.

## Updating store links

Replace the two placeholder `href="#"` download buttons in `index.html` with the live App Store and Play Store URLs once the app is published:

```html
<!-- iOS -->
<a href="https://apps.apple.com/app/praniq/idXXXXXXXXXX" ...>

<!-- Android -->
<a href="https://play.google.com/store/apps/details?id=com.praniqwellness.praniq" ...>
```

## Notes

- This folder is listed in `.gitignore` of the Flutter project — it will **not** be included in Flutter builds or the main app repository.
- No build tools, frameworks, or dependencies. Pure HTML/CSS/JS.
- Images are served from Unsplash CDN (free for commercial use under the Unsplash licence). Attribution is in the footer.
- Fonts are loaded from Google Fonts (Inter + Cormorant Garamond).
