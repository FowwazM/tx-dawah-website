# Texas Dawah - Switchable Palette System (authoritative)

Goal: every standalone landing page can switch its color palette to any of the 8, via a header dropdown,
so layout and color can be reviewed independently. Switching flips light/dark correctly (e.g. the
Midnight layout shown in the Minimal "bone + emerald" palette becomes a light page).

Mechanism: 8 palettes are defined as a shared set of `--p-*` canonical tokens. Each file remaps its own
local CSS tokens to read from `--p-*`. The active palette is chosen by `data-palette` on `<html>`. A small
self-contained switcher sets that attribute (and persists to localStorage, and accepts postMessage from the
admin master switcher).

---

## A. Shared palette block (paste VERBATIM into every file, right after the Google Fonts `<link>`, before the main `<style>`)

```html
<style id="txd-palettes">
[data-palette="midnight"]{--p-bg:#0d1230;--p-surface:#161d44;--p-surface-2:#1d2662;--p-ink:#eef1fb;--p-muted:#aab4dc;--p-accent:#e7c66b;--p-accent-deep:#d4ac4d;--p-accent-ink:#15183a;--p-accent-2:#9bb4e8;--p-accent-3:#9bb4e8;--p-line:rgba(155,180,232,.16);--p-line-2:rgba(155,180,232,.30);--p-band:#090d24;--p-band-ink:#eef1fb;--p-overlay:rgba(13,18,48,.6)}
[data-palette="olive"]{--p-bg:#1d2416;--p-surface:#28311e;--p-surface-2:#323d26;--p-ink:#ebeed6;--p-muted:#b3bb95;--p-accent:#cdb968;--p-accent-deep:#b6a24f;--p-accent-ink:#1d2416;--p-accent-2:#8a946f;--p-accent-3:#8a946f;--p-line:rgba(235,238,214,.14);--p-line-2:rgba(235,238,214,.26);--p-band:#161c10;--p-band-ink:#ebeed6;--p-overlay:rgba(29,36,22,.6)}
[data-palette="cream"]{--p-bg:#f6f1e1;--p-surface:#fffdf7;--p-surface-2:#efe8d4;--p-ink:#24302a;--p-muted:#54604f;--p-accent:#c1851f;--p-accent-deep:#9f6e16;--p-accent-ink:#22150a;--p-accent-2:#4f7e6e;--p-accent-3:#cf5d42;--p-line:rgba(36,48,42,.14);--p-line-2:rgba(36,48,42,.26);--p-band:#3a5e52;--p-band-ink:#f4efe0;--p-overlay:rgba(36,48,42,.34)}
[data-palette="mocha"]{--p-bg:#362116;--p-surface:#48301f;--p-surface-2:#5a3c27;--p-ink:#f1e3d4;--p-muted:#c9ab93;--p-accent:#d8ad7c;--p-accent-deep:#c0925f;--p-accent-ink:#2a1810;--p-accent-2:#b06a45;--p-accent-3:#b06a45;--p-line:rgba(241,227,212,.14);--p-line-2:rgba(241,227,212,.26);--p-band:#251610;--p-band-ink:#f1e3d4;--p-overlay:rgba(40,24,16,.58)}
[data-palette="aubergine"]{--p-bg:#1f0f24;--p-surface:#2e1834;--p-surface-2:#3a1f42;--p-ink:#f3e7f1;--p-muted:#c6a6cb;--p-accent:#e3c071;--p-accent-deep:#cda74f;--p-accent-ink:#1c0c20;--p-accent-2:#c79bd6;--p-accent-3:#c79bd6;--p-line:rgba(243,231,241,.13);--p-line-2:rgba(243,231,241,.26);--p-band:#170a1b;--p-band-ink:#f3e7f1;--p-overlay:rgba(31,15,36,.6)}
[data-palette="geometric"]{--p-bg:#072d2b;--p-surface:#0d3c39;--p-surface-2:#124a46;--p-ink:#e8f3ee;--p-muted:#8fc1b4;--p-accent:#e7c66b;--p-accent-deep:#d4ac4d;--p-accent-ink:#07221f;--p-accent-2:#46b89a;--p-accent-3:#46b89a;--p-line:rgba(232,243,238,.14);--p-line-2:rgba(232,243,238,.26);--p-band:#04201e;--p-band-ink:#e8f3ee;--p-overlay:rgba(7,45,43,.6)}
[data-palette="interfaith"]{--p-bg:#e7d3c8;--p-surface:#f1e3da;--p-surface-2:#ddc6b8;--p-ink:#2b211c;--p-muted:#7a6253;--p-accent:#9c5c41;--p-accent-deep:#7d4631;--p-accent-ink:#f7efe9;--p-accent-2:#7d4631;--p-accent-3:#9c5c41;--p-line:rgba(43,33,28,.15);--p-line-2:rgba(43,33,28,.26);--p-band:#211a17;--p-band-ink:#f1e7df;--p-overlay:rgba(43,28,20,.42)}
[data-palette="minimal"]{--p-bg:#f4f1ea;--p-surface:#ffffff;--p-surface-2:#ebe7dc;--p-ink:#16130f;--p-muted:#6b6457;--p-accent:#0c5440;--p-accent-deep:#0a4435;--p-accent-ink:#f4f1ea;--p-accent-2:#bfa15a;--p-accent-3:#0c5440;--p-line:rgba(22,19,15,.12);--p-line-2:rgba(22,19,15,.22);--p-band:#0c5440;--p-band-ink:#f4f1ea;--p-overlay:rgba(12,40,33,.4)}
</style>
```

