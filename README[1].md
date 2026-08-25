# Profile ↔ Position Matcher

A single-file, self-contained tool for matching candidate profiles against open job positions. Styled as a talent case file / dossier.

**[▶ Live Demo](https://sireeshabathu-oss.github.io/profile-position-matcher/)**

![Match Matrix screenshot](screenshots/match-matrix.png)

## Features

- **Candidates** — add multiple profiles: name, years of experience, skills, and a short note
- **Positions** — add multiple roles: required skills, nice-to-have skills, minimum experience
- **Match Matrix** — a candidate × position grid with color-coded fit scores, a "top pick per position" summary, and a click-to-expand breakdown of matched/missing skills per pair

## Scoring

Each match score is computed as:

- Required skills overlap — 70%
- Nice-to-have skills overlap — 20%
- Experience fit (candidate years vs. minimum required) — 10%

## Screenshots

| Candidates | Positions |
|---|---|
| ![Candidates tab](screenshots/candidates.png) | ![Positions tab](screenshots/positions.png) |

| Match Matrix | Match Detail |
|---|---|
| ![Match matrix](screenshots/match-matrix.png) | ![Match detail drawer](screenshots/match-detail.png) |

## Usage

Just open `index.html` in any browser — no build step, no dependencies, no server required. All data lives in memory for the session (nothing is sent anywhere or persisted to disk).

1. Add one or more **candidates** (name, years of experience, skills, optional note)
2. Add one or more **positions** (title, required skills, nice-to-have skills, minimum experience)
3. Switch to **Match Matrix** to see color-coded fit scores for every candidate × position pair
4. Click any score cell to expand a breakdown of matched vs. missing skills for that pair

You can also serve it as a static page (e.g. via GitHub Pages) to share a live link.

## Enabling GitHub Pages (optional)

Already live for this repo at the link above. To do the same for your own fork:

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Under "Build and deployment", set Source to **Deploy from a branch**, branch `main`, folder `/ (root)`
4. Your tool will be live at `https://<your-username>.github.io/<repo-name>/`

## Tech Stack

No frameworks, no package manager, no build step — everything lives in the one `index.html` file.

| Layer | Choice |
|---|---|
| Markup | Plain HTML5 |
| Styling | Hand-written CSS (custom properties for theming, CSS Grid/Flexbox for layout, no framework) |
| Logic | Vanilla JavaScript (ES6+), DOM APIs only — no React/Vue/etc. |
| Fonts | [Google Fonts](https://fonts.google.com/) — Special Elite, Libre Baskerville, IBM Plex Mono (loaded via CDN `@import`) |
| State | In-memory JS arrays (`candidates`, `positions`) — nothing persisted or sent over the network |
| Hosting | Any static file host — works from `file://`, or deploy to GitHub Pages, Netlify, Vercel, etc. |

Because it's a single dependency-free file, you can copy `index.html` anywhere and it just works — no `npm install`, no server, no bundler.

## Roadmap

Ideas for future iterations, roughly in order of usefulness:

- [ ] **Persistence** — save candidates/positions to `localStorage` so data survives a page refresh
- [ ] **Import/export** — load and save candidate/position lists as JSON or CSV
- [ ] **Editable entries** — edit an existing candidate/position in place instead of remove-and-re-add
- [ ] **Configurable weights** — let users adjust the 70/20/10 scoring split from the UI
- [ ] **Skill synonyms** — fuzzy/alias matching (e.g. "JS" ↔ "JavaScript") instead of exact string match
- [ ] **Sortable/filterable matrix** — sort the match matrix by score, filter by minimum threshold
- [ ] **Shareable state** — encode the current data set in the URL so a filled-in case file can be shared via link
- [ ] **Print/PDF export** — export the match matrix or a single candidate's detail as a printable report
- [ ] **Multi-file split** — optionally split into separate HTML/CSS/JS files for easier contribution, while keeping a bundled single-file build for the "no build step" use case

Contributions and suggestions welcome — feel free to open an issue or PR if you build on this.

## License

[MIT](LICENSE) — free to use, modify, and distribute.

