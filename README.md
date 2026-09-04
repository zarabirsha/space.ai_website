# spacea.ai — static mirror

Local static copy of [https://spacea.ai](https://spacea.ai), captured on 2026-09-03,
ready to deploy on **GitHub Pages** (project site, user site, or custom domain —
all links and assets are page-relative, and `.nojekyll` is included so the
`_astro-*` folder is served).

Site content, design, images and text are © SpaceA S.r.l. Società Benefit
(Via Giovanni Briosi 10, Milan, Italy). This repository is a local working copy.

## Pages

Two builds of the same site live in this repo:

- **`spacea.html`** — the whole site as **one HTML document** (plus the
  `assets/` and `_astro-1761032302980/` folders next to it). All five pages are
  embedded as sections and a small hash router switches between them
  (`#/home`, `#/code-of-ethics`, `#/contact-us`, `#/servizi`, `#/progetti`),
  with the correct nav item highlighted per page. No hydration JavaScript runs.
- The multi-page build — one directory per page, used by the GitHub Pages
  deployment (Jekyll-free via `.nojekyll`, relative paths, deploy workflow):

| Path | Source |
| --- | --- |
| `/` | `index.html` |
| `/contact-us/` | `contact-us/index.html` |
| `/servizi/` | `servizi/index.html` |
| `/progetti/` | `progetti/index.html` |
| `/code-of-ethics/` | `code-of-ethics/index.html` (added to the mirror: heading, blurb and a download button for the PDF) |

All assets (CSS/JS bundles, fonts, logos, Unsplash imagery, the Code of Ethics
PDF) are stored locally and referenced with relative paths. Hostinger
analytics/cookie tracking and the Cloudflare email-obfuscation loader were
stripped; protected email links were decoded into plain `mailto:`; the site's
canonical-domain redirect (which bounced the local copy to spacea.ai) is
disabled.

## Deploy on GitHub Pages

1. Create a GitHub repository and push this folder:
   ```sh
   git remote add origin git@github.com:<you>/<repo>.git
   git push -u origin main
   ```
2. In the repo: **Settings → Pages → Build and deployment → Source: GitHub Actions**.
3. The included workflow (`.github/workflows/deploy.yml`) publishes the site on
   every push to `main`. The site works at `https://<you>.github.io/<repo>/`
   thanks to the relative paths (and equally at a user root site or with a
   custom domain).

Alternative without Actions: set **Source: Deploy from a branch**, branch
`main`, folder `/ (root)` — `.nojekyll` ensures underscore-prefixed asset
folders are served.

## Run locally

```sh
python3 -m http.server 8000
# open http://localhost:8000
```

Any static file server works; opening `index.html` via `file://` is not
recommended (the hydrated app expects HTTP).

## Known limitations

- The contact form renders but does not submit — on the live site it posts to
  Hostinger's backend, which a static copy cannot reproduce.
- The `Code of Ethics` nav item opens the local `/code-of-ethics/` page added
  by this mirror (the live site links the PDF directly).

## Rebuilding the mirror

`_mirror_work/` (gitignored) holds the scripts used to produce and adapt this
copy (download, URL rewriting, Code of Ethics page generation, GitHub Pages
path conversion); it is not part of the site itself.
