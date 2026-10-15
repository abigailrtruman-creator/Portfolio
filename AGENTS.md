# AGENTS.md

## Cursor Cloud specific instructions

This repository is a **single static website**: Abbie Truman's product design
portfolio. It is plain HTML/CSS/vanilla-JS with hashed assets under `assets/`,
deployed to Vercel (`vercel.json`). There is no build step, no package manager
manifest, no backend, and no database.

### Running locally

Serve the repo root with a static server that honors clean URLs, then open
`http://localhost:3000/`:

```
serve -l 3000 /workspace
```

- Internal links use **clean URLs** (e.g. `/sofa-to-saddle`, no `.html`),
  matching `"cleanUrls": true` in `vercel.json`. `serve` resolves these to the
  corresponding `.html` file, so navigation works. A bare
  `python3 -m http.server` will 404 on those in-site links unless you append
  `.html` manually, so prefer `serve`.
- Full visual fidelity needs outbound network: Google Fonts, GSAP/Lenis via
  jsDelivr CDN (case study pages), and a YouTube embed on `sofa-to-saddle`.
- `/_vercel/insights/script.js` (Vercel Web Analytics) 404s locally — expected.

### Lint / test / build

There is no lint step, no test suite, and no build step in this repo — Vercel
serves the files as-is. "Testing" means serving the site and browsing the pages
(`/`, `/boots-checkout`, `/sofa-to-saddle`, `/british-cycling`, `/api-portal`,
`/pwc-client-portal`).

### Gotchas

- `.gitignore` ignores `*.md` (drafts are kept locally and the public repo must
  not publish them at `/<name>.md`). `AGENTS.md` is explicitly re-included via
  `!AGENTS.md`; keep that exception if you add tracked docs.
- Asset authoring is done by local Python `build-*.py` scripts that are
  **gitignored** (`*.py`); they are not needed to run or view the site.
