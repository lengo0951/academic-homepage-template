# Design Guidelines — Scientist Homepage Template

Static personal homepage for an academic researcher. Hybrid of `yuanxzhang.github.io` (minimalist, text-first, generous whitespace) and `zwq2018.github.io` (hero photo, badge-rich pub cards). Plain HTML5 + CSS3 + vanilla JS, deployed to GitHub Pages.

## 1. Typography

### Fonts (Google Fonts)

- **Headings — Newsreader** (serif, optical sizing, full Vietnamese support)
- **Body — Inter** (sans, variable, full Vietnamese diacritics)

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&family=Newsreader:ital,opsz,wght@0,6..72,500;0,6..72,600;0,6..72,700;1,6..72,500&display=swap" rel="stylesheet">
```

### Type scale

| Token | Size | Line-height | Weight | Usage |
|---|---|---|---|---|
| `--fs-display` | 2.25rem (36px) | 1.15 | 600 | Hero name |
| `--fs-h1` | 1.625rem (26px) | 1.25 | 600 | Section headings |
| `--fs-h2` | 1.25rem (20px) | 1.3 | 600 | Subsection / pub title |
| `--fs-body` | 1.0625rem (17px) | 1.65 | 400 | Body text |
| `--fs-meta` | 0.9375rem (15px) | 1.5 | 400 | Authors, venue, dates |
| `--fs-small` | 0.8125rem (13px) | 1.45 | 500 | Nav, footer, labels |
| `--fs-badge` | 0.6875rem (11px) | 1 | 600 | Badge pills |

Headings use Newsreader; body / nav / badges use Inter. Body text 17px desktop, 16px mobile.

## 2. Color Tokens

### Light theme (`:root`)

```css
--bg:            #fbfaf7;  /* warm off-white */
--bg-elevated:   #ffffff;  /* card / hero panel */
--bg-subtle:     #f1efe9;  /* hovers, code, badges-neutral */
--text:          #1a1d23;  /* near-black body */
--text-muted:    #5a6068;  /* meta, captions */
--text-subtle:   #6e7480;  /* timestamps, divider labels — WCAG AA on --bg */
--accent:        #1e4ba0;  /* deep academic blue, links */
--accent-hover:  #173a80;
--border:        #e3dfd6;  /* hairline dividers */
--border-strong: #cdc7b9;
--shadow:        0 1px 2px rgba(20,22,28,0.04), 0 4px 12px rgba(20,22,28,0.04);
```

### Dark theme (`[data-theme="dark"]`)

```css
--bg:            #0f1620;
--bg-elevated:   #161e2a;
--bg-subtle:     #1d2735;
--text:          #e8ecf2;
--text-muted:    #a7afbd;
--text-subtle:   #828b9c;
--accent:        #6ea3e8;  /* desaturated blue, AAA on dark bg */
--accent-hover:  #8fbaf0;
--border:        #2a3444;
--border-strong: #3a4658;
--shadow:        0 1px 2px rgba(0,0,0,0.3), 0 4px 12px rgba(0,0,0,0.25);
```

WCAG: text on `--bg` ≥ 12:1 (light), ≥ 11:1 (dark). Accent on bg ≥ 4.6:1 both modes.

### Badge colors (brand-tinted)

| Badge | BG | Text |
|---|---|---|
| arXiv | `#b31b1b` | `#ffffff` |
| PDF | `#5a6068` | `#ffffff` |
| Code / GitHub | `#24292f` | `#ffffff` |
| HuggingFace | `#FFD21E` | `#1a1d23` |
| Project | `#1e4ba0` | `#ffffff` |
| Bibtex | `#7a6a3f` | `#ffffff` |
| Slides | `#0d8f6c` | `#ffffff` |
| Video | `#a13a8e` | `#ffffff` |

In dark mode, lighten by ~8%; in code use the same hex (already vivid enough).

## 3. Spacing Scale

Token: `--space-{n}` where n = 4/8/12/16/24/32/48/64/96 (px). Use only these increments.

Container: `max-width: 820px`, horizontal padding 24px (mobile 16px). Section vertical rhythm: 64px desktop, 48px mobile.

## 4. Layout & Breakpoints

| Bp | Range | Notes |
|---|---|---|
| Mobile | ≤640px | Single col, hero stacks (photo above text), nav collapses to horizontal scroll |
| Tablet | 641–1024px | Single col, hero side-by-side (photo 140px) |
| Desktop | ≥1025px | Single col 820px centered, hero photo 180px |

No multi-column main content (academic readability priority).

## 5. Component Specs

