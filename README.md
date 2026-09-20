# booqr-www

Static marketing site for booqr — a Hugo site deployed to GitHub Pages at
[www.booqr.dk](https://www.booqr.dk/).

Currently a single "under construction" front page.

## Commands

```bash
hugo server -D                           # dev, localhost:1313
hugo --gc --minify                       # build to public/
hugo --gc --minify --printPathWarnings   # must be warning-free before commit
```

Hugo 0.165+, **extended edition** (native WebP + inline CSS minify/fingerprint).
Plain CSS only — no SCSS/Dart Sass.

## Layout

| Path | What |
| --- | --- |
| `content/_index.md` | Front page copy and front matter |
| `layouts/` | Own templates — no external theme |
| `assets/css/main.css` | Design system, one file (inlined at build) |
| `static/CNAME` | Custom domain for GitHub Pages |

## Notes

- **Zero third-party requests.** System fonts, no CDN, no analytics.
  CSP is `default-src 'self'`; the stylesheet is inlined and its SHA-256 goes
  into `style-src`.
- `params.noindex` keeps the site out of search results while it is under
  construction — flip it to `false` in `hugo.toml` at launch.

## Deploy

Pushes to `main` build with Hugo and publish to GitHub Pages
(`.github/workflows/deploy.yml`). Pull requests run a warning-free build check
(`.github/workflows/build.yml`).
