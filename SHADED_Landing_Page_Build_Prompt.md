# SHADED Landing Page Build Prompt

Build a single-page landing site for **SHADED** with two full-height sections: **Hero** and **Capabilities**. Both sections use looping background videos with custom JS crossfade, a shared liquid-glass design system, and Framer Motion entrance animations.

SHADED is a shader-first visible-world-rules system for games.

Core principle:

```text
WHAT YOU SEE IS WHAT COUNTS.
```

SHADED makes game worlds readable. Rain darkens stone. Snow remembers footsteps. Fire dries mud. Grass bends. Fog hides distance. Puddles collect. Smoke marks heat. Seasons change the world. The visible world becomes the rulebook.

Keep the exact layout, spacing, responsiveness, animations, video URLs, typography, liquid glass styling, section structure, crossfade behavior, card layout, icon structure, and technical implementation from the original design.

Do not change any video URL.
Do not redesign the page.
Only transform the branding, copywriting, navigation labels, CTA labels, stats, partner/chip text, card titles, tags, and body text into SHADED's visible world-logic workflow.

The visual tone should remain cinematic and polished, but the meaning should become cartoony, game-like, strange, cozy, and world-simulation focused.

Do not mention space travel, Mars, aerospace, voyages, rockets, product photography, catalogs, branding services, or corporate AI production.

---

# Tech stack (pinned, CDN-only)

```html
<script src="https://cdn.tailwindcss.com"></script>
<script src="https://unpkg.com/react@18.3.1/umd/react.development.js" integrity="sha384-hD6/rw4ppMLGNu3tX5cjIb+uRZ7UkRJ6BPkLpg4hAu/6onKUg4lLsHAs9EBPT82L" crossorigin="anonymous"></script>
<script src="https://unpkg.com/react-dom@18.3.1/umd/react-dom.development.js" integrity="sha384-u6aeetuaXnQ38mYT8rp6sbXaQe3NL9t+IBXmnYxwkUI2Hw4bsp2Wvmx4yRQF1uAm" crossorigin="anonymous"></script>
<script src="https://unpkg.com/@babel/standalone@7.29.0/babel.min.js" integrity="sha384-m08KidiNqLdpJqLq95G/LEi8Qvjl/xUYll3QILypMoQ65QorJ9Lvtp2RXYGBFj1y" crossorigin="anonymous"></script>
<script src="https://unpkg.com/framer-motion@11.11.17/dist/framer-motion.js"></script>
<script>window.Motion = window.FramerMotion;</script>
```

Body is bg: `#000`.

Page is a React app mounted on `#root`.

All components are `<script type="text/babel">` files exporting via `window.X = X`.

---

# Fonts

Google Fonts:

```text
family=Instrument+Serif:ital@0;1&family=Barlow:wght@300;400;500;600
```

Tailwind config adds:

- `font-heading` → `'Instrument Serif', serif` always italic in use
- `font-body` → `'Barlow', sans-serif`

Default border radius override:

```js
DEFAULT: "9999px"
```

so bare `rounded` becomes pill.

---

# Liquid-glass utilities

Use exact CSS in a `<style>` block.

Two variants:

- `.liquid-glass` subtle, for nav/chips/cards
- `.liquid-glass-strong` heavier blur, for primary CTA

```css
.liquid-glass {
  background: rgba(255,255,255,0.01);
  background-blend-mode: luminosity;
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border: none;
  box-shadow: inset 0 1px 1px rgba(255,255,255,0.1);
  position: relative;
  overflow: hidden;
}

.liquid-glass::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1.4px;
  background: linear-gradient(180deg,
    rgba(255,255,255,0.45) 0%,
    rgba(255,255,255,0.15) 20%,
    rgba(255,255,255,0) 40%,
    rgba(255,255,255,0) 60%,
    rgba(255,255,255,0.15) 80%,
    rgba(255,255,255,0.45) 100%);
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}

.liquid-glass-strong {
  background: rgba(255,255,255,0.01);
  background-blend-mode: luminosity;
  backdrop-filter: blur(50px);
  -webkit-backdrop-filter: blur(50px);
  border: none;
  box-shadow: 4px 4px 4px rgba(0,0,0,0.05), inset 0 1px 1px rgba(255,255,255,0.15);
  position: relative;
  overflow: hidden;
}

.liquid-glass-strong::before {
  content: "";
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1.4px;
  background: linear-gradient(180deg,
    rgba(255,255,255,0.5) 0%,
    rgba(255,255,255,0.2) 20%,
    rgba(255,255,255,0) 40%,
    rgba(255,255,255,0) 60%,
    rgba(255,255,255,0.2) 80%,
    rgba(255,255,255,0.5) 100%);
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}
```

