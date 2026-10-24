# VNW entry page, production package

One static file. No build step, no dependencies.

## What is inside
| File | Purpose |
|---|---|
| `index.html` | The entry page: torn-paper loading, the split, the tear and the redirect |
| `switch-button.html` | Snippet for BOTH portfolios: the "switch style" button that returns here |
| `_headers` | Security and cache headers (Netlify / Cloudflare Pages) |
| `robots.txt` | Allows indexing |

## Before you deploy: replace the demo values
Open `index.html` and edit these (search for the names):

| Name | Where | What to put |
|---|---|---|
| `SITES.L.url` | script | Your **Kingdom** portfolio URL (currently `https://example.com/`) |
| `SITES.R.url` | script | Your **Lab** URL (already `https://www.nayaka100.in/`) |
| `EMAIL` | script | Your email (shown by `hire()` in the console) |
| `RESUME_URL` | script | Optional resume link. Leave `''` to hide the small "resume" tag |
| `<noscript>` links | body | Same two URLs again, for visitors without JavaScript and for crawlers |

The console prints a warning if the Kingdom link is still the demo one.

## Recommended URL layout
- `/` this entry page
- `/lab` and `/kingdom` the two portfolios (or two separate domains)

If the portfolios stay on other domains, use their full URLs above and in `switch-button.html`.

## The "switch style" button
1. Open `switch-button.html`, set `STYLE` (`'lab'` or `'kingdom'`), `OPENING_URL` (where this page lives) and `POSITION`.
2. Paste the whole block once before `</body>` on every page of each portfolio.
3. The button links to `OPENING_URL?switch=1`, which skips the loading and goes straight to the split.
4. The Kingdom site has a chat button at the bottom right, so use `bottom-left` or `bottom-center` there.

## How the page behaves
- Loading always plays in full. "skip" or Esc jumps to the end. "Open the file" opens the split.
- Drag the tear to either edge (or tap a side, press Enter on a button, or use the left and right arrow keys) to open that portfolio.
- Tear sound: none. Motion toggle (bottom-left) switches the endless loops off; the OS "reduce motion" setting turns it on by default.
- The redirect happens in the same tab. Chrome, Edge and Safari 18+ cross-fade between pages via `@view-transition`; other browsers still get the fade-in.

## Optional: self-host the fonts
The page loads Caveat and Permanent Marker from Google Fonts. To self-host: download both from fonts.google.com, put the `.woff2` files in `/fonts`, add `@font-face` rules at the top of the `<style>` block, then delete the three Google Fonts `<link>` tags (two `preconnect`, one `stylesheet`) in `index.html` and the font link inside `switch-button.html`.

## Test checklist
- [ ] Loading plays and the Kingdom/Lab links go to the right sites
- [ ] Drag to each edge, and tap each side, on desktop and on your phone
- [ ] "switch style" returns here from both portfolios
- [ ] Works with JavaScript off (two plain links)
- [ ] Lighthouse on the entry page

## Optional extras
- Add `<meta property="og:image">` with a 1200x630 preview image and `<link rel="canonical">` once the domain is final.
