# Quantum Robotics — Design System
**Tactical Command Interface** · VEX Robotics High School Team · QR-917 Ignite Division

> Aesthetic direction: Dark military sci-fi HUD inspired by NDOS 纷争演绎 game UI.
> Sharp geometry, orange ember glow, structured information hierarchy.
> Two fonts only. No gradients on white. No purple. No Inter.

---

## 1. Color System

### Background Layers
| Token     | Value       | Usage                                                 |
|-----------|-------------|-------------------------------------------------------|
| `--bg`    | `#07090D`   | Base page background — near-black with blue-black tint |
| `--bg2`   | `#0B0E16`   | Alternate section bg — slightly lighter for contrast  |
| `--panel` | `#0E1219`   | Card / panel surface — used on all cards              |
| Footer bg | `#050710`   | Deeper than --bg, footer only                         |

### Accent — Team Orange
| Token   | Value                      | Usage                                             |
|---------|----------------------------|---------------------------------------------------|
| `--or`  | `#FF6B3B`                  | Primary accent — all interactive + highlight elements |
| `--or2` | `rgba(255,107,59, 0.16)`   | Subtle orange fill, glow backgrounds              |
| `--or3` | `rgba(255,107,59, 0.07)`   | Whisper tint — atmospheric use                    |
| Hover   | `#FF8055`                  | Button fill hover state (lighter warm orange)     |

