# Texas Dawah — Brand Spec (single source of truth for all landing-page options)

Derived by auditing 14 real Texas Dawah marketing posters in `refs/`. Every option must
honor this spec exactly so the set reads as ONE brand expressed in different palettes.

---

## 0. What Texas Dawah is (for realistic placeholder copy)

A student-led Muslim dawah organization based in Austin, Texas (UT Austin area — Nueces St / Jester
Center). Mission: share the message of Islam with wisdom and beautiful character, build bridges across
faiths, and serve the Austin community. Two audiences at once:
- Muslims who want to get involved / volunteer / donate
- Curious non-Muslims and people of other faiths exploring Islam

Real programs seen in refs (use as placeholder content): weekly **Dawah Training ("learn to invite")**,
the **"Why Islam Is True" course (now free)**, **Interfaith Iftars**, **"Baking Bread & Building Bridges"**,
**dawah tabling** on campus (the Drag / West Mall), **Book Club**, **General Body Meetings**, **Moon Sighting**,
**"What Did Jesus Really Say?"** lectures with guest scholars.

Tagline candidates: "Inviting to the way of your Lord with wisdom." · "Truth, with beautiful character." ·
"Sharing Islam. Building bridges. In the heart of Texas."

Site has 5 pages (only the LANDING page is built now; nav links point to the others as placeholders):
Mission (home) · Committee (exec team) · Course (Why Islam Is True, free) · Blog (dawah FAQ + deep dives) · Donate.

---

## 1. Logo

### Inline SVG emblem (use VERBATIM; it inherits `currentColor` so it recolors per palette)

```html
<svg class="dawah-mark" viewBox="0 0 64 64" role="img" aria-label="Texas Dawah" fill="none"
     xmlns="http://www.w3.org/2000/svg">
  <circle cx="32" cy="39" r="18.5" stroke="currentColor" stroke-width="1.4" opacity="0.8"/>
  <path d="M31 7c7.2 3.3-3.6 11.4 3 16.5 6.4 5 -4.4 9.7 1.4 15.2 4 3.8 9.4 2.3 12-1.2"
        stroke="currentColor" stroke-width="3.2" stroke-linecap="round" stroke-linejoin="round"/>
  <path d="M31 7c-1.6 1.9-1.4 4.2 .4 6.2" stroke="currentColor" stroke-width="3.2" stroke-linecap="round"/>
  <rect x="26.4" y="40.2" width="5.4" height="5.4" rx="0.6" transform="rotate(45 29.1 42.9)" fill="currentColor"/>
  <rect x="33.6" y="40.2" width="5.4" height="5.4" rx="0.6" transform="rotate(45 36.3 42.9)" fill="currentColor"/>
</svg>
```

It is an intentional, geometric abstraction of the real calligraphic mark (circle + interlaced vertical
calligraphic stroke + two diamond dots). Do NOT attempt sketchy/hand-drawn alternatives.

### Wordmark lockup (the real brand lockup is "dawah" + "TEXAS")

```html
<a class="logo" href="index.html" aria-label="Texas Dawah home">
  <span class="logo-mark"><!-- emblem SVG here, sized ~28-40px, color = accent --></span>
  <span class="logo-type">
    <span class="logo-word">dawah</span>      <!-- font: 'Yeseva One', high-contrast serif -->
    <span class="logo-tx">TEXAS</span>        <!-- font: 'League Spartan' or 'Quicksand' 600, letter-spacing .38em, uppercase -->
  </span>
</a>
```

In the real brand "dawah" is gold or the palette accent; "TEXAS" is a lighter tint. Keep that.

---

