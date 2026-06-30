# Texas Dawah - Redesign manifesto (for the 6 new distinct designs)

The goal: a set of 8 landing pages that are TRULY distinct artifacts, spanning the real breadth of
frontend design, with zero AI-slop. Two are already built as the quality bar:
- `landing-options/redesign-folio.html` (ornate Islamic illuminated manuscript)
- `landing-options/redesign-index.html` (austere almanac / register, table-driven)

Read BOTH before building. They set the craft bar. But note their LIMIT: both are centered, pure-type,
imageless, medium-density vertical documents. The 6 new designs must each occupy a DIFFERENT region of the
design space so the set spans the full breadth, not one corner of it.

---

## 1. Design-space axes (each new design OWNS a distinct paradigm)

Do NOT default to a centered single-column type document (the proofs already cover that). Each of the 6 owns
a paradigm the others do not touch:

- **2 Photo Documentary** - full-bleed IMAGERY-led, asymmetric magazine/photo-essay. Photography is the design.
- **3 Kinetic Geometry** - MOTION / scroll-driven scene; the Islamic geometry is the protagonist; dark, immersive; type-as-image.
- **4 Poster Stack** - SINGLE-SCREEN poster panels (scroll-snap, each 100dvh), like flipping through real event posters. Not a scrolling document.
- **5 Riso Zine** - COLLAGE / broken-grid; rotated cut-paper shapes, halftone/grain, overprint (mix-blend), stamps; playful, hand-made.
- **7 The Conversation** - asymmetric DIALOGUE; the page is the real Q&A at the table (questions on one side, answers on the other).
- **8 Split Spread** - FIXED-PANEL; a persistent brand half (fixed) + an independently scrolling content half. Two-column architecture.

Each must differ from the others AND from the two proofs on: layout structure, alignment, density,
image strategy, motion, navigation pattern, and type role. If a draft could be mistaken for another design
in the set once color is removed, it has failed.

---

## 2. Anti-slop (the specific tells to refuse)

From the design skills (design-taste-frontend, impeccable, emil, gpt-taste). The brand SLOP TEST: a viewer
should ask "how was this made?", not "which AI made this?". Refuse:

- A centered hero with eyebrow + display headline + lede + two pill buttons. (The #1 AI landing shape.)
- A tiny uppercase tracked **eyebrow above every section**. (Saturated AI scaffold.) Labels must be functional, not decorative reflex.
- The **hero-metric stat template** (big number + label + supporting stats + glow). Recast figures entirely or omit.
- **Identical card grids** (icon + heading + text repeated). 
- The **gold/accent italic word inside a serif headline** tic, repeated across sections.
- **One uniform fade-up reveal** on every section. Motion must fit the artifact; vary it or drop it.
- **Rounded-pill buttons with a `›`/arrow** as the only button. Vary button form per design.
- **The editorial-typographic lane** as a reflex (display serif + small mono labels + ruled separators + monochrome restraint). It is itself saturated now. Only use it if the design is a LITERAL artifact that requires it.
- **Monospace as costume** for "technical". Banned unless genuinely a terminal/data artifact.
- **ZERO em-dashes (—) and en-dashes (–)** anywhere visible. Use hyphen, comma, period, colon, parentheses. Verify with `grep -n $'—\|–' file`.
- AI-tell content: generic names (use Yusuf Rahman, Aisha Siddiqui, Bilal Ahmed, Khadija Noor, Omar Farouk, Maryam Tariq, Hamza Sheikh, Zainab Ali), "Acme", fake-perfect stats (label any number illustrative), filler verbs (Elevate/Seamless/Unleash), "Quietly trusted by", scroll cues, decorative status dots, locale/weather strips, version stamps, gradient text, glassmorphism-as-default, side-stripe borders, hand-drawn sketchy SVG illustrations.

The cultural reading (Islamic, dawah) should come from TYPOGRAPHY, CALLIGRAPHY, GEOMETRY, IMAGERY and COPY,
not from making everything green. Each design has ONE locked accent (the palette system handles this).

---

## 3. Brand content (realistic placeholders; reuse, reword to fit each artifact's voice)

Texas Dawah: student-led Muslim dawah org, UT Austin (1906 Nueces St, Austin TX 78705). Dual audience:
Muslims who want to get involved/donate, and non-Muslims exploring Islam. Mission: share the message of
Islam with wisdom and beautiful character; build bridges; serve Austin. The five site pages (nav targets):
Mission (home) · Committee · Course · Blog · Donate.

Programs: **Dawah tabling** (weekly, West Mall / the Drag), **Dawah training** ("learn to invite", Thursdays 8 PM,
1906 Nueces), **Interfaith iftars** (each Ramadan), **Book club & lectures** (monthly, guest scholars), the free
**"Why Islam Is True"** six-part course, **"What did Jesus really say?"** guest lectures, **interfaith dinners**.
FAQ/blog: "If God is merciful, why is there suffering?", "What the Qur'an says about Jesus, son of Mary",
"So you want to learn about Islam, begin here". Quote (illustrative): "I came to the table to argue. I left
with a friend, a book, and more questions than I started with." CTA intents (keep ONE label per intent within
a page): donate = "Support the dawah" (or a design-fitting equivalent used consistently), course = "Start the
free course", mission = "Our mission".