> The orange (#FF6B3B) is derived directly from the team logo's accent bar color.

### Text Scale
| Token  | Value     | Usage                                          |
|--------|-----------|------------------------------------------------|
| `--t1` | `#F2F7FC` | Primary text — headings, emphasis, white labels |
| `--t2` | `#A8BEC8` | Body text — paragraphs, card bodies, secondary  |
| `--t3` | `#2E4252` | Muted — metadata, coordinates, disabled states  |

### Borders
| Token   | Value                      | State         |
|---------|----------------------------|---------------|
| `--bd`  | `rgba(255,107,59, 0.12)`   | Default border |
| `--bd2` | `rgba(255,107,59, 0.28)`   | Hover / active border |

### Global Background Texture
A fixed full-viewport grid overlay is applied via `body::after`:
```css
background-image:
  linear-gradient(rgba(255,107,59,0.014) 1px, transparent 1px),
  linear-gradient(90deg, rgba(255,107,59,0.014) 1px, transparent 1px);
background-size: 64px 64px;
```
Extremely subtle — gives depth and "command grid" feel without being visible as scanlines.

### Selection & Scrollbar
- Text selection: `background: rgba(255,107,59,0.20)`
- Scrollbar width: `3px`, thumb: `--bd2`, track: `--bg`

---

## 2. Typography

### Font Stack (two fonts only)

| Token  | Family         | Source                              | Weights used |
|--------|----------------|-------------------------------------|--------------|
| `--fA` | Anurati        | `Fonts/Anurati-Regular.woff` (local) | 400 / 700   |
| `--fB` | Chakra Petch   | Google Fonts CDN                    | 400 · 500 · 600 |

**Alternative title font available locally:**
| Family | Files                                         | Weights |
|--------|-----------------------------------------------|---------|
| Aquire | `Fonts/Aquire-Regular.woff`                   | 400     |
|        | `Fonts/Aquire-Bold.woff`                      | 700     |
|        | `Fonts/Aquire-Light.woff`                     | 300     |

> To switch title font from Anurati → Aquire, change `--fA` to `'Aquire', sans-serif`
> and update `@font-face` src to `Fonts/Aquire-Regular.woff`.

### @font-face declaration (in `<head>`)
```css
@font-face {
  font-family: 'Anurati';
  src: url('Fonts/Anurati-Regular.woff') format('woff');
  font-weight: 400 700;
  font-style: normal;
  font-display: swap;
}
```

### Type Scale

| Element            | Class / Selector  | Font    | Size                       | Weight | Line-height | Letter-spacing | Transform  |
|--------------------|-------------------|---------|----------------------------|--------|-------------|----------------|------------|
| Hero H1            | `.hero-h1`        | `--fA`  | `clamp(54px, 8.2vw, 118px)` | 700    | 0.92        | 0.04em         | uppercase  |
| Section H2         | `.sec-h2`         | `--fA`  | `clamp(44px, 6.2vw, 80px)` | 700    | 0.90        | 0.08em         | —          |
| Support heading    | `.sup-h`          | `--fA`  | `clamp(40px, 5.2vw, 66px)` | 700    | 0.94        | 0.07em         | uppercase  |
| Card title         | `.c-title`        | `--fA`  | 20px                       | 700    | —           | 0.09em         | —          |
| Schedule title     | `.s-title`        | `--fA`  | 18px                       | 700    | —           | 0.09em         | —          |
| Support item num   | `.sup-n`          | `--fA`  | 18px                       | 700    | —           | 0.06em         | —          |
| Nav brand name     | `.brand-name`     | `--fA`  | 13px                       | 700    | —           | 0.14em         | —          |
| Splash title       | `.sp-name`        | `--fA`  | `clamp(22px, 3vw, 34px)`   | —      | —           | 0.16em         | —          |
| Footer name        | `.ft-name`        | `--fA`  | 17px                       | 700    | —           | 0.18em         | —          |
| Schedule number    | `.s-num`          | `--fA`  | 58px                       | 700    | 1           | 0.04em         | —          |
| Body text          | `.hs-text`, `.c-body`, `.sup-desc` | `--fB` | 15px | 600 | 1.75–1.95 | —         | —          |
| Card body          | `.c-body`         | `--fB`  | 14px                       | 600    | 1.90        | —              | —          |
| Small body         | `.s-body`, `.s-body` | `--fB` | 13.5–15px               | 600    | 1.85        | —              | —          |
| Eyebrow labels     | `.sec-eye`, `.h-eyebrow`, `.hs-label` | `--fB` | 9–10px | 400 | — | 0.26–0.30em | uppercase |
| Nav links          | `.nav-links a`    | `--fB`  | 10px                       | 400    | —           | 0.14em         | uppercase  |
| Brand code         | `.brand-code`     | `--fB`  | 9px                        | 400    | —           | 0.22em         | —          |
| Buttons            | `.btn-fill`       | `--fB`  | 10px                       | 500    | —           | 0.18em         | uppercase  |
| Splash tag         | `.sp-tag`         | `--fB`  | 10px                       | 400    | —           | 0.28em         | uppercase  |
| Footer label       | `.ft-lbl`         | `--fB`  | 9px                        | —      | —           | 0.30em         | uppercase  |
| Footer text        | `.ft-txt`         | `--fB`  | 12px                       | —      | 1.85        | —              | —          |
| Footer copyright   | `.ft-copy`, `.ft-coord` | `--fB` | 9px                  | —      | —           | 0.10em         | —          |

### Orange highlight span
```html
<span class="hi">WORD</span>
```
```css
.hi {
  color: var(--or);
  filter: drop-shadow(0 0 36px rgba(255,107,59,0.60))
          drop-shadow(0 0 80px rgba(255,107,59,0.22));
}
```
Used on: hero "QUANTUM", support heading "Resources".

---

## 3. Layout & Spacing

### Page Structure
```
[ NAV fixed 58px ]
[ SPLASH fixed fullscreen overlay ]
[ #hero  100vh ]
[ #about .sec ]
[ .sec.sec-dark ]
[ .sec (support) ]
[ footer ]
```

### Grid
| Class      | Columns                    | Gap  | Breakpoint collapse     |
|------------|----------------------------|------|-------------------------|
| `.grid-2`  | `1fr 1fr`                  | 2px  | → 1-col at 1080px       |
| `.grid-3`  | `1fr 1fr 1fr`              | 2px  | → 2-col at 1080px, 1-col at 700px |
| `.sup-layout` | `1fr 1fr` gap 80px      | 80px | → 1-col at 1080px       |
| `.ft-top`  | `1fr 1.2fr 1fr` gap 48px  | 48px | → 1-col at 700px        |

> Gap is **2px** (not 16–24px). The tight seam between cards is intentional — creates a panel/tile aesthetic instead of airy card grids.

### Spacing tokens (not CSS variables — consistent values used throughout)
| Name                  | Value   |
|-----------------------|---------|
| Max content width     | 1340px  |
| Horizontal padding    | 56px    |
| Nav padding           | 0 44px  |
| Section vertical pad  | 144px   |
| Section head margin-b | 84px    |
| Card padding          | 40px 32px 32px |
| Schedule card padding | 44px 32px |
| Support item padding  | 24px 28px |
| Footer top padding    | 68px 56px 52px |
| Footer bottom padding | 20px 56px 36px |

---

## 4. Components

### Navigation
```
[ logo 36px ] [ brand name / code ] ─────── [ links ] ─────── [ Est. 2013 ]
```
- `position: fixed; top: 0; z-index: 900; height: 58px`
- `background: rgba(5,7,11,0.95)` + `backdrop-filter: blur(20px)`
- `border-bottom: 1px solid --bd`
- Link hover: `color --t1` + orange underline `scaleX(0→1)` from left, 0.24s ease
- Active link: same state as hover (`.active` class)

### Hero Section
Layer stack (back → front, all `position: absolute`):

| z-index | Element         | Class / ID     | Notes |
|---------|-----------------|----------------|-------|
| 0       | Atmospheric bg  | `.h-bg #hBg`   | Radial gradients, inset -20% for parallax room |
| 1       | Watermark logo  | `.hero-wm #hWm`| PNG logo, opacity 0.18, brightness 1.3 |
| 2       | Corner reticles | `.rc.tl/tr/bl/br` | 16×16px L-brackets, `--bd2` color |
| 3       | Content inner   | `.hero-inner`  | Text + CTA |

Hero background gradient:
```css
radial-gradient(ellipse 55% 55% at 50% 50%, rgba(140,45,10,0.22) 0%, transparent 65%),
radial-gradient(ellipse 28% 28% at 88% 18%, rgba(180,60,10,0.10) 0%, transparent 55%),
linear-gradient(160deg, #0A0C14 0%, #07090D 100%)
```

Corner reticles (HUD targeting aesthetic):
```css
.rc.tl { top:72px; left:32px;   border-width: 1px 0 0 1px; }
.rc.tr { top:72px; right:32px;  border-width: 1px 1px 0 0; }
.rc.bl { bottom:32px; left:32px; border-width: 0 0 1px 1px; }
.rc.br { bottom:32px; right:32px;border-width: 0 1px 1px 0; }
```

Scroll hint:
```css
.h-hint::before { width:1px; height:30px;
  background: linear-gradient(to bottom, var(--or), transparent); }
```

### Hero Watermark Logo
```css
.hero-wm {
  position: absolute; right: 4%; top: 50%;
  translate: 0 -50%;        /* CSS Individual Transform — vertical center */
  z-index: 1; pointer-events: none;
  will-change: transform;   /* GPU layer for Lenis */
}
.hero-wm img {
  width: clamp(260px, 30vw, 440px);
  opacity: 0.18;
  filter: brightness(1.3);
}
```
> `translate` (CSS individual transform) and `transform` (set by JS) are independent properties — they compound. JS sets only `translateY(scrollOffset)`, CSS `translate` handles the -50% centering. Do NOT put -50% inside the JS transform.

### Cards (`.card`)
```
┌─── corner reticle (.ck.tl)
│
│  [c-code]   9px orange label
│  [c-title]  20px --fA heading
│  [c-body]   14px body text
│  [c-tag]    9px bordered metadata tag
│
└────────────────── corner reticle (.ck.br)
```
- Left border accent bar: `position:absolute; left:0; width:2px; background:--or; opacity:0.25`
- Hover: border → `--bd2`, accent bar opacity → 1, corner reticles → orange
- `.ck` (corner reticle): 8×8px, single-corner L-bracket, color `--t3` → `--or` on hover

List items inside `.c-body ul`:
```css
li::before { content: '›'; color: var(--or); font-size: 16px; }
```

### Schedule Cards (`.s-card`)
Same structure as `.card` but:
- Large decorative number `.s-num`: 58px, `--fA`, `rgba(255,107,59,0.09)` — nearly invisible ghost
- Has `data-py="-55"` for parallax — number drifts upward as section scrolls in
- `.s-phase`: 9px orange label above title

### Support Section
Two-column layout: left = big heading + description, right = numbered list items
```
[ sup-h heading ]       [ 01  item title     ]
[ sup-desc body ]       [     item body       ]
                        [ 02  item title     ]
                        [ 03  item title     ]
```
`.sup-item` uses `grid-template-columns: 32px 1fr` — number column fixed 32px.

### Buttons
**`.btn-fill`** — Primary CTA:
```css
background: var(--or);
clip-path: polygon(8px 0%, 100% 0%, calc(100% - 8px) 100%, 0% 100%);
/* parallelogram — both corners clipped diagonally */
color: var(--bg);
font: 500 10px/1 var(--fB); letter-spacing: 0.18em; text-transform: uppercase;
padding: 13px 30px;
```
Hover: `background: #FF8055; box-shadow: 0 0 30px rgba(255,107,59,0.50)`

**`.btn-text`** — Secondary link:
```css
color: var(--t2); border-bottom: 1px solid var(--bd); padding-bottom: 2px;
```
Hover: `color: --or; border-color: --or`

### Section Header Pattern
```html
<div class="sec-head" data-reveal="left">
  <div class="sec-eye">// 01 · Section Name</div>
  <h2 class="sec-h2" data-py="-28">Heading</h2>
  <div class="sec-rule"></div>
</div>
```
- `.sec-eye`: 9px, `--or`, 0.3em tracking, opacity 0.6 — acts as section number prefix
- `.sec-rule`: 48×2px orange horizontal rule below heading

### Footer
Three-column grid: `[ location ] [ centered logo + name ] [ contact ]`
- Top border: `linear-gradient(90deg, transparent, --or, transparent)` at opacity 0.3
- Footer bg: `#050710` — slightly darker than `--bg`
- Bottom strip: copyright left, coordinates right (`47.6587° N · 122.1215° W`)

---

## 5. Motion & Animation System

### Smooth Scroll — Lenis
```html
<script src="https://unpkg.com/lenis@1.1.13/dist/lenis.min.js"></script>
```
Required CSS boilerplate:
```css
html { scrollbar-gutter: stable; }
html.lenis, html.lenis body { height: auto; }
.lenis.lenis-smooth { scroll-behavior: auto !important; }
.lenis.lenis-stopped { overflow: hidden; }
```
Init:
```js
const lenis = new Lenis({
  duration: 1.3,
  easing: t => Math.min(1, 1.001 - Math.pow(2, -10 * t)), // exponential
  smoothWheel: true,
});
(function raf(t) { lenis.raf(t); requestAnimationFrame(raf); })(0);
```

### Hero Parallax (6 independent layers)
Fires on `lenis.on('scroll')`, guarded to `scroll < H * 1.25` (stops below hero):

| Layer ID   | CSS class    | Speed ×  | Fade-out threshold | Notes |
|------------|--------------|----------|--------------------|-------|
| `#hBg`     | `.h-bg`      | ×0.72    | none               | Fastest — creates depth recession |
| `#hWm`     | `.hero-wm`   | ×0.45    | none               | Watermark logo mid-depth float |
| `#hEye`    | `.h-eyebrow` | ×0.48    | 42% of hero H      | Eyebrow label fades first |
| `#hTitle`  | `.hero-h1`   | ×0.28    | 58% of hero H      | Title slow drift |
| `#hSub`    | `.hero-sub`  | ×0.14    | 70% of hero H      | Subtitle barely moves |
| `#hCta`    | `.hero-cta`  | ×0.06    | 82% of hero H      | CTA anchored — fades last |

Fade formula: `opacity = Math.max(0, 1 - scroll / (H * threshold))`

### Section Parallax (`data-py` attribute)
Applied to elements in sections below hero. Activates when `scroll >= H * 1.25`.

Formula:
```js
const progress = (vh / 2 - (rect.top + rect.height / 2)) / vh;
el.style.transform = `translateY(${progress * range}px)`;
```
`progress` = 0 when element centre is at viewport bottom → 1 when at top.
`range` = pixel value from `data-py` (negative = drifts upward as it scrolls into view).

| Element     | `data-py` | Effect |
|-------------|-----------|--------|
| `.s-num`    | `-55`     | Large ghost number drifts up 55px over viewport travel |
| `.sec-h2`   | `-28`     | Section title subtle float |
| `.sup-h`    | `-22`     | Support heading mild drift |

### Scroll Reveal (`data-reveal` attribute)
IntersectionObserver with threshold 0.1 — adds `.in` class when element enters viewport.
Optional `data-delay="0.12"` (seconds) for staggered grid reveals.

| Value     | Initial state                            | Final state    |
|-----------|------------------------------------------|----------------|
| `up`      | `translateY(60px) opacity:0`            | `none opacity:1` |
| `left`    | `translateX(-70px) translateY(20px) opacity:0` | `none opacity:1` |
| `right`   | `translateX(70px) translateY(20px) opacity:0`  | `none opacity:1` |
| `scale`   | `translateY(40px) scale(0.96) opacity:0` | `none opacity:1` |

Transition: `0.85s cubic-bezier(.16, 1, .3, 1)` — springy ease-out.

### Hero Entry Animation
After splash exits, JS adds `.in` to all `.h-entry` elements:
```css
.h-entry { opacity:0; transform: translateY(28px); }
.h-entry.in { opacity:1; transform:none;
  transition: opacity 0.8s, transform 0.8s cubic-bezier(.16,1,.3,1); }
```
Staggered via inline `style="transition-delay: .10s"` etc.

### Splash Screen
| Step | Time     | Action |
|------|----------|--------|
| 0ms  | onload   | `lenis.stop()` — scroll locked. Logo: `scale(0.7) opacity(0)` |
| +1 frame | rAF | Logo → `scale(1) opacity(1)`, transition 0.9s spring |
| 800ms | setTimeout | Name slides up (translateY 10px→0), tag fades in |
| 2000ms | setTimeout | Splash gets `.exit` → `transform: translateY(-100%)`, 0.9s cubic-bezier(.76,0,.24,1) |
| 2900ms | setTimeout | `splash.style.display='none'`, `lenis.start()`, hero entries trigger |

Easing: `cubic-bezier(.76, 0, .24, 1)` — aggressive snap upward.

---

## 6. Responsive Breakpoints

| Breakpoint | Changes |
|------------|---------|
| `≤1080px`  | `.grid-2`, `.sup-layout` → 1-col; `.grid-3` → 2-col |
| `≤700px`   | `.grid-3`, `.ft-top` → 1-col; `.nav-links` hidden; `.hero-h1` forced 72px |

---

## 7. Assets & File References

### Logo — `Base/Quantum Robotics_files/logo+no+bg.png`
White geometric 3-element emblem (chevron left · spine · chevron right) with orange accent bar.
Transparent background — renders correctly on dark backgrounds without CSS adjustments.

| Use case          | Size              | Opacity | Filter          |
|-------------------|-------------------|---------|-----------------|
| Nav               | 36×36px           | 1.0     | none            |
| Splash            | 90×90px           | 0→1 animated | none       |
| Footer            | 40×40px           | 0.55    | none            |
| Hero watermark    | clamp(260px,30vw,440px) | 0.18 | brightness(1.3) |

### Fonts — `Fonts/`
| File                    | Family  | Weight | Used as |
|-------------------------|---------|--------|---------|
| `Anurati-Regular.woff`  | Anurati | 400/700| `--fA` (active) |
| `Aquire-Regular.woff`   | Aquire  | 400    | `--fA` (alt)    |
| `Aquire-Bold.woff`      | Aquire  | 700    | `--fA` (alt bold) |
| `Aquire-Light.woff`     | Aquire  | 300    | `--fA` (alt light) |

### Design Files — `Design/`
| File               | Contents |
|--------------------|----------|
| `tokens.css`       | `@font-face` declarations + all CSS custom properties |
| `design-system.md` | This document |

---

## 8. z-index Stack

| Layer              | z-index | Notes |
|--------------------|---------|-------|
| `#splash`          | 9999    | Fullscreen intro overlay |
| `nav`              | 900     | Fixed header |
| Corner reticles    | 2       | Hero HUD decoration |
| `.hero-inner`      | 3       | Hero content (above reticles) |
| `.hero-wm`         | 1       | Watermark behind content |
| `.h-bg`            | 0       | Background gradient |
| `body::after`      | 0       | Fixed grid texture |
| Sections / footer  | 1       | Above body texture |

---

## 9. CSS Custom Property Quick Reference

```css
:root {
  /* Backgrounds */
  --bg:    #07090D;
  --bg2:   #0B0E16;
  --panel: #0E1219;

  /* Accent */
  --or:    #FF6B3B;
  --or2:   rgba(255,107,59,0.16);
  --or3:   rgba(255,107,59,0.07);

  /* Text */
  --t1:    #F2F7FC;
  --t2:    #A8BEC8;
  --t3:    #2E4252;

  /* Borders */
  --bd:    rgba(255,107,59,0.12);
  --bd2:   rgba(255,107,59,0.28);

  /* Fonts */
  --fA: 'Anurati',      sans-serif;
  --fB: 'Chakra Petch', sans-serif;
}
```

---

## 10. HTML Page Sections

| Section ID / class | Content                          | Reveal direction | data-py elements |
|--------------------|----------------------------------|------------------|-----------------|
| `#splash`          | Intro overlay                    | exit: translateY(-100%) | — |
| `nav`              | Fixed navigation                 | —                | — |
| `#hero`            | Full-height landing, 6-layer parallax | h-entry (post-splash) | `.hero-wm` |
| `#about .sec`      | Features + Skills Gained cards   | left (head), up (cards) | `.sec-h2` |
| `.sec.sec-dark`    | 3-phase season schedule          | right (head), up (cards) | `.sec-h2`, `.s-num` ×3 |
| `.sec` (support)   | Mentorship overview + 3 items    | left + right     | `.sup-h` |
| `footer`           | Location / Logo / Contact + copyright | up, scale    | — |