## 2. Type system (Google Fonts — load via `<link>`; this is a prototype so CDN link is fine)

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Yeseva+One&family=League+Spartan:wght@400;500;600;700;800;900&family=Quicksand:wght@300;400;500;600;700&family=Kaushan+Script&family=Birthstone&family=Amiri:ital@0;1&display=swap" rel="stylesheet">
```

Roles (do not deviate):
- **Display serif (hero words, big numbers, "dawah"):** `'Yeseva One', serif`. High contrast. This is THE brand display face.
- **Geometric caps (secondary headers like "BODY MEETING", labels, dates):** `'League Spartan', sans-serif`, weight 600-800, UPPERCASE, letter-spacing 0.04–0.16em.
- **Body / UI / paragraphs / buttons:** `'Quicksand', sans-serif`, 400-600. Body 16–18px, line-height 1.7, max width 62–68ch.
- **Brush/script accent (ONE phrase per page max, e.g. "learn to invite", "sighting"):** `'Kaushan Script', cursive`. Optional alt: `'Birthstone', cursive`. Never for body or buttons.
- **Arabic (optional bismillah / a single ayah / "دعوة"):** `'Amiri', serif`. Use tastefully, at most once or twice.

Type rules: display letter-spacing floor -0.02em (do NOT go tighter than -0.04em). `text-wrap: balance`
on h1–h3. Hero display clamp max ~ clamp(2.6rem, 6vw, 5.5rem); never above ~6rem. Yeseva One is a
display face: do not use it below ~22px or for long passages.

### Signature type treatment (optional, brand-authentic): offset drop-shadow on big display words
The posters give big serif words a soft offset shadow (slightly darker, down-right ~6px). Use sparingly
on the single hero word for brand recognition. Tint the shadow to the background hue, never pure black.

---

## 3. Palettes (each option uses EXACTLY ONE; all derived from real posters)

Use OKLCH or hex; values below are targets, refine for contrast (body text ≥ 4.5:1).

| Option | Family | bg (deep) | surface | ink (text) | muted | accent (gold/pop) | accent-2 |
|---|---|---|---|---|---|---|---|
| 1 Midnight | navy + gold | `#0d1230` | `#161d44` | `#eef1fb` | `#a9b4dc` | gold `#e7c66b` | powder blue `#9bb4e8` |
| 2 Olive Manuscript | deep olive + sage | `#1d2416` | `#2a3320` | `#ebeed6` | `#b3bb95` | gold-olive `#cdb968` | sage `#8a946f` |
| 3 Cream & Sage (LIGHT) | off-white + sage | bg `#f6f1e1` | surface `#fffdf6` | ink `#26312a` | muted `#5f6b5c` | gold `#d2992f` | sage/teal `#5d8a7b`; pops coral `#df6a4f`, blue `#6aa8c0` |
| 4 Mocha Warmth | mocha brown + tan | `#362116` | `#4d3120` | `#f1e3d4` | `#c9ab93` | tan-gold `#d8ad7c` | clay `#b06a45` |
| 5 Aubergine Nights | plum/aubergine + lilac | `#1f0f24` | `#311838` | `#f3e7f1` | `#c6a6cb` | gold `#e3c071` | lilac `#c79bd6` |
| 6 Geometric / Kinetic | deep teal/petrol + gold | `#072d2b` | `#0d3c39` | `#e8f3ee` | `#8fc1b4` | gold `#e7c66b` | jade `#46b89a` |
| 7 Photo-led Interfaith | dusty rose + ink (mixed) | light bg `#e7d3c8`, dark band `#211a17` | n/a | dark ink `#2b211c` on rose; cream `#f1e7df` on dark | `#8a6f60` | terracotta `#9c5c41` | — |
| 8 Minimal Mihrab (LIGHT) | bone + deep emerald | bg `#f4f1ea` | surface `#ffffff` | ink `#16130f` | muted `#6b6457` | deep emerald `#0c5440` | gold hairline `#bfa15a` |

ONE accent locked per page (color consistency lock). No section flips to an inverted theme except
Option 7, which is deliberately a light page with dark photo bands (allowed: one deliberate composition).

---

## 4. Islamic geometric star pattern (tone-on-tone background motif)

Subtle 8-point-star tessellation, stroke = ink/accent at very low opacity (0.05–0.10), behind hero/footer.
Use this tileable inline SVG (recolors via `color:`), placed as a `pointer-events:none` full-bleed layer:

```html
<svg class="geo-pattern" aria-hidden="true" width="100%" height="100%" style="position:absolute;inset:0;pointer-events:none">
  <defs>
    <pattern id="khatam" width="88" height="88" patternUnits="userSpaceOnUse">
      <g fill="none" stroke="currentColor" stroke-width="1">
        <rect x="22" y="22" width="44" height="44" transform="rotate(45 44 44)"/>
        <rect x="22" y="22" width="44" height="44"/>
        <rect x="-8" y="-8" width="16" height="16" transform="rotate(45 0 0)"/>
        <rect x="80" y="-8" width="16" height="16" transform="rotate(45 88 0)"/>
        <rect x="-8" y="80" width="16" height="16" transform="rotate(45 0 88)"/>
        <rect x="80" y="80" width="16" height="16" transform="rotate(45 88 88)"/>
      </g>
    </pattern>
  </defs>
  <rect width="100%" height="100%" fill="url(#khatam)"/>
</svg>
```
Wrap in a layer with `color: var(--ink); opacity: .07` (dark themes) or `color: var(--accent-2); opacity:.5`
on light themes. Give each option a UNIQUE pattern id (e.g. `khatam-1`) so multiple SVGs never collide
if combined. Keep it quiet — it must never compete with content.

---

## 5. Motion (Emil Kowalski craft bar)

- Custom easing only: `--ease-out: cubic-bezier(0.23, 1, 0.32, 1)`. Never `ease-in` on UI.
- Buttons: `transition: transform 160ms var(--ease-out)`; `:active { transform: scale(0.97); }`.
- Entrances: from `opacity:0; translateY(16px)` (never `scale(0)`); 400–600ms ease-out; stagger 40–70ms.
- Scroll reveal via IntersectionObserver (NO `window.addEventListener('scroll')`). Reveal must enhance an
  already-visible default. Set the final state as default and only animate when JS+motion are on, so the
  page is never blank without JS.
- **MANDATORY progressive-enhancement reveal pattern (do not gate content on JS):**
  Put `<script>document.documentElement.className += ' js';</script>` in `<head>` before the stylesheet.
  ```css
  .reveal{transition:opacity .6s var(--ease),transform .6s var(--ease)}
  .js .reveal{opacity:0;transform:translateY(18px)}
  .js .reveal.in{opacity:1;transform:none}
  @media (prefers-reduced-motion:reduce){ .js .reveal{opacity:1;transform:none;transition:none} }
  ```
  With no JS the content is fully visible; JS hides then reveals on scroll. Never default `.reveal` to opacity:0 unconditionally.
- Hover on cards/images: subtle `scale(1.03)` inside `overflow:hidden`, 500-700ms ease-out.
- `@media (prefers-reduced-motion: reduce)`: disable transforms, keep instant/opacity. MANDATORY.
- Only animate `transform` and `opacity` (plus blur/clip where it genuinely helps).

---

## 6. Hard anti-slop rules (Pre-Flight — failing any = not done)

