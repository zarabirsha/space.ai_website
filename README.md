# SpaceA website

Clean single-page rebuild of [spacea.ai](https://spacea.ai) — one readable
HTML document plus an external stylesheet and local assets. Works when served
over HTTP **and** when `index.html` is opened directly from the Finder
(e.g. in Safari) — every reference is relative and nothing is fetched from
the network.

Site content, design, imagery and text are © SpaceA S.r.l. Società Benefit
(Via Giovanni Briosi 10, Milan, Italy).

## Structure

```
index.html   the whole site: header, five routed sections, footer, router
style.css    design system (fonts, tokens, layout, animations) — preloaded
assets/
  fonts/     Schnyder Cond M Light, Neue Helvetica BQ, Montserrat (woff2)
  logo/      SpaceA logo (PNG)
  …pdf       Codice Etico (downloaded from the Code of Ethics page)
```

## Pages (hash routes)

| Route | Content |
| --- | --- |
| `#/home` | Hero — ART, ARCHITECTURE, AI / MULTIDISCIPLINARY OFFICE BASED IN MILAN |
| `#/servizi` | Servizi Creativi Innovativi — three service cards + CTA |
| `#/progetti` | Privacy Policy |
| `#/contact-us` | Contact form (Name, Email, Message) + address |
| `#/code-of-ethics` | Codice Etico blurb + PDF download button |

The router is ~40 lines of vanilla JS: it toggles sections, sets the active
nav item and `document.title`, and re-triggers the slide-in reveals
(`IntersectionObserver`).

## Design notes

The look replicates the live site: the `#FFF035` yellow field, Schnyder Cond
display headings, Montserrat UI text, black pill buttons (hover `#2D236D`),
sticky header, hairline-on-scroll, staggered slide-up reveals, and the
920px responsive breakpoint. The stylesheet is preloaded via
`<link rel="preload" …>` together with the first-screen fonts and hero image.

## Run locally

Any static server, or just open `index.html` in a browser:

```sh
python3 -m http.server 8000   # http://localhost:8000
open index.html               # file:// — works too
```

## Notes

- The contact form renders but does not submit (no backend in a static copy).
- `_mirror_work/` (gitignored) holds the scripts that produced the original
  scrape and rebuilds; it is not part of the site.
