# Vaultr — Curated Tools & Projects

> A handpicked directory of the best dev tools and projects — sourced from the [Orynth](https://www.orynth.dev/) community. **Live at [www.vaultr.site](https://www.vaultr.site)**

---

## Overview

**Vaultr** is a static, single-file HTML directory site that showcases developer tools and projects listed on [orynth.dev](https://www.orynth.dev/). It lets users browse, filter, search, and upvote tools across six categories — all without a backend.

---

## Features

- **18 curated tools** across 6 categories (AI/ML, Dev Tools, APIs, UI/Design, Productivity, Infra)
- **Live search** — filter by name, description, or tag instantly
- **Category filters** — pill-style filter buttons per category
- **Sort** — by top upvotes or newest
- **Upvote system** — toggle upvotes per tool (client-side, session-only)
- **Featured banner** — editor's pick section linking back to Orynth.dev
- **Fully static** — zero dependencies, no build step, no backend

---

## Project Structure

```
vaultr/
├── orynth-tools.html     # Main site — single self-contained file
├── README.md             # This file
└── docs/
    └── project-docs.html # Full project documentation
```

---

## Getting Started

### Option 1 — Open directly
Just open `orynth-tools.html` in any modern browser. No server needed.

### Option 2 — Serve locally
```bash
# Python
python -m http.server 8080

# Node.js (npx)
npx serve .

# Bun
bun --bun run --hot .
```

Then visit `http://localhost:8080/orynth-tools.html`.

---

## Customizing the Tool List

All tools are defined in the `TOOLS` array inside the `<script>` block of `orynth-tools.html`.

Each tool entry looks like this:

```js
{
  id: 1,                          // Unique integer ID
  name: "Vercel",                 // Display name
  icon: "▲",                      // Emoji or symbol shown on card
  category: "infra",              // Category slug (see below)
  desc: "Deploy web projects...", // Short description (1–2 sentences)
  tags: ["Deploy", "Edge"],       // 2–3 short tag labels
  url: "https://vercel.com",      // External link
  upvotes: 841,                   // Starting upvote count
  newest: 1                       // Sort order for "Newest" (lower = newer)
}
```

### Categories

| Slug          | Label        |
|---------------|--------------|
| `ai`          | AI / ML      |
| `devtools`    | Dev Tools    |
| `api`         | APIs         |
| `ui`          | UI / Design  |
| `productivity`| Productivity |
| `infra`       | Infra        |

To add a new category, add a new entry to the `TOOLS` array and a new `<button>` in the `#filters` div:

```html
<button class="filter-btn" data-cat="newcat">New Category</button>
```

---

## Connecting to the Orynth API

If Orynth exposes a public API, replace the static `TOOLS` array with a `fetch()` call:

```js
async function loadTools() {
  const res = await fetch('https://api.orynth.dev/projects');
  const data = await res.json();
  // Map data to TOOLS format, then call render()
}
loadTools();
```

---

## Deployment

Since the site is a single HTML file, it can be deployed anywhere:

| Platform       | Command / Method                              |
|----------------|-----------------------------------------------|
| **Vercel**     | Drag & drop `orynth-tools.html` in dashboard  |
| **Netlify**    | Drop into Netlify Drop at netlify.drop         |
| **GitHub Pages**| Push to repo, enable Pages on `main` branch  |
| **Cloudflare Pages** | Connect repo, no build command needed   |
| **Railway**    | Static site deploy via GitHub                 |

---

## Design System

| Property     | Value                        |
|--------------|------------------------------|
| Background   | `#080808`                    |
| Accent       | `#c6f135` (electric lime)    |
| Surface      | `#101010` / `#141414`        |
| Border       | `#222` / `#333`              |
| Display Font | Syne (Google Fonts)          |
| Mono Font    | DM Mono (Google Fonts)       |

All colors are defined as CSS custom properties in `:root` for easy theming.

---

## Contributing

1. Fork the repo
2. Add your tool to the `TOOLS` array in `orynth-tools.html`
3. Follow the existing entry format
4. Submit a pull request with a short description of the tool

Tools must be listed on [orynth.dev](https://www.orynth.dev/) to be eligible for inclusion.

---

## License

MIT — free to use, modify, and distribute.

---

Built with ♥ by the Vaultr community · [orynth.dev](https://www.orynth.dev/)
