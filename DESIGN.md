---
name: Texas Dawah
description: One brand, eight distinct landing artifacts, eight switchable palettes. A shared substrate for discovering the right voice by divergence.
colors:
  ground: "#0d1230"
  surface: "#161d44"
  surface-raised: "#1d2662"
  ink: "#eef1fb"
  muted: "#aab4dc"
  accent: "#e7c66b"
  accent-deep: "#d4ac4d"
  accent-ink: "#15183a"
  accent-secondary: "#9bb4e8"
  band: "#090d24"
  band-ink: "#eef1fb"
  line: "rgba(155,180,232,0.16)"
typography:
  display:
    fontFamily: "Yeseva One, Georgia, serif"
    fontSize: "clamp(2.6rem, 6vw, 5.5rem)"
    fontWeight: 400
    lineHeight: 1.05
    letterSpacing: "-0.02em"
  headline:
    fontFamily: "League Spartan, sans-serif"
    fontSize: "clamp(1.6rem, 3vw, 2.6rem)"
    fontWeight: 800
    lineHeight: 1.1
    letterSpacing: "0.02em"
  title:
    fontFamily: "League Spartan, sans-serif"
    fontSize: "1.15rem"
    fontWeight: 700
    lineHeight: 1.2
    letterSpacing: "0.04em"
  body:
    fontFamily: "Quicksand, sans-serif"
    fontSize: "clamp(1rem, 1.1vw, 1.125rem)"
    fontWeight: 500
    lineHeight: 1.7
    letterSpacing: "normal"
  label:
    fontFamily: "League Spartan, sans-serif"
    fontSize: "0.72rem"
    fontWeight: 600
    lineHeight: 1.2
    letterSpacing: "0.14em"
rounded:
  sharp: "0"
  xs: "3px"
  pill: "999px"
  circle: "50%"
spacing:
  xs: "0.5rem"
  sm: "1rem"
  md: "1.75rem"
  lg: "3rem"
  xl: "clamp(4rem, 8vw, 7rem)"
components:
  button-primary:
    backgroundColor: "{colors.accent}"
    textColor: "{colors.accent-ink}"
    rounded: "{rounded.sharp}"
    padding: "0.85rem 1.4rem"
  button-primary-hover:
    backgroundColor: "{colors.accent-deep}"
  button-ghost:
    backgroundColor: "transparent"
    textColor: "{colors.ink}"
    rounded: "{rounded.sharp}"
    padding: "0.85rem 1.4rem"
  nav:
    backgroundColor: "{colors.ground}"
    textColor: "{colors.ink}"
    height: "72px"
  palette-chip:
    backgroundColor: "transparent"
    textColor: "{colors.ink}"
    rounded: "{rounded.pill}"
    padding: "0.5rem 0.8rem"
---

# Design System: Texas Dawah

## 1. Overview

**Creative North Star: "One invitation, eight artifacts. Discover the voice by divergence."**

Texas Dawah is in an exploration phase, and this document is honest about that. There is no single locked aesthetic yet, by design. The project's whole purpose is to discover the right form by building eight genuinely distinct landing artifacts (illuminated manuscript, austere almanac, full-bleed photo essay, kinetic girih geometry, scroll-snap poster deck, cut-paper riso zine, two-sided conversation, fixed split spread) and narrowing to the one that most truthfully conveys the mission. What this DESIGN.md governs is therefore not a single look but the **shared brand substrate** every one of those artifacts must hold constant, so the set diverges in form while staying unmistakably one brand.

That substrate has four load-bearing pillars. **The emblem and wordmark** (a geometric abstraction of the calligraphic دعوة mark plus the "dawah / TEXAS" lockup) are fixed and recolor via `currentColor`. **The type families** (Yeseva One, League Spartan, Quicksand, with Kaushan Script and Amiri as accents) are fixed; only their register shifts per artifact. **The eight-palette engine** is the signature mechanic: every page reads its colors from a shared set of `--p-*` tokens and can switch between all eight palettes at runtime via `data-palette` on `<html>`, flipping light and dark correctly. **The motion and anti-slop law** (one custom easing, progressive-enhancement reveals, the hard ban list) is fixed across the set.

What this system explicitly rejects: the saturated AI landing grammar (centered eyebrow + headline + lede + two pill buttons; an eyebrow above every section; the hero-metric stat template; identical icon-heading-text card grids; the gold-italic-word-in-a-serif-headline tic; one uniform fade-up on every section). It rejects the cultural-symbol reflex of signalling "Islamic" by turning everything green. It rejects editorial-typographic restraint deployed as a reflex rather than because a literal artifact demands it. And it rejects every em-dash and en-dash in visible copy.

