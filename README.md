# O'Reilly's Food Court — Website

A single-page site for O'Reilly's Food Court, a lively single food stall in Cork city serving wraps, pizza, burgers and more.

## What's in this folder

```
oreillys-food-court/
├── index.html      ← the whole site (HTML + CSS + JS, no build step)
├── images/         ← drop your real photos in here (see list below)
└── README.md       ← this file
```

Everything is self-contained in `index.html` — nothing to compile or install. Open it directly in a browser to preview it, or deploy it as-is.

Fonts (Anton + Inter + IBM Plex Mono) load from Google Fonts over the internet, so an internet connection is needed to see the intended typefaces — it still works offline, just with fallback fonts.

## Animations included

- Staggered hero headline reveal on load (each line fades/slides in with its own delay)
- Scroll-triggered fades on every major section (`IntersectionObserver`-based)
- Cursor-follow red spotlight glow on the menu cards
- Shimmer sweep on the main "Get Directions" button
- Animated count-up stats (84 Google reviews, 1 stall/full menu, 7 days open, 0 bookings required)
- A pausable marquee strip — there's a dedicated play/pause button, and it respects reduced motion
- Everything respects `prefers-reduced-motion`: animations are disabled/instant for anyone with that OS setting on

## About the empty image slots

I don't have real photos of O'Reilly's, so **I didn't fake any** — every photo slot currently shows a clean, on-brand placeholder (a thin dashed tag with the filename it's waiting for) instead of a stock photo or a broken-image icon. The page still looks fully designed and intentional as-is. As soon as you add a real file with the **exact filename** listed below to `images/`, it swaps in automatically — no HTML edits needed.

## Images to drop in

| Filename | Used for | Recommended size |
|---|---|---|
| `images/hero.jpg` | Full-bleed hero background (top of page) | 1920×1080 or larger, landscape. A wide shot of the stall in full swing — evening, some movement, a bit of neon/signage if you have it |
| `images/counter.jpg` | Story section image + the location card in "Find Us" | 1200×1500, portrait-ish. Straight-on shot of the counter, ideally mid-service |
| `images/dish-1.jpg` | "Smash Burger" card in the menu grid | 900×1200, portrait |
| `images/dish-2.jpg` | "Korean Style Burger" card | 900×1200, portrait |
| `images/dish-3.jpg` | "Caesar Chicken Wrap" card | 900×1200, portrait |
| `images/dish-4.jpg` | "Stone-Baked Pizza" card | 900×1200, portrait |
| `images/og-image.jpg` | Social share preview (link unfurl on WhatsApp/Instagram/etc.) — no on-page fallback, just skipped if missing | 1200×630, landscape |
| `images/favicon.png` | Browser tab icon — no on-page fallback, browser just shows its default icon if missing | 512×512, square, ideally your logo mark on a solid background |

Tips:
- Keep photos bright and true-to-life — the black-and-red palette does the "premium" work, so avoid heavy filters that fight it.
- Filenames are case-sensitive on GitHub Pages — match them exactly.
- Large JPGs slow the page down — aim to export photos at roughly 200–500KB each (most photo editors' "web/export" quality ~75–85% gets you there).

## Assumptions I made — please check these

You gave me the name, concept, location, vibe, brand colours and one real review, but a few operational details weren't specified. I made reasonable, editable guesses so the site doesn't ship with empty gaps — **please verify/correct them**:

- **Reservations**: you left this blank, so I built the site as **walk-in only** (matches "no queue, no fuss" food-court energy). If it's actually phone or booking-link, search `index.html` for "Walk-ins only" / "No booking needed" / "No bookings, no table service" and swap in your real reservation method + link.
- **Opening hours**: guessed as Mon–Thu 12pm–9pm, Fri–Sat 12pm–11pm, Sun 1pm–8pm. Edit the `.hours-card` block and the footer's "Hours" column, plus the `openingHoursSpecification` near the top of `index.html`.
- **Exact address**: I only had "Cork" to go on, so all "Get Directions" links point to a Google Maps **search** for "O'Reilly's Food Court Cork" rather than a precise pin. Once you have your Google Business Profile link (or exact address), replace every occurrence of `https://www.google.com/maps/search/?api=1&query=O%27Reilly%27s+Food+Court+Cork` in `index.html` with your real Maps link, and add a `streetAddress` to the JSON-LD block near the top of the file.
- **Social links**: none were provided, so none are on the page. Add them to the footer (`.footer__col`) if you have Instagram/Facebook/etc.

## Editing content

Everything is plain text inside `index.html` — search for the text you want to change (e.g. `Cork City Centre` or `12pm – 9pm`) and edit it directly. The address, opening hours, the review, and the Google Maps link are all near the top third of the `<body>`, and the Maps link is repeated in a few places (nav, hero, location card, CTA, footer) — search-and-replace all instances if it ever changes.

## Deploying free on GitHub Pages

This folder is separate from any other site you already host on this machine, so give O'Reilly's its **own** GitHub repository.

1. **Create a new empty repository on GitHub** named `oreillys-food-court` (via github.com → New repository — do not initialize it with a README).

2. **From inside this folder**, initialize git and push:

```bash
cd "D:/Work/Webistes/oreillys-food-court"
git init
git add .
git commit -m "Initial O'Reilly's Food Court site"
git branch -M main
git remote add origin https://github.com/<your-username>/oreillys-food-court.git
git push -u origin main
```

3. **Turn on GitHub Pages**:
   - Go to the repo on GitHub → **Settings** → **Pages**
   - Under "Build and deployment" → **Source**, choose **Deploy from a branch**
   - Branch: **main**, folder: **/ (root)** → **Save**

4. Wait 1–2 minutes, then your site is live at:

```
https://<your-username>.github.io/oreillys-food-court/
```

To publish updates later (e.g. after adding real photos):

```bash
git add .
git commit -m "Add real photos"
git push
```

GitHub Pages redeploys automatically within a minute or two of every push to `main`.