Canonical token meanings:
- `--p-bg` page bg · `--p-surface` raised surface · `--p-surface-2` deeper surface / sand
- `--p-ink` primary text · `--p-muted` secondary text
- `--p-accent` primary accent (the gold/pop) · `--p-accent-deep` darker accent (hover) · `--p-accent-ink` text that sits ON an accent button
- `--p-accent-2` secondary accent · `--p-accent-3` tertiary accent / folk pop
- `--p-line` hairline · `--p-line-2` stronger hairline
- `--p-band` contrast-band bg (donate band etc.) · `--p-band-ink` text on band
- `--p-overlay` semi-opaque rgba for photo duotone overlays (palette-hued)

## B. `<html>` tag: set the file's NATIVE palette
`<html lang="en" data-palette="X">` where X is this file's own palette key:
option-1 midnight · option-2 olive · option-3 cream · option-4 mocha · option-5 aubergine · option-6 geometric · option-7 interfaith · option-8 minimal.

## C. Remap the file's local `:root` tokens to read from `--p-*`
Keep all local token NAMES (so the CSS body is untouched) but set their values from canonical tokens. Map by role:
- local bg/page tokens -> `var(--p-bg)`; raised surfaces -> `var(--p-surface)` / `var(--p-surface-2)`
- ink/text -> `var(--p-ink)`; muted -> `var(--p-muted)`
- primary accent (gold/terracotta/emerald/etc.) -> `var(--p-accent)`; its hover -> `var(--p-accent-deep)`
- secondary accent (blue/sage/lilac/jade/clay) -> `var(--p-accent-2)`; pops (coral) -> `var(--p-accent-3)`
- lines -> `var(--p-line)` / `var(--p-line-2)`
- add helpers if the file needs them: `--accent-ink:var(--p-accent-ink); --band:var(--p-band); --band-ink:var(--p-band-ink); --overlay:var(--p-overlay);`

## D. Tokenize hardcoded palette colors (CRITICAL - this is what makes the switch clean)
`grep -nE '#[0-9a-fA-F]{3,6}|rgba?\(' yourfile.html` and convert every palette-dependent literal:
- button text colors like `color:#15183a` on the gold button -> `var(--accent-ink)` (i.e. `var(--p-accent-ink)`)
- translucent nav/menu backgrounds like `rgba(13,18,48,.72)` -> `color-mix(in srgb, var(--p-bg) 78%, transparent)`
- hero/donate radial "glow" hex like `#1a2362` -> `var(--p-surface-2)`
- photo overlay gradients (`rgba(navy,...)`) -> `var(--p-overlay)`; an accent tint -> `color-mix(in srgb, var(--p-accent) 12%, transparent)`
- a near-bg opaque gradient stop `rgba(10,13,40,.92)` -> `var(--p-bg)`
Leave alone: pure `rgba(0,0,0,...)` shadows, `#fff`/`#000` only where genuinely universal, the geometric pattern stroke (it already uses currentColor/tokens).
`color-mix(in srgb, ... )` is the tool for "token color at X% alpha". Supported in all current browsers.