**Key Characteristics:**
- One brand, eight palettes, eight distinct artifacts; distinctiveness is proven by the set staying distinct even when color is stripped.
- Type, calligraphy, and Islamic geometry carry the cultural reading, not color.
- A single accent governs any one page; the eight-palette engine swaps the whole role-token set at once.
- Crafted and predominantly rectilinear: sharp corners by default, circles for marks, pills only for utility controls.
- Flat by default; depth comes from tonal surfaces, hairline rules, and one signature offset text-shadow, not from drop shadows on cards.

## 2. Colors: The Eight-Palette Engine

The defining color decision is that there is no single palette: there are eight, and the layout is reviewed independently of any one of them. The frontmatter tokens above carry the **Midnight** palette (navy + gold, the most official brand lockup) as the canonical reference values. At runtime every color is read from a `--p-*` role token, and `data-palette` on `<html>` swaps all of them together. Five palettes are dark-ground (Midnight, Olive, Mocha, Aubergine, Geometric) and three are light-ground (Cream, Interfaith, Minimal); the role tokens flip light and dark correctly, so a layout designed in Midnight reads as a light page under Minimal without edits.

### Primary
- **Brand Accent / Gold** (`#e7c66b` in Midnight, via `--p-accent`): the single locked accent on any given page. Carries the primary CTA, the emblem, rule emphasis, and the active palette state. Its exact hue changes per palette (gold in Midnight/Olive/Aubergine/Geometric, tan in Mocha, ochre in Cream, terracotta in Interfaith, deep emerald in Minimal) but its *role* never multiplies. One accent per page, always.
- **Accent Deep** (`#d4ac4d`, via `--p-accent-deep`): the hover/pressed shade of the accent. Used only as the darker state of the same color, never as a second accent.

### Secondary
- **Accent Secondary** (`#9bb4e8`, via `--p-accent-2`): a supporting tint (powder blue in Midnight; sage, lilac, jade, clay, or terracotta per palette) for quiet emphasis, links within prose, and small marks. Subordinate to the primary accent; never competes for the CTA.

### Neutral
- **Ground** (`#0d1230`, via `--p-bg`): the page background. Deep and saturated on dark palettes; a true tinted off-white on light palettes.
- **Surface / Surface Raised** (`#161d44` / `#1d2662`, via `--p-surface` / `--p-surface-2`): raised and deeper panels. Depth is expressed by tonal step, not shadow.
- **Ink** (`#eef1fb`, via `--p-ink`): primary text. Always carried to AA against its ground.
- **Muted** (`#aab4dc`, via `--p-muted`): secondary text. Held at AA (4.5:1), never a decorative light gray.
- **Accent Ink** (`#15183a`, via `--p-accent-ink`): the text color that sits *on* an accent fill (a deep tint of the ground), so CTA labels clear AA against the accent.
- **Band / Band Ink** (`#090d24` / `#eef1fb`): the high-contrast band used for the donate/CTA strip and footer.
- **Line** (`rgba(155,180,232,0.16)`, via `--p-line` / `--p-line-2`): hairline rules. The primary structural device of the system; this is how sections, tables, and the almanac grid are drawn.

### Named Rules
**The One Accent Rule.** A single page is governed by exactly one accent (`--p-accent`). `--p-accent-deep` is its hover state, not a second color. `--p-accent-2` is a quiet supporting tint and never carries the primary call to action. If a page reads as two-accent, it has failed.

**The Token-Only Rule.** No palette-dependent color may be hardcoded in the body. Every color reads from a `--p-*` token; alpha-on-token uses `color-mix(in srgb, var(--p-token) N%, transparent)`. The only literals permitted are pure black/white shadows and the palette-definition block itself. Verify with `grep -nE '#[0-9a-fA-F]{3,6}|rgba?\(' file`.

