# Customization Guide

A walkthrough of every editable section. Open `index.html` and search for `✏️ EDIT` to find the exact spots.

## 1. Page metadata (`<head>`)

Find the `<head>` block at the top of `index.html`:

| What to change | Where |
|---|---|
| Browser tab title + Google search title | `<title>` |
| Meta description (search snippet, social card) | `<meta name="description">` |
| Author name | `<meta name="author">` |
| Canonical URL (your live URL) | `<link rel="canonical" href="...">` |
| Social card title / description | `og:title`, `og:description`, `og:url` |

Replace every occurrence of `Jane Doe` with your name and `jane.doe.github.io` with your real URL.

## 2. Avatar / portrait

Replace `assets/img/avatar.svg` with your photo:

- Recommended: square, ≥360×360 px, JPG / PNG / SVG
- File path stays the same so HTML works without changes — or update the `src` in `index.html` if you rename
- For retina displays, supply a 2× version and use `srcset` (optional)

## 3. Hero (name, title, affiliation, bio)

In `index.html`, find:

```html
<h1 class="hero-name">Jane Doe</h1>
<p class="hero-title">PhD Candidate · Computer Science</p>
<p class="hero-affiliation">Stanford University, USA</p>
<p class="hero-bio">…</p>
```

Plain text edits. Bio: 2-3 sentences max.

## 4. Brand initials (top-left "JD")

```html
<a href="#top" class="nav-brand" aria-label="Home">JD</a>
```

Two letters works best.

## 5. Social links

Each `<li>` in `<ul class="social-row">` is one icon. Edit the `href`:

| Platform | Example href |
|---|---|
| Email | `mailto:you@uni.edu` |
| Google Scholar | `https://scholar.google.com/citations?user=YOUR_ID` |
| GitHub | `https://github.com/YOUR_USER` |
| ORCID | `https://orcid.org/0000-0000-0000-0000` |
| LinkedIn | `https://linkedin.com/in/YOUR_USER` |
| X (Twitter) | `https://x.com/YOUR_USER` |
| Semantic Scholar | `https://www.semanticscholar.org/author/YOUR_ID` |