---

## 4. Type system

Brand fonts (Google): **Yeseva One** (high-contrast display serif), **League Spartan** (geometric grotesque,
caps/labels/heavy display), **Quicksand** (rounded sans body/UI), **Kaushan Script** (brush accent), **Amiri**
(Arabic). Each design should use them in a DIFFERENT register so the type voice differs per design (e.g. the
Index is League-Spartan-led; the Folio is Yeseva+EB-Garamond-led). A register-justified extra font is allowed
when the artifact demands it (e.g. EB Garamond for a manuscript), but avoid the reflex-reject fonts: Fraunces,
Playfair, Cormorant, Lora, Crimson, Inter, DM Sans/Serif, Space Mono, IBM Plex *, Instrument *, Outfit, Syne.
The calligraphic logo SVG (the `#mark` symbol) is in both proofs - copy it.

---

## 5. Imagery

Use `https://picsum.photos/seed/{seed}/{w}/{h}` ONLY (no loremflickr - watermarks; no guessed Unsplash IDs - 404).
Treat photos as ART-DIRECTED, not literal stock: a consistent treatment per design (editorial B&W, palette
duotone via blend + `var(--p-overlay)`, grain). Full-bleed atmospheric use is forgiving of random subjects;
prefer atmospheric seeds (light, hands, architecture, crowd, candle, sky, books, table). For the image-led
designs (Photo Documentary, Split Spread) commit to imagery; for the others use it sparingly or not at all.
For team/committee avatars use brand-tinted initials monograms, never random photos.

---

## 6. The palette system (KEEP IT - every design stays switchable)

Copy VERBATIM from `landing-options/redesign-index.html`:
- the `<style id="txd-palettes">` block (8 palettes as `--p-*` tokens) - place after the Google Fonts `<link>`.
- the palette switcher CSS, the switcher HTML (place it to fit your design's nav), and the switcher `<script>`.
Set `<html data-palette="NATIVE">` per design (see assignments). Read all colors from `--p-*` tokens; use
`color-mix(in srgb, var(--p-*) N%, transparent)` for any alpha-on-token need. No hardcoded palette colors in
the body - verify with `grep -nE '#[0-9a-fA-F]{3,6}|rgba?\(' file` (only the palette block, the JS swatch
array, and pure black/white shadows may remain). Native palettes: 2 Photo=interfaith, 3 Kinetic=geometric,
4 Poster=olive, 5 Riso=cream, 7 Conversation=mocha, 8 Split=aubergine.

---

## 7. Mandatory per design

- Self-contained `.html` (inline CSS/JS/SVG, Google Fonts link, picsum images). File: `landing-options/redesign-<slug>.html`.
- `<title>Texas Dawah - Redesign: <Name></title>`. Progressive-enhancement reveal pattern IF you use reveals
  (`<script>document.documentElement.className += ' js'</script>` in head; content visible without JS).
- Custom easing `cubic-bezier(.23,1,.32,1)`; buttons get a press state; honor `prefers-reduced-motion`;
  animate only transform/opacity (plus blur/clip/mask where it helps); NO `window.addEventListener('scroll')`
  (use IntersectionObserver or CSS scroll-driven animations `animation-timeline`).
- Responsive: explicit mobile behavior for the design's core mechanic (fixed panels stack, horizontal becomes
  vertical, poster panels still fit, etc.). Nav fits; contrast AA (body/label/placeholder >= 4.5:1).
- Communicate the mission (who we are + what we do) and route to the course and donate, in the artifact's own voice.
- Verify in 3 palettes (native + one cross-light + one cross-dark) by screenshot; fix stranded colors / contrast / overflow.