## E. Switcher CSS (paste into the main `<style>`; self-contained, adapts via `--p-*`)

```css
.txd-pal{position:relative;font-family:'League Spartan',sans-serif;z-index:60}
.txd-pal-btn{display:inline-flex;align-items:center;gap:.5rem;cursor:pointer;background:color-mix(in srgb,var(--p-ink) 7%,transparent);
  border:1px solid var(--p-line-2);color:var(--p-ink);border-radius:999px;padding:.5rem .8rem;font-size:.7rem;font-weight:600;
  text-transform:uppercase;letter-spacing:.1em;transition:border-color .2s ease,background .2s ease}
.txd-pal-btn:hover{border-color:var(--p-accent)}
.txd-pal-sw{width:32px;height:13px;border-radius:999px;display:inline-block;border:1px solid var(--p-line-2);
  background:linear-gradient(90deg,var(--p-bg) 0 33%,var(--p-accent) 33% 66%,var(--p-accent-2) 66% 100%)}
.txd-pal-cv{width:13px;height:13px;opacity:.7}
.txd-pal-menu{position:absolute;top:calc(100% + 10px);right:0;min-width:252px;max-width:calc(100vw - 32px);
  background:var(--p-surface);border:1px solid var(--p-line-2);border-radius:14px;padding:.45rem;
  box-shadow:0 24px 60px rgba(0,0,0,.4);opacity:0;visibility:hidden;transform:translateY(-8px);
  transition:opacity .2s ease,transform .2s ease,visibility .2s ease;max-height:74vh;overflow:auto}
.txd-pal.open .txd-pal-menu{opacity:1;visibility:visible;transform:none}
.txd-pal-opt{display:flex;align-items:center;gap:.7rem;width:100%;text-align:left;cursor:pointer;background:none;border:0;
  color:var(--p-ink);padding:.55rem .6rem;border-radius:9px;font-size:.82rem;font-weight:600;font-family:'Quicksand',sans-serif}
.txd-pal-opt:hover{background:color-mix(in srgb,var(--p-ink) 9%,transparent)}
.txd-pal-opt[aria-selected="true"]{background:color-mix(in srgb,var(--p-accent) 20%,transparent)}
.txd-pal-opt .sw{width:30px;height:18px;border-radius:5px;flex:none;border:1px solid var(--p-line-2);
  background:linear-gradient(90deg,var(--a) 0 50%,var(--b) 50% 80%,var(--c) 80% 100%)}
.txd-pal-opt .nm{display:flex;flex-direction:column;line-height:1.18}
.txd-pal-opt .nm small{opacity:.62;font-weight:500;font-size:.7rem}
@media (max-width:680px){.txd-pal-name{display:none}}
```

## F. Switcher HTML (place inside the nav, next to the primary CTA, so it stays visible on mobile)

```html
<div class="txd-pal" data-txd-pal>
  <button class="txd-pal-btn" type="button" aria-haspopup="listbox" aria-expanded="false" aria-label="Switch color palette">
    <span class="txd-pal-sw" aria-hidden="true"></span>
    <span class="txd-pal-name">Palette</span>
    <svg class="txd-pal-cv" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" aria-hidden="true"><path d="M6 9l6 6 6-6"/></svg>
  </button>
  <div class="txd-pal-menu" role="listbox" aria-label="Color palette"></div>
</div>
```
If the nav is overflow-clipped, give the menu `position:fixed` instead, or ensure the nav is not `overflow:hidden`.

## G. Switcher JS (paste before `</body>`, after existing scripts)