---

# FadingVideo component

Custom JS crossfade, no CSS transitions.

Wraps a `<video autoPlay muted playsInline preload="auto">` starting at opacity: 0.

Behavior:

- `FADE_MS = 500`
- `FADE_OUT_LEAD = 0.55` seconds
- `fadeTo(target, duration)` uses `requestAnimationFrame`
- reads current opacity from `video.style.opacity` so each new fade resumes from wherever the last one left off
- each call cancels previous `requestAnimationFrame` id before starting
- on `loadeddata`: set opacity 0, `play()`, `fadeTo(1)`
- on `timeupdate`: if `fadingOutRef` not set and `duration - currentTime <= 0.55` and `> 0`, flip the ref and `fadeTo(0)`
- on `ended`: set opacity 0; after `setTimeout(100ms)`, reset `currentTime = 0`, `play()`, clear `fadingOutRef`, `fadeTo(1)`
- `loop` attribute is OFF
- cleanup on unmount: cancel rAF, remove listeners

---

# Section 1 — Hero

Full viewport, black bg.

Background video is 120% width/height, top-aligned, centered horizontally. Focal point is the top of frame.

Video URL:

```text
https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260418_080021_d598092b-c4c2-4e53-8e46-94cf9064cd50.mp4
```

Class:

```text
absolute left-1/2 top-0 -translate-x-1/2 object-cover object-top z-0
```

Style:

```js
{ width: "120%", height: "120%" }
```

No overlay.

`z-10` layer holds:

```text
Navbar → Hero content (flex-1, centered) → World Rule chips
```

---

## Navbar

Fixed top-4, px-8 / lg:px-16, z-50.

Left:

48×48 liquid-glass circle with italic serif lowercase:

```text
s
```

Use Instrument Serif.

Center desktop only:

liquid-glass pill, `px-1.5 py-1.5`, holding 5 text links:

- Home
- World Rules
- Weather
- Materials
- Run Test

Each:

- `px-3 py-2`
- `text-sm`
- `font-medium`
- `text-white/90`
- `font-body`

Followed by a white pill button:

```text
Run Simulation
```

with ArrowUpRight icon.

Button style:

- `bg-white`
- `text-black`
- `whitespace-nowrap`

Right:

48×48 invisible spacer to balance logo.

---

## Hero content

Centered, `pt-24 px-4`.

All animated with Framer Motion:

```js
initial: { filter: "blur(10px)", opacity: 0, y: 20 }
```

Use easeOut.

---

## Badge

Delay: 0.4s.

liquid-glass rounded-full pill.

Contains white pill chip:

```text
Visible Rule
```

Chip style:

- `bg-white`
- `text-black`
- `px-3 py-1`
- `text-xs`
- `font-semibold`

Badge text:

```text
Rain, snow, mud, fire, fog, and time become readable
```

Style:

- `text-sm`
- `text-white/90`
- `pr-3`

---

## Headline

BlurText component, word-by-word animation.

Text:

```text
What You See Is What Counts
```

Classes:

- `text-6xl md:text-7xl lg:text-[5.5rem]`
- `font-heading`
- `italic`
- `text-white`
- `leading-[0.8]`
- `max-w-2xl`
- `justify-center`
- `tracking-[-4px]`

---

## Subheading

Delay: 0.8s.

Classes:

- `mt-4`
- `text-sm md:text-base`
- `text-white`
- `max-w-2xl`
- `font-body`
- `font-light`
- `leading-tight`

Text:

```text
SHADED makes game worlds explain themselves. Surfaces do not merely look different — they remember weather, pressure, heat, time, and consequence. The shader is not decoration. It is readable world logic.
```

---

## CTAs

Delay: 1.1s.

Container:

- `flex items-center gap-6 mt-6`

Primary:

liquid-glass-strong rounded-full `px-5 py-2.5 text-sm font-medium text-white`

Text:

```text
Enter the Diorama
```

with ArrowUpRight icon (`h-5 w-5`).

Secondary bare text link:

```text
Watch the World Change
```

with Play icon (`h-4 w-4`, filled).

---

## Stats row

Delay: 1.3s.

Container:

- `flex items-stretch gap-4 mt-8`

Two liquid-glass cards:

- `p-5`
- `w-[220px]`
- `rounded-[1.25rem]`

Each card:

Top: white 28×28 outline SVG icon.

Card 1:
Use clock/weather-memory style icon.

Large number:

```text
40+
```

Label:

```text
Visible world systems
```

Card 2:
Use globe/layers style icon.

Large number:

```text
1 Rule
```

Label:

```text
Every effect must be seen
```

Large number styling:

- Instrument Serif italic white
- `text-4xl`
- `tracking-[-1px]`
- `leading-none`

Label styling:

- `text-xs`
- `text-white`
- `font-body`
- `font-light`
- `mt-2`

---

## World Rule chips

Bottom of hero, delay 1.4s.

Container:

- `flex flex-col items-center gap-4 pb-8`

liquid-glass rounded-full chip:

```text
Built for game worlds that explain themselves
```

Style:

- `px-3.5 py-1`
- `text-xs`
- `font-medium`
- `text-white`

Row of 5 names in Instrument Serif italic white:

```text
Rain · Mud · Snow · Fire · Fog
```

Style:

- `text-2xl md:text-3xl`
- `tracking-tight`
- `gap-12 md:gap-16`

---

# BlurText component

Word-by-word blur-in.

IntersectionObserver triggers on 10% visibility.

Splits text by spaces.

Each word is a `motion.span` with:

```js
initial: { filter: "blur(10px)", opacity: 0, y: 50 }
```

3-step keyframes:

```js
{ filter: "blur(5px)", opacity: 0.5, y: -5 }
{ filter: "blur(0px)", opacity: 1, y: 0 }
```

Duration:

```text
0.7
```

This is `stepDuration 0.35 × 2`.

Times:

```js
[0, 0.5, 1]
```

Ease:

```text
easeOut
```

Stagger:

```js
delay = (i * 100) / 1000 seconds
```

Style:

- `display: inline-block`
- `marginRight: 0.28em`

Do not use non-breaking spaces. Letter-spacing -4px eats nbsp.

Parent `<p>`:

- `display: flex`
- `flexWrap: wrap`
- `justifyContent: center`
- `rowGap: 0.1em`

---

# Section 2 — Capabilities

`min-h-screen`, black bg.

Background video full-bleed, no 120% scale.

Video URL:

```text
https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260418_094631_d30ab262-45ee-4b7d-99f3-5d5848c8ef13.mp4
```

Class:

```text
absolute inset-0 w-full h-full object-cover z-0
```

Same FadingVideo treatment.

No overlay.

---

## Content

Relative `z-10`.

Classes:

- `px-8 md:px-16 lg:px-20`
- `pt-24 pb-10`
- `flex flex-col min-h-screen`

---

## Header

`mb-auto`

Kicker:

```text
// Visible Systems
```

Classes:

- `text-sm`
- `font-body`
- `text-white/80`
- `mb-6`

Heading:

```text
World rules
that show
```

Use two lines with `<br/>`.

Classes:

- `font-heading`
- `italic`
- `text-white`
- `text-6xl md:text-7xl lg:text-[6rem]`
- `leading-[0.9]`
- `tracking-[-3px]`

---

## Three capability cards

Grid:

- `grid grid-cols-1 md:grid-cols-3`
- `gap-6`
- `mt-16`

Each card:

- `liquid-glass`
- `rounded-[1.25rem]`
- `p-6`
- `min-h-[360px]`
- `flex flex-col`

---

## Card top row

Each card top row:

- `flex items-start justify-between gap-4`

Left:

44×44 nested liquid-glass square:

- `rounded-[0.75rem]`

Contains white Material Icons SVG:

- `fill currentColor`
- `h-6 w-6`
- `text-white`

Use these paths exactly:

### Card 1 icon — Weather Memory

```text
M5 21q-.825 0-1.412-.587T3 19V5q0-.825.588-1.412T5 3h14q.825 0 1.413.588T21 5v14q0 .825-.587 1.413T19 21H5Zm1-4h12l-3.75-5-3 4L9 13l-3 4Z
```