### Top Nav (sticky)
- Height 56px, `position: sticky; top: 0`, `backdrop-filter: blur(10px)`, bg = `--bg` at 85% alpha
- Hairline bottom border (`--border`)
- Left: monogram/initials (Newsreader 600, 18px). Right: anchor links (Inter 500, 13px, uppercase letter-spacing 0.04em) + theme toggle button (icon-only, 36×36, no border)
- Active section link: color = `--accent`, underline 1px offset 4px

### Hero
- Top padding 64px, bottom 48px
- Layout: photo left (180px rounded-square, 8px radius, 1px border), text block right; gap 32px
- Name: `--fs-display`, Newsreader 600
- Title: `--fs-body`, Inter 500, color `--text-muted`
- Affiliation: `--fs-body`, Inter 400, color `--text-muted`, italics optional
- Bio: `--fs-body`, max 2 lines, color `--text`
- Social icons row: 8 max, 22px icon, 8px gap, color `--text-muted`, hover → `--accent`
- Mobile: stacks vertical, photo 140px top, text below, icons centered

### Section Heading
- Newsreader 600, `--fs-h1`, color `--text`
- Hairline underline below: `border-bottom: 1px solid --border`, padding-bottom 8px, margin-bottom 24px
- No asterisk dividers (modernized vs yuanxzhang)

### News Item
- List, no bullets. Each item = flex row.
- Date: `--fs-meta`, Inter 500, color `--text-muted`, monospace tabular-nums, width 92px, format `[Mar 2026]`
- Body: `--fs-body`, color `--text`. Links underlined in `--accent`.
- Vertical gap 12px

### Publication Card
- Grid: thumbnail (left, 160×100px object-cover, 6px radius, 1px border) + content (right). Gap 20px.
- Title: `--fs-h2`, Newsreader 600, color `--text`
- Authors: `--fs-meta`, color `--text-muted`. Self-name **bold + `--text`**. `*` = equal contribution, `✉` = corresponding author (legend in section intro)
- Venue: `--fs-meta`, italic, color `--text-muted`. Year appended.
- Badges row: 8px gap, wrap, margin-top 10px
- Mobile (≤640): thumbnail full-width on top, content below

### Badge (pill)
- `display: inline-flex`, height 22px, padding 0 10px, border-radius 999px
- `--fs-badge`, Inter 600, letter-spacing 0.02em
- 14px monochrome icon left, 4px gap (optional)
- Hover: brightness 1.08 + 1px translateY(-1px), 120ms ease

### Experience Timeline
- Vertical rail: 1px `--border` at left=8px from container edge
- Each item: 14px dot (filled `--accent`) at -7px, content padded-left 28px
- Role: Inter 600 `--fs-body`. Org: Inter 400 `--text-muted`. Date: Inter 500 `--fs-small` `--text-subtle`. Location after org `· Stanford, CA`

### Honors / Services
- Honors: simple `<ul>` with year prefix span (Inter 500, `--text-muted`, width 60px) + text
- Services: 3 grouped subheadings (`<h3>` Newsreader 600, `--fs-h2`) with bulleted list under each

### Footer
- 64px top padding, hairline top border
- Three rows: (a) "Last updated: Mar 2026", (b) visitor counter slot `<div id="visitor-counter">` for clustrmaps/revolver embed, (c) © with name + License
- All `--fs-small`, color `--text-subtle`, centered

## 6. Interactions

- Smooth-scroll anchors (`scroll-behavior: smooth` + JS offset for sticky nav 72px)
- Theme toggle: persists to `localStorage('theme')`; defaults to `prefers-color-scheme`
- Year filter on Publications: pill buttons "All / 2026 / 2025 / 2024…"; toggles `[hidden]` on entries
- All transitions ≤ 200ms ease; respect `prefers-reduced-motion: reduce` (disable smooth-scroll + transitions)

## 7. Accessibility

- Semantic HTML5: `<header><nav><main><section><article><footer>`
- All sections have `id` + `aria-labelledby`
- Skip-to-content link (visible on focus)
- Theme toggle: `<button aria-label="Toggle dark mode" aria-pressed>`
- Social icons: `aria-label` on each `<a>`; SVG `aria-hidden="true"`
- Focus ring: 2px `--accent` outline, 2px offset, 4px radius
- Min touch target 44×44px (nav links use padding to meet this on mobile)
- Color contrast verified for both themes ≥ AA

## 8. Performance

- Single CSS file, single JS file (~3KB minified)
- Google Fonts via `<link>` with `display=swap` and `preconnect`
- No images required for layout (placeholder via placehold.co or inline SVG)
- Total page weight target: < 150KB excluding pub thumbnails

## 9. File Structure

```
docs/wireframe/
├── index.html       # full template, semantic, ~280 lines
├── style.css        # all tokens + components, ~520 lines
└── script.js        # toggle + smooth-scroll + filter, ~80 lines
```