- **ZERO em-dashes (—) and zero en-dashes (–) anywhere visible.** Use hyphen `-`, comma, period, colon, or parentheses. Ranges use `-`.
- Hero fits viewport: headline ≤ 2 lines, subtext ≤ 20 words / ≤ 4 lines, primary CTA visible without scroll. `min-h-[100dvh]` not `h-screen`. Hero top padding ≤ ~6rem.
- Max 4 text elements in hero (eyebrow-or-brandstrip / headline / subtext / CTAs). No trust strip, no tagline-below-CTAs inside hero.
- **Eyebrow restraint:** at most 1 small uppercase tracked label per 3 sections (hero counts as 1). Do NOT put a kicker above every section. NO numbered section markers (01/02/03) unless it's a real sequence.
- ONE accent color across the whole page. ONE corner-radius system. ONE theme (except Option 7's deliberate light+dark bands).
- No three identical feature cards; vary layout families (≥4 different families across the page). No 3+ consecutive image+text zigzag rows. Max ONE marquee per page.
- **Images: `https://picsum.photos/seed/{atmospheric-seed}/{w}/{h}` ONLY** (no loremflickr - it bakes attribution watermarks into corners; no Unsplash Source - discontinued). Picsum returns a RANDOM photo per seed (not subject-matched), so treat every photo as **branded duotone texture, not literal stock**: apply `filter:grayscale(1) contrast(1.05) brightness(.5)` (dark themes) or a palette-tinted duotone for light themes, plus a brand-color gradient overlay, so the literal subject recedes into atmosphere. Prefer atmospheric seeds (light, architecture, sky, hands, candlelight, books). This is also more on-brand: the real Texas Dawah posters are type-and-pattern-forward; photography is the exception, not the rule. Lean on TYPE + the geometric pattern + color as the primary visual language; use heavily-treated photos sparingly. NO div-based fake screenshots, NO sketchy hand-drawn SVG illustrations.
- Button contrast WCAG AA (≥4.5:1 text on its button). No CTA label wraps to 2 lines at desktop. **No duplicate CTA intent** — pick ONE label per intent. Primary conversion intent across the site = **Donate** ("Support the dawah" / "Donate"). Course CTA = "Start the free course". Keep them distinct.
- Body text ≥ 4.5:1 contrast; placeholder/label/helper text also ≥ 4.5:1. No light-gray-for-elegance.
- Nav on ONE line at desktop, height ≤ 80px. Mobile collapse explicit for every multi-column section.
- No scroll cues, no version stamps/labels, no decorative status dots, no locale/weather/time strips, no "Quietly trusted by", no fake-precise stats (any number must read as illustrative), no gradient text, no glassmorphism-as-default, no side-stripe borders, no border-radius > 16px on cards.
- For committee/team avatars (no real headshots exist), use **brand-tinted initials monograms** (a rounded square in a soft palette tint with the person's initials in Yeseva One), NOT random picsum photos. Random landscapes where faces are expected reads as broken.
- Realistic, locale-appropriate Muslim names for committee/quotes (e.g. Yusuf Rahman, Aisha Siddiqui, Bilal Ahmed, Khadija Noor, Omar Farouk, Maryam Tariq, Hamza Sheikh, Zainab Ali, Ibrahim Qureshi, Sumaya Hassan). Never "John Doe"/"Acme".
- Respect content density: section = short headline (≤8 words) + ≤25-word sub + one visual/CTA. Quotes ≤3 lines.

---

## 7. Required page structure (AIDA; every option, expressed differently per direction)

1. **Nav** (logo left; links: Mission / Committee / Course / Blog; one Donate button right). One line desktop, hamburger or simplified mobile.
2. **Hero** (mission-forward: who we are + what we do, in one breath). Primary CTA.
3. **Mission / "Who we are"** statement.
4. **What we do** (programs: Dawah Training, Interfaith Iftars, Tabling, Book Club, "Why Islam Is True", lectures). Use a layout family that fits the direction (bento, list, horizontal scroll, etc.) — vary it per option.
5. **Featured: "Why Islam Is True" course is now free** (a real conversion moment → "Start the free course").
6. **Blog teaser** (FAQ / deep dives) — 2-3 sample posts.
7. **Impact / community** (interfaith, photos) OR a testimonial/quote — illustrative only.
8. **Donate CTA band** (the conversion).
9. **Footer** (logo, nav, Austin TX address `1906 Nueces St, Austin, TX 78705`, socials as text/icon links, copyright).

Each option must use ≥ 4 different layout families across these sections and feel like a distinct design,
not a recolor of the same template.

---

## 8. Deliverable format

Each option = ONE fully self-contained `.html` file in `landing-options/` (inline `<style>`, inline
`<script>`, inline SVG logo+pattern, Google Fonts `<link>`, picsum images). No local shared dependencies.
File naming: `option-N-slug.html`. Title each `<title>` as "Texas Dawah - Option N: Name".