To **remove** a platform: delete its entire `<li>...</li>`. To **add** one (e.g. Bluesky, Mastodon, YouTube): copy an existing `<li>` and replace the `<svg>` with the new icon (grab from [simpleicons.org](https://simpleicons.org/)).

## 6. About paragraphs

Plain `<p>` tags inside `#about`. Use `<strong>` for emphasis. Keep it 2-3 paragraphs. Keywords list at the end is optional.

## 7. News

Each item:

```html
<li><span class="news-date">[Apr 2026]</span><span>Your news here. <a href="#">link</a></span></li>
```

Newest first. Show ~6, link to a longer page if you want.

### Placeholder links (`href="#"`)

Many template links — news items, paper badges, mailing list — use `href="#"` as a placeholder. Replace each with a real URL when you fill in your content. (Until then, clicking them scrolls back to the top — that's the browser's default for empty fragments, not a bug.)

## 8. Publications

Each paper is one `<article class="pub" data-year="YYYY">`. To add a new paper, copy an existing block.

### Paper structure

```html
<article class="pub" data-year="2026">
  <img class="pub-thumb" src="assets/img/pub-thumb-NN.svg" alt="..."/>
  <div class="pub-body">
    <span class="pub-badge-flag">Spotlight</span>     <!-- optional -->
    <h4 class="pub-title">Paper title</h4>
    <p class="pub-authors"><strong>You</strong>*, Co-author, Advisor ✉</p>
    <p class="pub-venue"><em>Venue</em>, Year</p>
    <ul class="badge-row" aria-label="Paper links">
      <li><a class="badge badge-arxiv" href="...">arXiv</a></li>
      <li><a class="badge badge-pdf" href="...">PDF</a></li>
      <li><a class="badge badge-code" href="...">Code</a></li>
      <li><a class="badge badge-bibtex" href="...">BibTeX</a></li>
    </ul>
  </div>
</article>
```

### Author conventions

- `<strong>You</strong>` — bold yourself
- `*` after a name — equal contribution
- `✉` after a name — corresponding author

### Available badge classes

| Class | Brand color |
|---|---|
| `badge-arxiv` | arXiv red `#b31b1b` |
| `badge-pdf` | gray `#5a6068` |
| `badge-code` | GitHub black `#24292f` |
| `badge-project` | accent blue `#1e4ba0` |
| `badge-hf` | HuggingFace yellow `#FFD21E` |
| `badge-bibtex` | tan `#7a6a3f` |
| `badge-slides` | green `#0d8f6c` |
| `badge-video` | magenta `#a13a8e` |

### Year filter

Two coupled changes per year:

1. Add a button to `<div class="pub-filter">`:
   ```html
   <button class="pub-filter-btn" type="button" data-year="2027" aria-pressed="false">2027</button>
   ```
2. Add a year heading above that year's papers — **must include `data-year`**:
   ```html
   <h3 class="pub-year" data-year="2027">2027</h3>
   ```

The JS auto-wires both. Each `<article class="pub" data-year="YYYY">` must match a button.

### Paper thumbnails

Either reuse `assets/img/pub-thumb-01.svg`–`04.svg`, or drop your own image (PNG / SVG) into `assets/img/` and update the `src`. Recommended aspect ratio: 16:10 (320×200).

## 9. Experience timeline

Each `<li class="timeline-item">` = one role. Most recent first. Keep `role / org / location / date range`.

## 10. Honors & Awards

Simple bullet list. `[year][award]`.

## 11. Academic Services

Three sub-sections (Conference Reviewing, Journal Reviewing, Organization). Add / remove `<ul class="bullet-list">` as you like.

## 12. Contact

Email, office address, mailing list. Drop the mailing list `<li>` if you don't have one.

## 13. Footer

- "Last updated" — change manually when you push edits
- Visitor counter — paste a [clustrmaps](https://clustrmaps.com/) or [revolvermaps](https://revolvermaps.com/) embed where the placeholder span is, or delete the whole `<div id="visitor-counter">`

## 14. Theme — colors & fonts

### Change the accent color

In `assets/css/style.css`, find `:root` (light theme) and `[data-theme="dark"]`:

```css
:root {
  --accent:        #1e4ba0;   /* deep blue */
  --accent-hover:  #173a80;
}
```

Pick from common alternatives:

| Style | Light `--accent` | Dark `--accent` |
|---|---|---|
| Deep blue (default) | `#1e4ba0` | `#6ea3e8` |
| Forest green | `#1b5e3f` | `#5dbb8c` |
| Terracotta | `#a14a2c` | `#e08767` |
| Royal purple | `#4c2a85` | `#a884d5` |
| Charcoal | `#2c3038` | `#a7afbd` |

Update `--accent`, `--accent-hover`, and the `badge-project` color (in `style.css`) plus `assets/img/favicon.svg` for visual consistency.

### Change the fonts

The `<link>` to Google Fonts in `index.html` (and in `404.html`) controls the font families. To swap:

1. Pick a pair from [Google Fonts](https://fonts.google.com/) (one serif heading + one sans body).
2. Replace the `href=...fonts.googleapis.com/css2?family=...` URL.
3. In `assets/css/style.css`, find `--font-serif` and `--font-sans` and update the `font-family` values.

Pairs to try: Newsreader + Inter (default) · Lora + Source Sans 3 · EB Garamond + Plus Jakarta Sans · Crimson Pro + IBM Plex Sans.

## 15. Custom domain

See README **Custom Domain** section.

## 16. Updating the SEO files

When you go live, update three URLs:

- `index.html` — `og:url`, canonical
- `sitemap.xml` — `<loc>`
- `robots.txt` — `Sitemap:`

A simple find/replace of `jane.doe.github.io` → your real domain handles all three.

## 17. Auto-update from ORCID

The Publications section between `<!-- ORCID:PUBS:START -->` and `<!-- ORCID:PUBS:END -->` markers in `index.html` is **auto-managed** by `scripts/hydrate-from-orcid.mjs`. A daily GitHub Actions cron + a manual "Run workflow" button regenerate it from your ORCID record.

### One-time setup

1. Edit `data/orcid-config.json` — set your ORCID + name variants (the script bolds matching names in author lists):
   ```json
   {
     "orcid": "0000-0002-5945-3712",
     "name_pattern": ["Your Name", "Y. Name", "Name, Y."]
   }
   ```
2. Make sure your ORCID profile visibility = **Everyone** (Settings on orcid.org).
3. After pushing to GitHub: **Repo Settings → Actions → General → Workflow permissions → "Read and write permissions"** (so the bot can commit back).

### Adding extras (arXiv, code, project, slides, video, BibTeX, HuggingFace)

ORCID does not store these. Add them in `data/paper-extras.json`, keyed by DOI:

```json
{
  "10.1016/j.eswa.2026.132546": {
    "arxiv":   "https://arxiv.org/abs/2401.12345",
    "code":    "https://github.com/youruser/repo",
    "project": "https://yourproject.dev",
    "slides":  "https://...slides.pdf",
    "video":   "https://youtu.be/...",
    "bibtex":  "https://.../paper.bib",
    "hf":      "https://huggingface.co/datasets/...",
    "thumb":   "assets/img/pub-mypaper.png",
    "flag":    "Best Paper"
  }
}
```

Any field is optional. Push the JSON change → next workflow run merges it.

### Manual trigger

GitHub repo → **Actions** tab → **"Hydrate from ORCID"** → **Run workflow** button. Useful right after you push a paper to ORCID.

### Local re-run

```bash
node scripts/hydrate-from-orcid.mjs            # update index.html in place
node scripts/hydrate-from-orcid.mjs --dry-run  # print HTML to stdout, do not modify
```

Requires Node 20+ (built-in fetch). No `npm install` needed.

### Disabling auto-update

- Delete `.github/workflows/hydrate-orcid.yml` to stop the cron.
- Optionally remove the `<!-- ORCID:PUBS:* -->` markers in `index.html` if you want to fully manage publications by hand.

### Troubleshooting

| Symptom | Cause | Fix |
|---|---|---|
| Author not bolded | `name_pattern` doesn't include that variant | Add a variant to the array in `orcid-config.json` |
| 0 works fetched | ORCID profile not public | orcid.org → Settings → set visibility to Everyone |
| Workflow fails on push | Repo workflow permissions read-only | Settings → Actions → "Read and write permissions" |
| Cron stopped firing | 60-day inactivity (rare with daily commits) | Click "Run workflow" once to revive |
| Extras DOI not matching | DOI typo or different case | Script logs `extras-matched=N/M`; check the count |

## 18. Removing sections you don't need

- Don't have a mailing list? Delete that `<li>` in `#contact`.
- No services to list? Delete `<section id="services">` and its nav link.
- No honors yet? Same pattern.

The site degrades gracefully — sections are independent.

## Troubleshooting

- **Fonts look wrong** — check the Google Fonts `<link>` is reachable. Some networks block fonts.googleapis.com; if so, host the font files yourself.
- **Theme flashes on load** — the `(function(){...})()` block in `<head>` prevents flash. Don't move it below the stylesheet.
- **Year-filter does nothing** — every `<article class="pub">` must have `data-year="YYYY"` matching a button's `data-year`.
- **Page is 404 on GitHub Pages** — check Settings → Pages → Source is set to `main` branch, root folder. Wait 60 seconds after first push.
