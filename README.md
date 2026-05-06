# Scientist Homepage Template

A minimal, hybrid academic personal site

> Plain HTML5 + CSS3 + vanilla JS. **No build step.** Push to `<username>.github.io` and it's live.

## Features

- Hero with portrait + name + title + affiliation + 7 social icons (Email · Scholar · GitHub · ORCID · LinkedIn · X · Semantic Scholar)
- Sections: About · News · Selected Publications · Experience · Honors · Services · Contact
- **Auto-update from ORCID**: GitHub Actions cron + manual trigger pulls publications daily from your ORCID record. Extras (arXiv, code, project, slides, video) merged via `data/paper-extras.json`. See [CUSTOMIZE.md §17](./CUSTOMIZE.md).
- **Light + dark mode** with manual toggle (respects `prefers-color-scheme`, persisted to `localStorage`)
- **Year-filter pills** for publications
- **Brand-tinted badges**: arXiv · PDF · Code · Project · BibTeX · HuggingFace · Slides · Video
- Responsive (mobile / tablet / desktop)
- Accessibility: skip-link with focus-move, ARIA labels, keyboard-navigable, WCAG AA contrast (light + dark)
- SEO: Open Graph, canonical URL, sitemap, robots.txt
- Print stylesheet + reduced-motion support

## Quick Start

1. **Use this repo** as your `<username>.github.io` repository (or fork / template).
2. **Edit `index.html`** — every section has a `<!-- ✏️ EDIT: ... -->` comment guiding you.
3. **Replace `assets/img/avatar.svg`** with your portrait (square, ≥360×360, JPG/PNG/SVG).
4. **Push to `main`** — GitHub Pages serves the root.

```bash
git add .
git commit -m "feat: customize scientist homepage"
git push origin main
```

Then in your repo: **Settings → Pages → Source: `main` / root**.

Site goes live at `https://<username>.github.io/` within a minute.

## File Layout

```
.
├── index.html                 # Homepage — edit this
├── 404.html                   # Custom not-found page
├── assets/
│   ├── css/style.css          # All styles (CSS variables for theming)
│   ├── js/script.js           # Theme toggle, scroll-spy, year-filter
│   └── img/                   # Avatar, pub thumbnails, favicon, OG image
├── .nojekyll                  # Skip GitHub's default Jekyll processing
├── sitemap.xml                # SEO sitemap
├── robots.txt                 # Crawler rules
├── CUSTOMIZE.md               # Step-by-step editing guide
├── docs/
│   ├── design-guidelines.md   # Design system (typography, colors, components)
│   └── wireframe/             # Original approved wireframe (reference copy)
├── plans/                     # Implementation plans
└── README.boilerplate.md      # Original ClaudeKit boilerplate readme (kept as ref)
```

## Customization

See **[CUSTOMIZE.md](./CUSTOMIZE.md)** for a section-by-section walkthrough — name, photo, social links, news, publications, experience, honors, services, custom domain, accent color, fonts.

## Custom Domain (optional)

If you have your own domain (e.g. `you.dev`):

1. Add a file named `CNAME` at the root containing `you.dev` (no protocol, no slash).
2. In your DNS, add a `CNAME` record pointing `you.dev` → `<username>.github.io`.
3. **Settings → Pages → Custom domain** → enter `you.dev`, enable HTTPS.

## Browser Support

Modern evergreen browsers (Chrome, Firefox, Safari, Edge — last 2 versions). Falls back gracefully on older browsers — `localStorage`-blocked theme picks via media query.

## Credits

- Design hybrid: [yuanxzhang.github.io](https://yuanxzhang.github.io/) (text-first restraint) + [zwq2018.github.io](https://zwq2018.github.io/) (hero + badge cards).
- Fonts: [Newsreader](https://fonts.google.com/specimen/Newsreader) + [Inter](https://fonts.google.com/specimen/Inter) via Google Fonts.

## License

MIT — see [LICENSE](./LICENSE). You may use, modify, and redistribute freely.