### Card 2 icon — Material Truth

```text
M4 6.47 5.76 10H20v8H4V6.47M22 4h-4l2 4h-3l-2-4h-2l2 4h-3l-2-4H8l2 4H7L5 4H4c-1.1 0-1.99.89-1.99 2L2 18c0 1.1.9 2 2 2h16c1.1 0 2-.9 2-2V4Z
```

### Card 3 icon — Living Time

```text
M9 21c0 .55.45 1 1 1h4c.55 0 1-.45 1-1v-1H9v1Zm3-19C8.14 2 5 5.14 5 9c0 2.38 1.19 4.47 3 5.74V17c0 .55.45 1 1 1h6c.55 0 1-.45 1-1v-2.26c1.81-1.27 3-3.36 3-5.74 0-3.86-3.14-7-7-7Z
```

Right:

`flex flex-wrap justify-end gap-1.5 max-w-[70%]`

4 small liquid-glass pill tags:

- `rounded-full`
- `px-3 py-1`
- `text-[11px]`
- `text-white/90`
- `font-body`
- `whitespace-nowrap`

Card 1 tags:

```text
Wet Stone · Puddles · Footsteps · Drip Paths
```

Card 2 tags:

```text
Mud · Grass · Cloth · Rust
```

Card 3 tags:

```text
Seasons · Fog · Smoke · Decay
```

Middle:

`flex-1` spacer.

---

## Bottom of each card

`mt-6`

### Card 1

Title:

```text
Weather Memory
```

Body:

```text
Rain does not decorate the world. It changes it. Stone darkens, puddles gather in low places, footprints disturb mud and snow, and surfaces remember what happened.
```

### Card 2

Title:

```text
Material Truth
```

Body:

```text
Every surface has a visible state. Grass bends. Cloth soaks. Rust stains. Mud dries near fire. The shader is not polish — it is the world explaining itself.
```

### Card 3

Title:

```text
Living Time
```

Body:

```text
Time is visible. Leaves change, snow settles, fog rolls through streets, smoke marks fire, and abandoned places slowly become different without a quest marker saying so.
```

Title styling:

- `h3`
- `font-heading`
- `italic`
- `text-white`
- `text-3xl md:text-4xl`
- `tracking-[-1px]`
- `leading-none`

Body styling:

- `mt-3`
- `text-sm`
- `text-white/90`
- `font-body`
- `font-light`
- `leading-snug`
- `max-w-[32ch]`

---

# Icons

Inline lucide-style SVGs, currentColor stroke.

ArrowUpRight:

- 24×24
- `M7 17L17 7`
- `M7 7h10v10`
- strokeWidth 2
- round caps

Play:

- 24×24
- filled polygon `6 4 20 12 6 20 6 4`

---

# Notes

All text white.

No green.

No gradient backgrounds.

No CSS transitions on the videos. Fades must be `requestAnimationFrame` driven per the FadingVideo spec.

Videos are full-bleed with no dark overlay. Contrast comes from the liquid-glass chrome.

Framer Motion dev warnings about list keys can be suppressed with a `console.error` filter wrapper. They are benign.

The detailed prompt above captures every element, style, animation, video URL, and font needed to recreate the landing page exactly while transforming the content into SHADED.

---

# Content rules

Do not mention:

- space travel
- Mars
- aerospace
- voyage
- launch
- liftoff
- rockets
- planets
- product photography
- catalogues
- branding
- corporate AI
- photo realism
- ray tracing as marketing language

Instead communicate:

- shader-first world logic
- visible consequences
- weather memory
- material states
- readable game worlds
- environmental storytelling
- seasons
- fog
- smoke
- puddles
- footprints
- grass
- mud
- fire
- decay
- time
- player-readable systems

The site should feel like entering a magical cartoon diorama where physics, memory, and consequence are visible.

Core message:

```text
Shader systems are not decoration.
They are readable world logic.
```

Keep every animation, every video, every responsive behavior, every liquid glass effect, every spacing rule, every typography rule, every layout, every crossfade behavior, and every technical implementation exactly as described. Only transform the narrative, copywriting, navigation labels, CTA labels, stats, chips, tags, card titles, and card body text into SHADED's visible-world-rules workflow.
