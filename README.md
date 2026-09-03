# spacea.ai — static mirror

Local static copy of [https://spacea.ai](https://spacea.ai), captured on 2026-09-03.

Site content, design, images and text are © SpaceA S.r.l. Società Benefit
(Via Giovanni Briosi 10, Milan, Italy). This repository is a local working copy.

## Pages

| Path | Source |
| --- | --- |
| `/` | `index.html` |
| `/contact-us/` | `contact-us/index.html` |
| `/servizi/` | `servizi/index.html` |
| `/progetti/` | `progetti/index.html` |

All assets (Astro CSS bundle, Montserrat font-faces CSS, logos, Unsplash imagery,
the Code of Ethics PDF, background video) are stored locally under `assets/` and
`_astro-1761032302980/`, with URLs in the HTML rewritten to point at them.
Hostinger analytics/cookie tracking and the Cloudflare email-obfuscation loader
were stripped; the two protected email links were decoded into plain `mailto:`
links.

## Run locally

```sh
python3 -m http.server 8000
# then open http://localhost:8000
```

Any static file server works; opening `index.html` directly via `file://` is not
recommended (absolute asset paths assume a server root).

## Known limitations

- The contact form renders but does not submit — on the live site it posts to
  Hostinger's backend, which a static copy cannot reproduce.
- Client-side behaviour that calls Hostinger/Cloudflare services (if any) is inert.

## Rebuilding the mirror

`_mirror_work/` (gitignored) holds the download/rewrite scripts used to produce
this copy; it is not part of the site itself.
