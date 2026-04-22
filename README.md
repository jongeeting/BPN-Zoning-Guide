# BPN Zoning Guide

A reader reference site covering Philadelphia's zoning, boards, commissions, and development vocabulary. Published by [Build Philly Now](https://buildphillynow.substack.com).

Live at **[bpnguide.netlify.app](https://bpnguide.netlify.app)**.

## What's here

Five static HTML pages + one shared stylesheet:

| Page | Purpose |
|---|---|
| `index.html` | Landing page with links to the four reference pages |
| `who-decides-what.html` | Philadelphia's building-relevant boards, commissions, and departments — full current rosters, meeting info, jurisdiction, political context |
| `glossary.html` | Plain-language definitions of 34 key terms across zoning, historic preservation, land disposition, and politics |
| `philly-zoning-districts.html` | Plain-language guide to the core zoning districts most readers will encounter |
| `philly-zoning-districts-other.html` | Every base zoning district in Title 14, organized by family |
| `styles.css` | Shared styles for `who-decides-what.html` and `glossary.html` |

No build step, no framework, no dependencies. Plain HTML + CSS + a small amount of vanilla JS.

## Editing

Each HTML file is the canonical source for its page. Edit the file, preview locally, push. Netlify redeploys on push.

- **Member rosters** (board chairs, commissioners, council members) live in `who-decides-what.html` and are sourced from phila.gov, phlcouncil.com, phdcphila.org, and phillylandbank.org. Each card's "Members" field shows the count expected by the charter alongside the current roster so vacancies are explicit.
- **Glossary terms** live in `glossary.html` inside `#glossaryGrid`. Each term is a `<div class="g-term" data-cluster="…">` — the `data-cluster` attribute controls which topic filter it belongs to (`historic`, `disposition`, `political`, `planning`).
- **Zoning districts** live in the two `philly-zoning-districts*.html` files. These have their own inline styles and are not yet unified with `styles.css`.

When a piece of data needs verification, mark it with a yellow **TK** span — the convention is explained in each page's info-box.

## Preview locally

No build step. Any static server works:

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

## Deploy

Hosted on Netlify. Every push to `main` triggers an auto-deploy. `netlify.toml` configures:

- `pretty_urls = true` so `/who-decides-what` resolves to `/who-decides-what.html`
- Short HTML cache (5 min), longer CSS cache (24 h)
- Basic security headers

Legacy hash URLs (`bpnguide.netlify.app/#RSA-5`) are redirected client-side by a small shim in `index.html`.

## Accessibility

- Expandable cards and glossary terms are keyboard-operable (Enter / Space) with visible focus rings
- ARIA `role="button"` + `aria-expanded` added via JS at load
- Semantic headings, responsive to small screens

## Corrections

Email [tips@buildphillynow.com](mailto:tips@buildphillynow.com) or open an issue.

## License

Content: © Build Philly Now. Code: CC0 — use the scaffolding if it's useful to you.
