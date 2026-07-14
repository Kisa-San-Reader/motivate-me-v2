# Motivate Me v2 — Project Context

## What is this?
A PWA motivational quote app. Users tap/swipe through cards showing a background image with a quote overlaid. Subtle ambient particles float on top. There's a bell button for ambient sounds and a favorites system.

## Live URL
https://kisa-san-reader.github.io/motivate-me-v2/

## GitHub
https://github.com/Kisa-San-Reader/motivate-me-v2
- Push requires a personal access token (fine-grained, Contents: Read and write)
- Push command: `git push 'https://Kisa-San-Reader:TOKEN@github.com/Kisa-San-Reader/motivate-me-v2.git' main`
- The local git credential is for a different account (SphoorthyMasa-UXR), so always use the token URL

## Architecture
- **Single-file app**: `index.html` has all HTML, inline CSS, and JS
- **Card data**: JSON block in `<script type="application/json" id="card-data">` — array of card objects
- **Card format**: `{"text":"quote","bg":"backgrounds/bg-XXX.png","particles":"type"}`
- **No build step** — just static files served via GitHub Pages
- **Service worker** (`sw.js`): network-first strategy, bump `CACHE_NAME` version on every deploy

## Current State (as of July 14, 2026)
- **306 PNG background images** in `backgrounds/` (bg-001.png to bg-306.png)
- **306 matched quotes** — each quote matches the image category
- **CSS scene cards removed** — only PNG backgrounds remain
- **Phone emulation on desktop** — 390x844 frame centered on black
- **Mobile** — full screen, no frame

## Image Categories (sorted by bg number)
| Range | Category | Particles |
|-------|----------|-----------|
| 001-053 | Night/stars/moon | stars-big, glitter, fireflies |
| 054-092 | Water/ocean | water-sparkle, bubbles, iridescent |
| 093-131 | Greenery/forest | leaf, fall-leaves, mist |
| 132-184 | Whimsy/abstract/dreamy | glitter, iridescent, sparkles |
| 185-212 | Modern architecture | glitter, sparkles |
| 213-237 | Asian architecture | petals, diyas, fireflies |
| 238-260 | Indian architecture | diyas, marigold |
| 261-281 | European architecture | sparkles, glitter, fireflies |
| 282-290 | Aesthetic backgrounds | glitter, iridescent |
| 291-299 | Animals | butterflies, fireflies |
| 300-305 | Flowers | rose, petals, lily, magnolia |
| 306 | Food | glitter |

## Particle Types Available
petals, fireflies, sparkles, rain, lanterns, butterflies, snow, lotus, star, bubbles, leaf, sand, mist, lightning, comets, rose, marigold, lily, magnolia, iridescent, water-sparkle, diyas, fall-leaves, glitter, stars-big

## Key Features
- **Background images**: `cover` with blurred bleed layer behind for edge softness
- **No Ken Burns drift** — images are static, only particles move
- **Particles**: Slow ambient pace (12-20s durations), start within 0.3s, 25 count
- **Glitter overlay**: CSS-only sparkle layer on all image backgrounds
- **Bell button**: Toggle ambient sounds (rain, birds, water, wind, crickets) — loops per card, different sound each card
- **Favorites**: Heart button saves cards, playable as slideshow
- **Meh button**: Hides cards you don't like
- **Preloading**: Next card's image loads in background for instant transitions
- **Quote style**: White italic Georgia text with dark text-shadow

## Design Principles (from user)
- Mobile-first — only care about phone experience
- No stretching of images
- Particles should be SLOW and AMBIENT — meditative, not anxious
- No delay on particle start, but they fill space gradually
- Quotes should MATCH background themes (ocean quote = ocean image)
- More glitter is good
- Micro-animations should match aesthetic (no snow on sunny day)

## Source Images
- `New backgrounds/` folder has the originals sorted into subfolders by category
- `backgrounds/` has the cleaned sequential copies (bg-001 to bg-306)
- User screenshots images from various sources and sorts them into category subfolders

## Files
- `index.html` — the entire app (HTML + inline CSS + JS)
- `styles.css` — legacy CSS scene styles (no longer used, can be removed)
- `sw.js` — service worker
- `manifest.json` — PWA manifest
- `backgrounds/` — 306 PNG files
- `New backgrounds/` — source images in category subfolders (not in git)
- `Previous backgrounds/` — older set (not in git)
