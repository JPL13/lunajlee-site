# lunajlee.com — site source

Static site for lunajlee.com (no build step — plain HTML/CSS).

- `index.html` — personal homepage
- `first90days/` — First 90 Days teen money posts + Minimum Payment Calculator (`first90days/calculator/`)
- `calculators/` — calculators landing page

## Deploy
Hosted on Cloudflare Pages with Git integration: every push to `main` deploys automatically.
Production branch: `main`. Build command: none. Output directory: `/` (repo root).

## Edit guide — which file controls which page

| Page (URL) | File to edit |
|---|---|
| Homepage — lunajlee.com | `index.html` (name, tagline, the three cards, footer links) |
| Calculators — lunajlee.com/calculators/ | `calculators/index.html` |
| First 90 Days posts — lunajlee.com/first90days/ | `first90days/index.html` — all three posts live in this one file |
| Post images | `first90days/assets/` (hero, paycheck, apartment, credit `.webp` files) |
| Calculator (standalone) — lunajlee.com/first90days/calculator/ | `first90days/calculator/index.html` |
| Shared look (fonts, colors, header, cards, footer) for the homepage + calculators page | `assets/site.css` |
| Browser-tab icon | `favicon.svg` (charcoal rounded square, sans-serif L, rust dot) |

The First 90 Days pages keep their own built-in styles (they were designed as a set); they carry a slim `lunajlee.com` bar on top injected as `.lj-bar` styles inside each file — edit those blocks in place if you ever need to change the bar.

**One trap:** the Minimum Payment Calculator exists in *two* places — embedded inside `first90days/index.html` and standalone in `first90days/calculator/index.html`. If you ever change how the calculator works (not just wording around it), make the same change in both files, or the two copies will drift apart.

**Don't rename folders.** The URL is the folder name: renaming `first90days/` changes lunajlee.com/first90days/ and breaks every link already posted.

**Preview before pushing:** open the HTML file in a browser, or run `python3 -m http.server 8000` in this folder and visit `localhost:8000`.

**After pushing:** the deploy takes about a minute. Check the change at lunajlee.com (hard-refresh with Cmd+Shift+R if it looks stale — the CDN caches briefly).

## Local testing (before you push)

Don't double-click the HTML files — the links between sections start with `/` (root-relative), so they break under `file://`. Run a tiny local server instead, from this folder:

```sh
cd lunajlee-site-repo
python3 -m http.server 8000
```

Then open `http://localhost:8000` and click through. Stop the server with Ctrl+C when done.

Pre-push checklist:
- Homepage loads; all three cards' links work
- `/first90days/` — posts render, all four images show
- Calculator (both copies): defaults give 61 months and $925.71 interest for $1,200 at 24.99% APR paying $35/mo; a payment under the first month's interest ($24.99) triggers the never-pays-off warning
- `/calculators/` — all three outbound links open
- Shrink the browser window to phone width and confirm nothing overflows

**Even safer — preview deploys:** push your edit to a *branch* instead of `main` and Cloudflare Pages builds a preview at `<branch>.lunajlee-site.pages.dev`. Check it there; merge to `main` only when it looks right, and only `main` touches the live site.
