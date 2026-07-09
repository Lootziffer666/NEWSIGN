# SWIFT Hero Carousel Build Prompt

Build a single full-viewport hero section in React + TypeScript + Vite + Tailwind CSS, using `lucide-react` for icons. The component is a procedural sprite-production carousel called **SWIFT**.

SWIFT is a fast visual production pipeline for game creators. It turns 3D models, visual ideas, sketches, source assets, or character concepts into clean 2D/3D decisions, render previews, turntables, sprite sheets, masks, depth passes, thumbnails, and game-ready output.

Keep the exact carousel structure, image URLs, colors, responsive behavior, animation timings, role logic, layout, typography, grain overlay, button styling, and technical implementation described below.

Do not change any image URL.
Do not redesign the page.
Only transform the branding, copywriting, labels, and product logic from a character-figurine carousel into SWIFT's procedural sprite/render pipeline.

The page should feel playful, cartoony, fast, sharp, and production-focused — like a small game asset machine rather than a toy shop.

---

## Fonts

Load in `index.html` head:

```html
<link rel="preconnect" href="https://fonts.googleapis.com" />
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin />
<link href="https://fonts.googleapis.com/css2?family=Anton&family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet" />
```

Body font: `'Inter', sans-serif`.

Display font for huge ghost text and bottom-right link: `'Anton', sans-serif`.

---

## Image data

Use 4 items with the exact URLs and colors below. These are placeholder character/model images and should be treated as SWIFT input/output preview subjects. Keep every URL and color exactly as provided.

```ts
const IMAGES = [
  {
    src: 'https://fifth-gentle-45902158.figma.site/_components/v2/4de492f6d9cf8244ad5293233e5c6f52407d42fc/1.02464a56.png',
    bg: '#F4845F',
    panel: '#F79B7F',
    mode: '3D INPUT',
    output: 'SPRITE SHEET'
  },
  {
    src: 'https://fifth-gentle-45902158.figma.site/_components/v2/4de492f6d9cf8244ad5293233e5c6f52407d42fc/2.b977faab.png',
    bg: '#6BBF7A',
    panel: '#85CC92',
    mode: 'TURNAROUND',
    output: '8 ANGLES'
  },
  {
    src: 'https://fifth-gentle-45902158.figma.site/_components/v2/4de492f6d9cf8244ad5293233e5c6f52407d42fc/3.4df853b4.png',
    bg: '#E882B4',
    panel: '#ED9DC4',
    mode: 'RENDER PASS',
    output: 'MASKS + DEPTH'
  },
  {
    src: 'https://fifth-gentle-45902158.figma.site/_components/v2/4de492f6d9cf8244ad5293233e5c6f52407d42fc/4.4457fbce.png',
    bg: '#6EB5FF',
    panel: '#8DC4FF',
    mode: 'STYLE LOCK',
    output: 'GAME READY'
  },
];
```

Preload all 4 images on mount via `new Image()`.

---

## State & logic

- `activeIndex` from 0–3.
- `isAnimating` boolean lock.
- `isMobile` = `window.innerWidth < 640`, updated on resize.
- `navigate('next' | 'prev')`: ignore if animating; set `isAnimating=true`; bump `activeIndex` using `(prev+1)%4` or `(prev+3)%4`; release lock after `650ms`.
- Roles derived from activeIndex:
  - `center=activeIndex`
  - `left=(activeIndex+3)%4`
  - `right=(activeIndex+1)%4`
  - `back=(activeIndex+2)%4`

---

## Layout structure

Outer `<div>` has:

- `backgroundColor: IMAGES[activeIndex].bg`
- transition `background-color 650ms cubic-bezier(0.4,0,0.2,1)`
- `fontFamily: 'Inter, sans-serif'`
- `relative w-full overflow-hidden`

Inside, a `relative w-full` div with:

```css
height: 100vh;
overflow: hidden;
```

---

## 1. Grain overlay

`absolute inset-0 pointer-events-none`, `zIndex: 50`.

Use an SVG fractalNoise data URI:

- `baseFrequency=0.9`
- `numOctaves=4`
- opacity 0.08 inside SVG
- container `opacity: 0.4`
- `backgroundSize: 200px 200px`
- repeat

This should read as subtle render grain / viewport noise.

---

## 2. Giant ghost text

Text:

```text
SPRITE FORGE
```

Style:

- `absolute inset-x-0 flex items-center justify-center pointer-events-none select-none`
- `zIndex: 2`
- `top: 18%`
- font Anton
- `fontSize: clamp(90px, 28vw, 380px)`
- weight 900
- color white
- opacity 1
- lineHeight 1
- uppercase
- letterSpacing `-0.02em`
- whiteSpace nowrap

---

## 3. Top-left brand label

Text:

```text
SWIFT
```

Position:

- `absolute top-6 left-4 sm:left-8`
- `zIndex: 60`

Style:

- `text-xs font-semibold uppercase`
- white
- opacity 0.9
- letterSpacing `0.18em`

Add a second tiny line under the brand:

```text
PROCEDURAL SPRITE PIPELINE
```

Style:

- `text-[10px]`
- uppercase
- white
- opacity 0.65
- letterSpacing `0.22em`
- marginTop 4px

---

## 4. Carousel

`absolute inset-0`, `zIndex: 3`.

Map all 4 `IMAGES`.

Each item:

- `position: absolute`
- `aspectRatio: '0.6 / 1'`
- role-based styles below

Inside each item, render an `<img>` with:

- `width: 100%`
- `height: 100%`
- `objectFit: contain`
- `objectPosition: bottom center`
- `draggable=false`

### Per-role style

**center**

- `transform: translateX(-50%) scale(${isMobile ? 1.25 : 1.68})`
- no blur
- opacity 1
- zIndex 20
- `left: 50%`
- `height: isMobile ? '60%' : '92%'`
- `bottom: isMobile ? '22%' : 0`

**left**

- `transform: translateX(-50%) scale(1)`
- blur 2px
- opacity 0.85
- zIndex 10
- `left: isMobile ? '20%' : '30%'`
- `height: isMobile ? '16%' : '28%'`
- `bottom: isMobile ? '32%' : '12%'`

**right**

Same as left, but:

- `left: isMobile ? '80%' : '70%'`

**back**

- `transform: translateX(-50%) scale(1)`
- blur 4px
- opacity 1
- zIndex 5
- `left: 50%`
- `height: isMobile ? '13%' : '22%'`
- `bottom: isMobile ? '32%' : '12%'`

Transition on each item:

```css
transform 650ms cubic-bezier(0.4,0,0.2,1),
filter 650ms cubic-bezier(0.4,0,0.2,1),
opacity 650ms cubic-bezier(0.4,0,0.2,1),
left 650ms cubic-bezier(0.4,0,0.2,1)
```

Use:

```css
will-change: transform, filter, opacity;
```

The character/model images sit at the bottom of the screen overlapping the giant `SPRITE FORGE` text behind them.

---

## 5. Bottom-left text + nav buttons

Position:

- `absolute bottom-6 left-4 sm:bottom-20 sm:left-24`
- `zIndex: 60`
- `maxWidth: 320px`

First paragraph:

```text
SWIFT OUTPUT MODE
```

Style:

- bold uppercase
- tracking-widest
- `mb-2 sm:mb-3`
- `text-base sm:text-[22px]`
- white
- opacity 0.95
- letterSpacing `0.02em`

Second paragraph, dynamic from active image:

```text
{IMAGES[activeIndex].mode} → {IMAGES[activeIndex].output}
```

Style:

- uppercase
- font-semibold
- `text-sm sm:text-base`
- white
- opacity 0.9
- `mb-2`

Description paragraph, hidden on mobile using `hidden sm:block`:

```text
Drop in a model, sketch, or idea. SWIFT chooses the right 2D/3D path, renders clean previews, and prepares production-ready sprite outputs without manually touching the full pipeline.
```

Style:

- `text-xs sm:text-sm`
- white
- opacity 0.85
- lineHeight 1.6
- `mb-4 sm:mb-5`

Navigation buttons:

Two circular buttons:

- `w-12 h-12 sm:w-16 sm:h-16`
- transparent background
- 2px white border
- white icon
- icons: `ArrowLeft` and `ArrowRight` from `lucide-react`
- size 26
- strokeWidth 2.25
- hover scale 1.08
- hover background `rgba(255,255,255,0.12)`
- transition `transform 150ms, background-color 150ms`
- click triggers `navigate('prev')` / `navigate('next')`

---

## 6. Bottom-right link

Text:

```text
GENERATE SHEET
```

Position:

- `absolute bottom-6 right-4 sm:bottom-20 sm:right-10`
- `zIndex: 60`

Element:

`<a>` flex items-center.

Style:

- font Anton
- `fontSize: clamp(20px, 4vw, 56px)`
- weight 400
- white
- opacity 0.95 to 1 on hover, 200ms
- letterSpacing `-0.02em`
- lineHeight 1
- uppercase
- no underline

Followed by `ArrowRight`:

- `w-5 h-5 sm:w-8 sm:h-8`
- strokeWidth 2.25

---

## Behavior summary

Clicking arrows rotates roles.

Background color, image positions, scales, blurs, and opacities all crossfade simultaneously over 650ms with `cubic-bezier(0.4,0,0.2,1)`.

The character/model images sit at the bottom of the screen overlapping the giant `SPRITE FORGE` text behind them.

---

## Content rules

Do not mention:

- figurines
- toy shop
- collectibles
- NFT
- blockchain
- marketplace
- rarity
- wallet
- minting
- ownership

Instead communicate:

- procedural sprites
- 2D/3D decision
- render pipeline
- sprite sheets
- model-to-preview
- turntables
- masks
- depth passes
- thumbnails
- production-ready output
- fast iteration
- game asset workflow

The page should feel like a fast, cartoony production machine that turns source material into usable game assets.

Keep every animation, every image URL, every responsive behavior, every carousel rule, every timing, every blur, every opacity, every layout value, every color, and every technical implementation exactly as described. Only transform the narrative, copywriting, labels, and logic into SWIFT's procedural sprite/render workflow.