```html
<script>
(function(){
  var P=[
    {k:'midnight',n:'Midnight',d:'Navy + Gold',c:['#0d1230','#e7c66b','#9bb4e8']},
    {k:'olive',n:'Olive Manuscript',d:'Deep Olive + Sage',c:['#1d2416','#cdb968','#8a946f']},
    {k:'cream',n:'Cream & Sage',d:'Off-white + Sage',c:['#f6f1e1','#c1851f','#4f7e6e']},
    {k:'mocha',n:'Mocha Warmth',d:'Mocha + Tan',c:['#362116','#d8ad7c','#b06a45']},
    {k:'aubergine',n:'Aubergine Nights',d:'Plum + Lilac',c:['#1f0f24','#e3c071','#c79bd6']},
    {k:'geometric',n:'Geometric',d:'Teal + Gold',c:['#072d2b','#e7c66b','#46b89a']},
    {k:'interfaith',n:'Interfaith',d:'Dusty Rose',c:['#e7d3c8','#9c5c41','#7d4631']},
    {k:'minimal',n:'Minimal Mihrab',d:'Bone + Emerald',c:['#f4f1ea','#0c5440','#bfa15a']}
  ];
  var root=document.documentElement, KEY='txd-palette';
  var NATIVE=root.getAttribute('data-palette')||'midnight';
  var valid=function(k){return P.some(function(p){return p.k===k})};
  var wraps=[].slice.call(document.querySelectorAll('[data-txd-pal]'));
  function label(k){var p=P.filter(function(x){return x.k===k})[0]||P[0];return p.n}
  function render(cur){wraps.forEach(function(w){
    var nm=w.querySelector('.txd-pal-name'); if(nm) nm.textContent=label(cur);
    var menu=w.querySelector('.txd-pal-menu');
    if(menu && !menu.dataset.built){P.forEach(function(p){
      var b=document.createElement('button'); b.type='button'; b.className='txd-pal-opt';
      b.setAttribute('role','option'); b.dataset.pal=p.k;
      b.innerHTML='<span class="sw" style="--a:'+p.c[0]+';--b:'+p.c[1]+';--c:'+p.c[2]+'"></span><span class="nm">'+p.n+'<small>'+p.d+'</small></span>';
      b.addEventListener('click',function(){set(p.k,true);close();}); menu.appendChild(b);
    }); menu.dataset.built='1';}
    [].slice.call(w.querySelectorAll('.txd-pal-opt')).forEach(function(o){o.setAttribute('aria-selected',o.dataset.pal===cur?'true':'false');});
  });}
  function set(k,persist){if(!valid(k))k=NATIVE; root.setAttribute('data-palette',k);
    if(persist){try{localStorage.setItem(KEY,k)}catch(e){}} render(k);}
  function openW(w){w.classList.add('open');var b=w.querySelector('.txd-pal-btn');if(b)b.setAttribute('aria-expanded','true')}
  function close(){wraps.forEach(function(w){w.classList.remove('open');var b=w.querySelector('.txd-pal-btn');if(b)b.setAttribute('aria-expanded','false')})}
  wraps.forEach(function(w){var btn=w.querySelector('.txd-pal-btn');
    if(btn)btn.addEventListener('click',function(e){e.stopPropagation();var o=w.classList.contains('open');close();if(!o)openW(w);});});
  document.addEventListener('click',function(e){if(!e.target.closest('[data-txd-pal]'))close()});
  document.addEventListener('keydown',function(e){if(e.key==='Escape')close()});
  window.addEventListener('message',function(e){var d=e&&e.data;if(d&&d.txdPalette){set(d.txdPalette,false)}});
  var params=new URLSearchParams(location.search), q=params.get('palette'), initial;
  if(q==='native'){initial=NATIVE} else if(q&&valid(q)){initial=q}
  else{var st;try{st=localStorage.getItem(KEY)}catch(e){} initial=(st&&valid(st))?st:NATIVE}
  set(initial,false);
})();
</script>
```

## H. Behavior
- On load: `?palette=KEY` query wins (no persist); `?palette=native` forces the file's own default and ignores storage (admin previews use this); else localStorage `txd-palette`; else the file's native default.
- Manual pick persists to localStorage (shared key) so a chosen palette carries across pages.
- `postMessage({txdPalette:'KEY'})` switches without persisting (admin master switcher uses this).

## I. Verify each file in 3 palettes (native + one cross light + one cross dark), e.g. midnight, minimal, interfaith.
Screenshot recipe (per file): copy file, append override `<style>.reveal{opacity:1!important;transform:none!important}.hero{min-height:auto!important;padding-top:120px!important}</style>`, set `?palette=minimal` via loading `file://...t.html?palette=minimal`, capture tall. Confirm: no stranded hardcoded color (e.g. a navy glow on an emerald page), text stays legible (AA), buttons legible, nav/cards/lines recolor. Fix any stranded literal.
