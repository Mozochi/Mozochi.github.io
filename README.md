# Lewis Jones — Portfolio

Personal portfolio site at <https://lewisjones.dev>. Static, built with
[Astro](https://astro.build), no UI framework, three self-hosted fonts
(Space Grotesk, IBM Plex Sans, IBM Plex Mono) and one stylesheet.

## Local development

```bash
npm install
npm run dev        # dev server at http://localhost:4321
npm run build      # static build into dist/
npm run preview    # serve the production build locally
```

## Deploying to GitHub Pages

The repo ships with `.github/workflows/deploy.yml`, which builds the site and
publishes it to GitHub Pages on every push to `main` (no `gh-pages` branch
needed — it uses the official Pages deployment action).

1. Push this project to the repo `Mozochi/Mozochi.github.io`, branch `main`.
2. In the repo: **Settings → Pages → Build and deployment → Source: GitHub
   Actions**.
3. Push — the workflow builds and deploys.

### Custom domain (lewisjones.dev)

The build ships a `CNAME` file (from `public/CNAME`) and `astro.config.mjs`
sets `site: 'https://lewisjones.dev'`. To finish the domain setup, once:

1. At your DNS provider, point the apex `lewisjones.dev` at GitHub Pages with
   four A records: `185.199.108.153`, `185.199.109.153`, `185.199.110.153`,
   `185.199.111.153` (and optionally `AAAA` records:
   `2606:50c0:8000::153` … `8003::153`).
2. In the repo: **Settings → Pages → Custom domain → `lewisjones.dev`**, wait
   for the DNS check, then tick **Enforce HTTPS**.

`.dev` is on the HSTS preload list, so browsers will refuse plain HTTP for the
domain regardless — the Enforce HTTPS tick just makes GitHub redirect too.

## Security posture

This is a fully static site: no backend, no APIs, no forms, no cookies, no
analytics, no third-party scripts. There is nothing to rate-limit and no user
input to sanitise. What is in place:

- **Content-Security-Policy** (meta tag — GitHub Pages can't set response
  headers): everything locked to same-origin, `object-src 'none'`,
  `form-action 'none'`, `base-uri 'self'`. Inline scripts are allowed only
  because the pre-paint theme snippet needs it; no external script can load.
- **Referrer-Policy** `strict-origin-when-cross-origin`.
- **HTTPS enforced** via the `.dev` TLD's HSTS preload + GitHub Pages.
- **Dependencies**: four runtime packages, Dependabot watches npm and the
  GitHub Action weekly (`.github/dependabot.yml`).
- The deploy workflow runs with a read-only `contents` permission and only the
  Pages-deployment scopes it needs.
- The only client-side state is the theme choice in `localStorage`.

If you ever want real response headers (HSTS, X-Content-Type-Options,
frame-ancestors), put Cloudflare in front of Pages or move to a host that
supports a `_headers` file (Netlify, Cloudflare Pages).

