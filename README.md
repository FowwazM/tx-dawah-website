# Texas Dawah — Landing Page Concepts

Eight structurally distinct landing-page designs for **Texas Dawah**, a student-led Muslim dawah organization at UT Austin. Each is the same brand expressed as a different artifact. A built-in **design console** previews all eight and lets you recolor any of them across eight shared palettes, so layout and color can be judged independently.

> **Status:** design exploration. Copy and figures are placeholders and imagery is palette-toned placeholder photography. The options are here for the team to compare and pick a direction to refine.

## [Live Demo](https://fowwazm.github.io/tx-dawah-website/)

The link opens the design console (a gallery of all eight concepts). Click any concept to open the full standalone page, then use its in-page palette switcher to compare layout against color.

## The eight concepts

| # | Concept | Native palette | Idea |
|---|---|---|---|
| 01 | The Illuminated Folio | Cream | Islamic illuminated manuscript |
| 02 | Kinetic Geometry | Teal + Gold | Scroll-driven girih geometry |
| 03 | Field Record | Dusty Rose | Full-bleed duotone photo essay |
| 04 | The Conversation | Mocha | Two-sided Q&A on a central spine |
| 05 | Poster Stack | Olive | Scroll-snap poster deck |
| 06 | The Register | Bone + Emerald | Austere typographic almanac |
| 07 | Riso Zine | Cream | Cut-paper collage zine |
| 08 | Split Spread | Aubergine | Fixed brand panel + scrolling chapters |

Every page switches across all eight palettes (midnight, olive, cream, mocha, aubergine, geometric, interfaith, minimal) from its header switcher; the choice persists in `localStorage`. Opening a page from the console carries the console's currently selected palette.

## Structure

```
admin.html                       # the design console / gallery (entry point)
landing-options/
  redesign-folio.html            # 01  The Illuminated Folio
  redesign-kinetic.html          # 02  Kinetic Geometry
  redesign-photo.html            # 03  Field Record
  redesign-conversation.html     # 04  The Conversation
  redesign-poster.html           # 05  Poster Stack
  redesign-index.html            # 06  The Register
  redesign-riso.html             # 07  Riso Zine
  redesign-split.html            # 08  Split Spread
  _brand-spec.md                 # brand system (source of truth)
  _palette-system.md             # the shared eight-palette token system
  _redesign-system.md            # design manifesto and anti-slop rules
PRODUCT.md / DESIGN.md           # product + visual design context
```

The earlier `option-1..8-*.html` files are a first pass, kept for reference and not linked from the console.

## Tech

Pure static HTML/CSS/JS — no build step, no dependencies, no backend; each page is a single self-contained file. Fonts load from Google Fonts (Yeseva One, EB Garamond, League Spartan, Quicksand, Kaushan Script, Amiri); placeholder imagery from picsum.photos. Motion honors `prefers-reduced-motion`, and text targets WCAG AA contrast.

## Run locally

Open the console directly:

```sh
open admin.html
```

Or serve the folder so the console's iframes and relative links behave exactly as deployed:

```sh
python3 -m http.server 8000
# then visit http://localhost:8000/admin.html
```

## Deploy (GitHub Pages)

1. Push this repo to GitHub.
2. **Settings → Pages →** deploy from branch `main`, folder `/ (root)`.
3. Add an `index.html` that opens `admin.html` so the bare URL lands on the console, then paste the published URL into **Live demo** above.