**The Green Restraint Rule.** Never signal "Islamic" by making the page green. The cultural reading comes from typography, calligraphy, geometry, imagery, and copy. Green is one palette among eight (Minimal's emerald), never the default tell.

## 3. Typography

**Display Font:** Yeseva One (with Georgia, serif fallback)
**Body Font:** Quicksand (with sans-serif fallback)
**Label / Heading Sans:** League Spartan (with sans-serif fallback)
**Accent Script:** Kaushan Script, one phrase per page maximum
**Arabic:** Amiri (for a bismillah, a single ayah, or دعوة), used once or twice at most

**Character:** A high-contrast display serif against a rounded geometric sans, structured by a heavy grotesque for labels and headings. The pairing is warm but disciplined: Yeseva One supplies the calligraphic, illuminated weight; Quicksand keeps body copy soft and approachable; League Spartan gives the system its rectilinear, almanac-like spine. Each artifact uses these families in a *different register* (the Index is League-Spartan-led; the Folio is Yeseva-led) so the type voice differs per design while the family set stays constant. A register-justified extra face is allowed when an artifact literally demands it (for example EB Garamond for a manuscript body).

### Hierarchy
- **Display** (Yeseva One, 400, `clamp(2.6rem, 6vw, 5.5rem)`, line-height 1.05, letter-spacing -0.02em): hero words, the "dawah" wordmark, large pull-figures. The brand's signature face. Never set below ~22px and never used for long passages.
- **Headline** (League Spartan, 800, `clamp(1.6rem, 3vw, 2.6rem)`, line-height 1.1): secondary section headers, especially the uppercase poster-style headings ("BODY MEETING").
- **Title** (League Spartan, 700, 1.15rem, letter-spacing 0.04em): sub-headers, program names, table headers.
- **Body** (Quicksand, 500, `clamp(1rem, 1.1vw, 1.125rem)`, line-height 1.7): paragraphs, UI, buttons. Max measure 62-68ch.
- **Label** (League Spartan, 600, 0.72rem, letter-spacing 0.14em, uppercase): dates, kickers, metadata, nav.

### Named Rules
**The Display Floor Rule.** Display letter-spacing never goes tighter than -0.02em and never tighter than -0.04em under any circumstance; hero clamp maxes out near 5.5rem and never exceeds ~6rem. The brand is dignified, not shouting.

**The One Script Rule.** Kaushan Script appears at most once per page, on a single short phrase ("learn to invite", "sighting"). Never for body, buttons, or more than one phrase. Amiri appears at most once or twice. Script and Arabic are seasoning, not structure.

**The Functional Label Rule.** Uppercase tracked labels are functional (a date, a section name that carries information), never a decorative eyebrow stacked above every section. At most one small tracked label per three sections.

## 4. Elevation

The system is flat by default. Depth is built from tonal layering (`--p-bg` to `--p-surface` to `--p-surface-2`) and hairline rules (`--p-line`), not from drop shadows on content. The one signature exception is a soft offset text-shadow on a single hero display word, tinted to the background hue (never pure black, never on more than one word), echoing the offset shadow on the real Texas Dawah posters. Drop shadows are reserved for genuinely floating UI (the palette menu and any overlay), where a single deep ambient shadow signals "this is above the page."

### Shadow Vocabulary
- **Floating overlay** (`box-shadow: 0 24px 60px rgba(0,0,0,0.4)`): the palette switcher menu and any popover/dialog. The only place a wide drop shadow is allowed.
- **Signature display shadow** (offset ~6px down-right, tinted to the ground hue): one hero word only, for brand recognition. Decorative, deliberate, singular.

### Named Rules
**The Flat-Content Rule.** Cards, panels, list items, and buttons cast no drop shadow. They sit on the page via tonal surface and hairline. A soft wide shadow under a card is the 2014-app tell; if a surface needs separation, deepen its tone or draw a `--p-line`, never blur it.

**The No Ghost-Card Rule.** Never pair a 1px border with a wide soft drop shadow on the same element. Pick one: a single hairline rule, or (for true overlays only) the floating-overlay shadow. Never both as decoration.

## 5. Components

Component form is allowed to vary per artifact (a poster button and an almanac button are not identical), but all variants obey the same shape law, color assignment, and motion below.

### Buttons
- **Shape:** rectilinear by default (`rounded.sharp`, 0px), reflecting the letterpress/poster character. A subtle 3px (`rounded.xs`) is the maximum softening; pills (`rounded.pill`) are reserved for utility chips, not primary CTAs. Card-scale radii above 16px are prohibited.
- **Primary:** accent fill (`--p-accent`), accent-ink label (`--p-accent-ink`) for AA contrast, padding ~`0.85rem 1.4rem`. An optional trailing arrow (`→` as a glyph, not an icon font) is permitted but is not the only button form on a page.
- **Hover / Focus:** background shifts to `--p-accent-deep`; transition `transform 160ms` on the custom easing; `:active { transform: scale(0.97); }`. Visible `:focus-visible` ring required.
- **Ghost / Secondary:** transparent fill, `--p-ink` label, a `--p-line-2` hairline border, same padding and motion. Used for the lower-priority CTA so the accent stays singular.

### Cards / Containers
- **Corner Style:** 0px to 3px. Never above 16px.
- **Background:** `--p-surface` or `--p-surface-2`; separation by tone.
- **Shadow Strategy:** none (see Elevation, The Flat-Content Rule).
- **Border:** a single full hairline (`--p-line`) when separation is needed. Never a side-stripe accent border.
- **Internal Padding:** `spacing.md` to `spacing.lg`.

### Inputs / Fields
- **Style:** transparent or `--p-surface` fill, a full `--p-line-2` hairline, `rounded.xs` at most. Placeholder text held at AA (4.5:1), never the muted-gray default.
- **Focus:** border shifts to `--p-accent` plus a `--p-accent` focus ring; no glow blur.

### Navigation
- **Style:** logo lockup left (emblem + "dawah / TEXAS"); links Mission / Committee / Course / Blog; one primary action right. One line on desktop, height <= 80px (~72px). Background `--p-bg`.
- **Typography:** League Spartan labels, uppercase, tracked.
- **States:** accent underline or color on hover/active; the palette switcher chip sits beside the primary action so it stays visible on mobile. Mobile collapses to a simplified or hamburger nav.

### The Palette Switcher (signature component)
A pill-shaped chip (`rounded.pill`) carrying a three-stop gradient swatch (ground / accent / accent-2) and the active palette name, opening a listbox of all eight palettes. It reads `--p-*` tokens so it restyles itself per palette, persists the choice to `localStorage`, and accepts `postMessage({txdPalette})` from the admin master switcher. It is the one place a pill and a small functional gradient are correct, because the gradient *is* the palette preview. This is the system's defining control; copy it verbatim from `landing-options/_palette-system.md`.

### The Emblem & Wordmark (signature component)
The inline SVG emblem (circle + interlaced calligraphic stroke + two diamond dots) inherits `currentColor`, so it recolors per palette. The wordmark sets "dawah" in Yeseva One at the accent color and "TEXAS" in League Spartan, uppercase, letter-spacing ~0.38em, in a lighter tint. Fixed across every artifact. Never substitute a hand-drawn or sketchy alternative.

### Islamic Geometry (signature motif)
A tone-on-tone 8-point khatam star tessellation as a `pointer-events:none` full-bleed layer behind hero/footer, stroke at very low opacity (0.05-0.10), `currentColor` so it recolors. Quiet; it must never compete with content. Each file gives its pattern a unique id to avoid collisions.

## 6. Do's and Don'ts

### Do:
- **Do** read every color from a `--p-*` role token and keep the layout switchable across all eight palettes; verify each artifact in its native palette plus one cross-light and one cross-dark.
- **Do** keep exactly one accent per page; use `--p-accent-deep` only as its hover state.
- **Do** let typography, calligraphy, the khatam geometry, imagery, and copy carry the Islamic reading.
- **Do** hold body, label, and placeholder text at >= 4.5:1 contrast (large text >= 3:1); bump toward `--p-ink` whenever contrast is even close.
- **Do** default to sharp corners (0-3px), full circles for marks and avatars, and pills only for the utility switcher chip.
- **Do** make every artifact genuinely distinct in layout, density, alignment, image strategy, and motion: if two designs are interchangeable once color is stripped, one has failed.
- **Do** give the page a default-visible state and only enhance with reveals when JS and motion are on (add `js` to `<html>`; reveals lift an already-visible element).
- **Do** use one custom easing, `cubic-bezier(0.23, 1, 0.32, 1)`, animate only transform/opacity (plus blur/clip/mask where it helps), and honor `prefers-reduced-motion` on every animation.
- **Do** use brand-tinted initials monograms for team/committee avatars, and realistic locale-appropriate Muslim names.
- **Do** treat every picsum photo as branded duotone texture (grayscale/contrast plus a `--p-overlay` tint), not literal stock.

### Don't:
- **Don't** ship the centered AI hero (eyebrow + display headline + lede + two pill buttons), the hero-metric stat template, or identical icon-heading-text card grids.
- **Don't** stack a tiny uppercase tracked eyebrow above every section, and don't use numbered section markers (01/02/03) unless the section is a real sequence.
- **Don't** repeat the gold/accent italic word inside a serif headline as a tic, and don't apply one uniform fade-up reveal to every section.
- **Don't** signal "Islamic" by making everything green; the One Accent Rule and the eight-palette engine govern color.
- **Don't** reach for editorial-typographic restraint (display serif + small mono labels + ruled separators + monochrome) as a reflex; only when a literal artifact demands it.
- **Don't** use any em-dash or en-dash in visible copy; use hyphen, comma, period, colon, or parentheses (and scrub them from HTML comments too, so audit greps stay clean).
- **Don't** put a `border-left`/`border-right` greater than 1px as a colored stripe, gradient text (`background-clip: text`), default glassmorphism, or a wide drop shadow paired with a 1px border.
- **Don't** round cards above 16px, hardcode a palette color in the body, or let a second accent compete with the primary.
- **Don't** drive motion with `window.addEventListener('scroll')`; use IntersectionObserver or CSS scroll-driven timelines.
- **Don't** use AI-tell content: generic names ("John Doe"/"Acme"), fake-precise stats, filler verbs (Elevate/Seamless/Unleash), scroll cues, decorative status dots, locale/weather/time strips, or "Quietly trusted by".
