# Product

## Register

brand

## Users

Texas Dawah is a student-led Muslim dawah organization at UT Austin (1906 Nueces St, Austin, TX 78705). The site speaks to two audiences at once, held in deliberate balance rather than ranked:

- **Curious / other-faith visitors** exploring Islam, often arriving from campus tabling on the Drag, a social post, or a friend's invitation. Their job to be done: a low-friction way to *start learning* without commitment, and to feel invited rather than sold to.
- **Muslims (UT students and the wider Austin community)** who want to get involved, volunteer, attend, and support. Their job to be done: understand what the org does and find the concrete next step to plug in.

The "build bridges" mission lives in this duality. The landing page is designed to address both visitors in one breath; neither is relegated to a secondary track.

## Product Purpose

The website exists to **maximize outreach** for the dawah, not to raise money. Success is reach and engagement, not revenue. The full site spans five pages (Mission/home, Committee, Course, Blog, Donate); currently only the landing page is being designed, as a frontend-craft exploration.

**Conversion hierarchy (this is the page's spine; it overrides the "Donate-primary" note in `landing-options/_brand-spec.md`):**

1. **Learn / read** — get visitors into the free "Why Islam Is True" course and reading the blog. This is the top outcome the page is paced toward.
2. **Show up / get involved** — tabling shifts, Thursday training, GBMs, book club, interfaith iftars. Second priority.
3. **Donate** — offered, never the climax. Deliberately deprioritized for now; the page should never pace toward the donate button as its emotional peak.

## Brand Personality

The verbal tone is **intentionally not locked yet** — this is a design-first phase. The eight landing artifacts each occupy a different point on a deliberate range from *warm and hospitable* ("come to the table") to *confident and rooted* (dignified, intellectually serious, the weight of a tradition that has answers). That spread is a feature, not indecision; the brand is being explored across its emotional breadth before a single voice is chosen. Exact copy is realistic placeholder for now and refined later.

Constants that hold regardless of where a given artifact sits on that range:

- **Wisdom and beautiful character.** Every surface should feel considered and dignified, never pushy or salesy.
- **Bridge-building.** Hospitable to the outsider, rooted for the insider.
- **An Islamic visual tradition expressed through craft** — calligraphy, geometry (the 8-point khatam star), jewel-and-cream palettes, the offset-shadow display serif — not through cliché.
- **"How was this made?", not "which AI made this?"** Distinctiveness and craft are the bar.

## Anti-references

The full anti-slop catalogue lives in `landing-options/_redesign-system.md` §2 and `_brand-spec.md` §6. The strategic anti-references:

- **The rejected `option-1..8` set.** They read as "AI slop" and went homogeneous when viewed in one palette, because all eight were built from a single shared nine-section skeleton. The redesign set fixes this: eight genuinely distinct artifacts that stay distinct even when color is removed. If a new design could be mistaken for another in the set once palette is stripped, it has failed.
- **The saturated AI landing grammar:** centered hero of eyebrow + headline + lede + two pill buttons; a tiny uppercase tracked eyebrow above every section; the hero-metric stat template; identical icon-heading-text card grids; the gold/accent italic word inside a serif headline as a tic; one uniform fade-up reveal on every section; the pill-with-arrow as the only button form.
- **The editorial-typographic lane as a reflex** (display serif + small mono labels + ruled separators + monochrome restraint). It is itself now saturated; use only when a design is a literal artifact that demands it.
- **The cultural-symbol reflex:** signalling "Islamic" by making everything green. The cultural reading must come from typography, calligraphy, geometry, imagery, and copy, with one locked accent per page.
- **AI-tell content:** generic names ("John Doe"/"Acme"), fake-precise stats, filler verbs (Elevate/Seamless/Unleash), scroll cues, decorative status dots, locale/weather strips, version stamps, gradient text, default glassmorphism, side-stripe borders, hand-drawn sketchy SVG illustrations.
- **Em-dashes and en-dashes** anywhere visible. Hyphen, comma, period, colon, or parentheses only.

## Design Principles

1. **Outreach over revenue.** Pace every page toward learning (course/blog) and showing up. Donation is offered, never the climax. The hierarchy is learn → involve → donate, in that order.
2. **One brand, many palettes, many artifacts.** The identity is a single brand expressed across switchable palettes and genuinely distinct design paradigms. Distinctiveness is proven, not asserted: the set must stay distinct even in one palette.
3. **"How was this made?", not "which AI made this?"** Refuse the saturated AI landing grammar. Earn distinctiveness through craft, structure, and a real point of view.
4. **Tradition through craft, not cliché.** Let the Islamic reading come from typography, calligraphy, geometry, imagery, and copy. One locked accent per page; never "everything green."
5. **Hold the dual audience.** The curious visitor and the involved Muslim are both addressed; warmth and confidence both keep a seat at the table.
6. **Design first, copy later.** The current phase is frontend craft and taste. Copy is realistic placeholder; verbal tone is intentionally unfixed across the set until a direction is chosen.

## Accessibility & Inclusion

- **WCAG 2.1 AA.** Body, label, and placeholder text all clear 4.5:1 contrast against their background (large text 3:1). No light-gray-for-elegance; bump body color toward the ink end of the ramp when contrast is even close.
- **Reduced motion is mandatory.** Every animation has a `@media (prefers-reduced-motion: reduce)` alternative (crossfade or instant). Animate only transform/opacity (plus blur/clip/mask where it genuinely helps); no `window.addEventListener('scroll')` driving motion.
- **Progressive enhancement.** Content is fully visible without JS; reveals enhance an already-visible default and never gate visibility on a class-triggered transition. The page must never ship blank in a headless renderer or on a hidden tab.
- **Cultural correctness.** Arabic set in Amiri and used tastefully; realistic, locale-appropriate Muslim names; team avatars as brand-tinted initials monograms rather than random photos where faces are expected.
