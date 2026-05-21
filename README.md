# klaus-huerbl.de — Persona-Site

Static one-page authority site for the Klaus Hürbl persona. No build step,
plain HTML/CSS, all assets self-contained under `assets/`.

## Repository layout

```
.
├── index.html              # the whole site
├── 404.html
├── favicon.svg
├── robots.txt
├── sitemap.xml
├── netlify.toml            # only read by Netlify
├── _headers                # only read by Netlify
├── .nojekyll               # tells GitHub Pages not to run Jekyll
└── assets/
    ├── klaus-huerbl.webp   # headshot (900×1124)
    └── papers/
        ├── huerbl-probabilistische-modelle.pdf       # 7 pages
        ├── huerbl-markteffizienz-liniendynamik.pdf   # 12 pages
        └── huerbl-xg-vs-poisson.pdf                  # 26 pages
```

## Deploy

### A — GitHub Pages (zero config)

1. Create an empty public repo on GitHub (e.g. `klaus-huerbl-site`).
2. From the unzipped folder:
   ```sh
   git init -b main
   git add .
   git commit -m "initial site"
   git remote add origin git@github.com:USERNAME/klaus-huerbl-site.git
   git push -u origin main
   ```
3. In the repo's **Settings → Pages**:
   - Source: **Deploy from a branch**
   - Branch: **main** · **/(root)**
   - Save.
4. After ~30 s the site is live at `https://USERNAME.github.io/klaus-huerbl-site/`.
5. For a custom domain (`klaus-huerbl.de`):
   - Add a `CNAME` file at the repo root containing `klaus-huerbl.de`.
   - Point your DNS A-records to GitHub Pages
     (`185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`)
     or a `CNAME` to `USERNAME.github.io`.

### B — Netlify connected to the GitHub repo (recommended for custom domains)

1. Push the repo as above.
2. Netlify → **New site from Git** → pick the repo.
3. Build command: empty · Publish directory: `.` (already configured via `netlify.toml`).
4. Domain settings → Add `klaus-huerbl.de`, follow the DNS instructions.

Netlify auto-deploys every push to `main`. `netlify.toml` adds:
- 1-year immutable cache on `/assets/*`
- standard security headers (X-Frame-Options, X-Content-Type-Options, etc.)

### C — Drag-and-drop (one-off testing)

Open `https://app.netlify.com/drop` and drop this folder in. No git involved.

## Editing

The whole site is `index.html`. Common edits:
- **Headshot** → replace `assets/klaus-huerbl.webp` (keep 900×1124).
- **Add a paper** → drop the PDF into `assets/papers/` and add a `<li>` in
  the `#publikationen` section of `index.html`.
- **Bio copy** → edit the section text directly in `index.html`.
