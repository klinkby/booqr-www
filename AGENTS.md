# AGENTS.md

Static marketing site for **booqr** — Hugo, deployed to GitHub Pages at
[www.booqr.dk](https://www.booqr.dk/). Danish (`da-dk`) content.

## Build

```bash
hugo server -D                                       # dev, localhost:1313
hugo --gc --minify                                   # build to public/
hugo --gc --minify --printPathWarnings --logLevel warn   # MUST be warning-free before commit
```

Hugo **extended** 0.165+. Own templates under `layouts/` — no external theme.

## House rules

- **Semantic HTML5.** Use `header`/`main`/`nav`/`section`/`article` for
  structure — never a `div` where an element with meaning exists. One `h1`
  per page; keep heading order intact.
- **Accessibility first.** Every page must work with a screen reader and the
  keyboard. Decorative emoji/icons get `aria-hidden="true"`; interactive and
  informative elements get accessible names. Don't rely on color alone.
- **Reduce scripting.** CSP is `script-src 'none'` — the site ships **zero
  JavaScript**. Solve layout and interaction with HTML + CSS. If JS ever
  becomes unavoidable, keep it minimal, progressively enhanced, and write
  **ES2022** (no transpiler/bundler in this repo).
- **No new abuse surface.** Zero third-party requests: self-hosted Nunito (`static/fonts/`, OFL), no CDN,
  no analytics, no external assets. `default-src 'self'`; the stylesheet is
  inlined and its SHA-256 pinned in `style-src`. Don't add network calls,
  trackers, or inline `<script>`.
- **Plain CSS only** in `assets/css/main.css` (one file, inlined at build) —
  no SCSS/Sass. Keep it lean; delete dead rules rather than leaving them.
- Markdown `unsafe = false` — raw HTML in content is off; use templates.

## Layout

| Path | What |
| --- | --- |
| `content/_index.md` | Front page copy + front matter |
| `content/problems/` | RFC 7807 error-type explanations (Danish) |
| `layouts/` | Own templates (`404.html` is the GitHub Pages 404); `partials/header.html` is the sticky site header + skip link, `partials/mailto.html` builds the invite mailto; `hero_highlight` front matter renders the gradient phrase of the h1 |
| `layouts/partials/icon.html` + `assets/icons/` | Inline Heroicons (outline, MIT, `LICENSE` alongside); front-matter `icon:` is the file name without `.svg` |
| `static/fonts/` | Self-hosted Nunito Variable (latin) + `OFL.txt` |
| `assets/css/main.css` | Design system, one file |
| `static/favicon.svg` | Logo/favicon — copy of booqr-app `src/lib/assets/favicon.svg` |
| `static/CNAME` | Custom domain for GitHub Pages |

## Deploy

Push to `main` → build + publish to GitHub Pages
(`.github/workflows/deploy.yml`). PRs run a warning-free build check
(`.github/workflows/build.yml`).
