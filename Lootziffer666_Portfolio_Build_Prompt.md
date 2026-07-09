# Lootziffer666 Portfolio Landing Page Build Prompt

Build a 3D / agentic creator portfolio landing page for **Lootziffer666** using React, TypeScript, Tailwind CSS, Framer Motion, and Lucide React.

The page has a dark theme (`#0C0C0C` background) with the font Kanit (Google Fonts, weights 300-900).

The page title is:

```text
Lootziffer666 -- Frictionless Toolsmith
```

This is not a classic 3D artist portfolio and not a corporate startup page. It is a personal workshop landing page for a non-technical worldbuilder who builds systems with AI, language, assets, shaders, and agents.

The page should present three main projects:

1. **WIZARD** — semantic asset production lead / AssetPilot
2. **SWIFT** — procedural sprite and render pipeline
3. **SHADED** — shader-first visible world rules

Keep the exact layout, spacing, responsiveness, image URLs, GIF URLs, typography, animations, sticky cards, marquee behavior, magnet effect, gradient button style, reusable component structure, and technical implementation described below.

Do not change any image URL.
Do not remove any GIF URL.
Do not redesign the page.
Only transform the branding, copywriting, navigation labels, service names, project names, project descriptions, button labels, and portfolio logic so the page becomes a Lootziffer666 / WIZARD / SWIFT / SHADED portfolio.

The tone should be dark, playful, strange, sharp, slightly cartoony, and workshop-like. It should feel like entering a personal game-production laboratory where vague ideas become visible systems.

Do not present Lootziffer666 as a traditional software engineer.
Do not say "I code".
Say: "I build systems with AI, language, assets, shaders, and agents."

Do not use fake client claims.
Do not use NFT, Web3, crypto, corporate agency, or generic startup language.

---

# GLOBAL STYLES

Background: `#0C0C0C` on `html`, `body`, `#root`, and the main wrapper.

Font family:

```text
'Kanit', sans-serif
```

Global reset:

```css
box-sizing: border-box;
margin: 0;
padding: 0;
```

CSS class `.hero-heading`:

Gradient text using:

```css
background: linear-gradient(180deg, #646973 0%, #BBCCD7 100%);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
```

Main wrapper has:

```js
overflowX: 'clip'
```

---

# SECTION ORDER

1. HeroSection
2. MarqueeSection
3. AboutSection
4. SystemsSection
5. ProjectsSection

---

# 1. HERO SECTION

Full viewport height (`h-screen`), flex column layout with `overflowX: clip`.

---

## Navbar

Horizontal nav bar with 4 links:

- About
- Systems
- Projects
- Contact

Evenly spaced with `justify-between`.

Text:

- color `#D7E2EA`
- `font-medium`
- uppercase
- tracking-wider
- sizes: `text-sm md:text-lg lg:text-[1.4rem]`
- padding: `px-6 md:px-10 pt-6 md:pt-8`
- hover: opacity 70% with 200ms transition

---

## Hero Heading

Massive h1 with text:

```text
Hi, i'm Lootz
```

Use lowercase `i`.

Uses `.hero-heading` gradient text class.

Style:

- `font-black`
- uppercase
- tracking-tight
- leading-none
- whitespace-nowrap
- w-full
- font sizes: `text-[14vw] sm:text-[15vw] md:text-[16vw] lg:text-[17.5vw]`
- margin top: `mt-6 sm:mt-4 md:-mt-5`
- wrapped in overflow-hidden container

---

## Bottom bar

Flexbox `justify-between items-end` with:

```text
pb-7 sm:pb-8 md:pb-10
```

Left paragraph text:

```text
a non-technical worldbuilder turning sentences, assets, shaders, and agents into playable systems
```

Style:

- color `#D7E2EA`
- `font-light`
- uppercase
- tracking-wide
- leading-snug
- font size: `clamp(0.75rem, 1.4vw, 1.5rem)`
- max-width: `max-w-[180px] sm:max-w-[240px] md:max-w-[300px]`

Right:

ContactButton component. Label:

```text
Enter Workshop
```

---

## Hero Portrait / Central Object

Centered absolutely.

Uses a Magnet component with mouse-following magnetic effect wrapping an image.

Keep this image URL exactly:

```text
https://shrug-person-78902957.figma.site/_components/v2/d24c01ad3a56fc65e942a1f501eb73db42d7cf9a/Rectangle_40443.81459862.png
```

Treat the image as a replaceable central artifact / avatar / workshop object.

Magnet settings:

- padding 150
- strength 3
- activeTransition `"transform 0.3s ease-out"`
- inactiveTransition `"transform 0.6s ease-in-out"`

Positioning:

- `absolute left-1/2 -translate-x-1/2 z-10`
- width: `w-[280px] sm:w-[360px] md:w-[440px] lg:w-[520px]`

On mobile:

- `top-1/2 -translate-y-1/2`

On sm+:

- `sm:top-auto sm:translate-y-0 sm:bottom-0`

---

## FadeIn animations

- Navbar fades in with delay 0, y -20.
- Heading: delay 0.15, y 40.
- Left text: delay 0.35, y 20.
- Contact button: delay 0.5, y 20.
- Portrait / central object: delay 0.6, y 30.

---

# 2. MARQUEE SECTION

Two rows of images that scroll horizontally based on page scroll position.

Background:

```text
#0C0C0C
```

Padding:

```text
pt-24 sm:pt-32 md:pt-40 pb-10
```

Use the following 21 GIF images from motionsites.ai exactly as provided.

Treat them as moving inspiration / project-surface tiles for a kinetic workshop portfolio. Do not alter the URLs.

```text
https://motionsites.ai/assets/hero-space-voyage-preview-eECLH3Yc.gif
https://motionsites.ai/assets/hero-codenest-preview-Cgppc2qV.gif
https://motionsites.ai/assets/hero-vex-ventures-preview-BczMFIiw.gif
https://motionsites.ai/assets/hero-stellar-ai-v2-preview-DjvxjG3C.gif
https://motionsites.ai/assets/hero-asme-preview-B_nGDnTP.gif
https://motionsites.ai/assets/hero-transform-data-preview-Cx5OU29N.gif
https://motionsites.ai/assets/hero-vitara-preview-Cjz2QYyU.gif
https://motionsites.ai/assets/hero-terra-preview-BFjrCr7T.gif
https://motionsites.ai/assets/hero-skyelite-preview-DHaZIgUv.gif
https://motionsites.ai/assets/hero-aethera-preview-DknSlcTa.gif
https://motionsites.ai/assets/hero-designpro-preview-D8c5_een.gif
https://motionsites.ai/assets/hero-stellar-ai-preview-D3HL6bw1.gif
https://motionsites.ai/assets/hero-xportfolio-preview-D4A8maiC.gif
https://motionsites.ai/assets/hero-orbit-web3-preview-BXt4OttD.gif
https://motionsites.ai/assets/hero-nexora-preview-cx5HmUgo.gif
https://motionsites.ai/assets/hero-evr-ventures-preview-DZxeVFEX.gif
https://motionsites.ai/assets/hero-planet-orbit-preview-DWAP8Z1P.gif
https://motionsites.ai/assets/hero-new-era-preview-CocuDUm9.gif
https://motionsites.ai/assets/hero-wealth-preview-B70idl_u.gif
https://motionsites.ai/assets/hero-luminex-preview-CxOP7ce6.gif
https://motionsites.ai/assets/hero-celestia-preview-0yO3jXO8.gif
```

Row 1:

First 11 images, tripled for seamless scrolling.

Moves RIGHT on scroll:

```js
translateX(offset - 200)
```

Row 2:

Remaining 10 images, tripled.

Moves LEFT on scroll:

```js
translateX(-(offset - 200))
```

Scroll offset calculated as:

```js
(window.scrollY - sectionTop + window.innerHeight) * 0.3
```

Each image tile:

- 420px x 270px
- `rounded-2xl`
- `object-cover`
- lazy loaded

Gap between tiles:

```text
gap-3
```

Gap between rows:

```text
gap-3
```

Uses:

```js
willChange: 'transform'
```

Scroll listener is passive.

---

# 3. ABOUT SECTION

Full-height centered section with:

- `min-h-screen`
- padding `px-5 sm:px-8 md:px-10 py-20`

Four decorative 3D images positioned absolutely in corners.

Keep every image URL exactly.

---

## Top-left image

Moon icon:

```text
https://shrug-person-78902957.figma.site/_components/v2/ebb2b8f25d8e24d5f0a5ca8af4c950de81aa2fd7/moon_icon.11395d36.png
```

Size:

```text
w-[120px] sm:w-[160px] md:w-[210px]
```

Position:

```text
top-[4%] left-[1%] sm:left-[2%] md:left-[4%]
```

FadeIn:

- delay 0.1
- x -80
- y 0
- duration 0.9

---

## Bottom-left image

3D object:

```text
https://shrug-person-78902957.figma.site/_components/v2/ebb2b8f25d8e24d5f0a5ca8af4c950de81aa2fd7/p59_1.4659672e.png
```

Size:

```text
w-[100px] sm:w-[140px] md:w-[180px]
```

Position:

```text
bottom-[8%] left-[3%] sm:left-[6%] md:left-[10%]
```

FadeIn:

- delay 0.25
- x -80
- y 0
- duration 0.9

---

## Top-right image

Lego icon:

```text
https://shrug-person-78902957.figma.site/_components/v2/ebb2b8f25d8e24d5f0a5ca8af4c950de81aa2fd7/lego_icon-1.703bb594.png
```

Size:

```text
w-[120px] sm:w-[160px] md:w-[210px]
```

Position:

```text
top-[4%] right-[1%] sm:right-[2%] md:right-[4%]
```

FadeIn:

- delay 0.15
- x 80
- y 0
- duration 0.9

---

## Bottom-right image

3D group:

```text
https://shrug-person-78902957.figma.site/_components/v2/ebb2b8f25d8e24d5f0a5ca8af4c950de81aa2fd7/Group_134-1.2e04f3ce.png
```

Size:

```text
w-[130px] sm:w-[170px] md:w-[220px]
```

Position:

```text
bottom-[8%] right-[3%] sm:right-[6%] md:right-[10%]
```

FadeIn:

- delay 0.3
- x 80
- y 0
- duration 0.9

---

## Heading

Text:

```text
About me
```

Use `.hero-heading` gradient text.

Style:

- `font-black`
- uppercase
- leading-none
- tracking-tight
- centered
- font size: `clamp(3rem, 12vw, 160px)`

FadeIn:

- delay 0
- y 40

---

## Animated paragraph

Uses character-by-character scroll-driven opacity animation.

Text:

```text
I don't build apps because I love code. I build systems because thoughts need shapes. WIZARD turns ideas into asset kits. SWIFT turns models into usable game sprites. SHADED turns visible changes into world rules. The code is only the machinery. The point is less friction between imagination and something you can actually play.
```

Style:

- color `#D7E2EA`
- `font-medium`
- centered
- leading-relaxed
- max-w-[680px]
- font size `clamp(1rem, 2vw, 1.35rem)`

Each character animates from opacity 0.2 to 1 based on scroll progress, with scroll offset:

```js
['start 0.8', 'end 0.2']
```

Contact button below the text block.

Gap between heading/text:

```text
gap-10 sm:gap-14 md:gap-16
```

Gap between text block and button:

```text
gap-16 sm:gap-20 md:gap-24
```

ContactButton label:

```text
Ask what I'm building
```

---

# 4. SYSTEMS SECTION

Use the same structure and styling as the original ServicesSection, but rename it to SystemsSection.

White background:

```text
#FFFFFF
```

Top corners:

```text
rounded-t-[40px] sm:rounded-t-[50px] md:rounded-t-[60px]
```

Padding:

```text
px-5 sm:px-8 md:px-10 py-20 sm:py-24 md:py-32
```

Heading:

```text
Systems
```

Style:

- color `#0C0C0C`
- `font-black`
- uppercase
- centered
- font size `clamp(3rem, 12vw, 160px)`
- margin bottom `mb-16 sm:mb-20 md:mb-28`

Create 5 system items in a vertical list, max-w-5xl, centered.

---

## 01 — WIZARD

Description:

```text
Semantic production lead for game assets. Describe a game idea and WIZARD translates it into environments, characters, props, templates, gaps, and a usable starter kit.
```

---

## 02 — SWIFT

Description:

```text
Procedural sprite and render pipeline. Turns 3D models, sketches, or visual ideas into clean previews, sprite sheets, turntables, masks, and game-ready output.
```

---

## 03 — SHADED

Description:

```text
Shader-first world logic. Rain, snow, mud, fire, grass, fog, decay, and material states become visible rules instead of decorative effects.
```

---

## 04 — CUE / Evidence

Description:

```text
Agent verification layer. Claims require evidence, screenshots, logs, and repeatable checks before a system is allowed to call something done.
```

---

## 05 — mini-me / Language

Description:

```text
A prompt-shaped writing engine distilled from my own texts. It turns strange inputs into internally consistent stories, pitches, and narrative systems.
```

---

Each item:

Horizontal layout with number on the left and name + description stacked vertically on the right.

Number:

- `font-black`
- font size `clamp(3rem, 10vw, 140px)`
- color `#0C0C0C`

Name:

- `font-medium`
- uppercase
- font size `clamp(1rem, 2.2vw, 2.1rem)`

Description:

- `font-light`
- leading-relaxed
- max-w-2xl
- font size `clamp(0.85rem, 1.6vw, 1.25rem)`
- opacity 0.6

Items separated by:

```css
1px solid rgba(12, 12, 12, 0.15)
```

Padding:

```text
py-8 sm:py-10 md:py-12
```

Staggered FadeIn:

```js
delay = i * 0.1
```

---

# 5. PROJECTS SECTION

Dark background:

```text
#0C0C0C
```

Rounded top corners:

```text
rounded-t-[40px] sm:rounded-t-[50px] md:rounded-t-[60px]
```

Pulled up with:

```text
-mt-10 sm:-mt-12 md:-mt-14
```

`z-10`.

Heading:

```text
Projects
```

Use `.hero-heading` gradient, same styling as other headings.

3 sticky-stacking project cards that scale down as you scroll past them using Framer Motion `useScroll` and `useTransform`.

Each card is sticky:

```text
top-24 md:top-32
```

inside an:

```text
h-[85vh]
```

container.

Scale calculation:

```js
targetScale = 1 - (totalCards - 1 - index) * 0.03
```

Each card offset by:

```js
top: `${index * 28}px`
```

Each card has:

- `rounded-[40px] sm:rounded-[50px] md:rounded-[60px]`
- `border-2 border-[#D7E2EA]`
- background `#0C0C0C`
- padding `p-4 sm:p-6 md:p-8`

---

## Card layout

Top row:

- Number, huge, same style as systems/services
- category label
- project name
- `LiveProjectButton` ghost button

Bottom row:

Two-column image grid.

Left column:

- 40% width
- 2 stacked images

Right column:

- 60% width
- 1 tall image

All images have heavy border radius:

```text
rounded-[40px] sm:rounded-[50px] md:rounded-[60px]
```

Left top image height:

```text
clamp(130px, 16vw, 230px)
```

Left bottom image height:

```text
clamp(160px, 22vw, 340px)
```

Use the provided image URLs exactly as listed below.

---

## Project 01 — WIZARD

Category:

```text
Asset Production Lead
```

Project name:

```text
WIZARD
```

Button label:

```text
Open WIZARD
```

Description concept:

```text
2470 indexed assets become searchable production intent.
```

Image meanings:

- asset grid
- starter kit result
- missing asset list

Keep these image URLs exactly:

Col1 image 1:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_055344_5eff02e0-87a5-41ce-b64f-eb08da8f33db.png&w=1280&q=85
```

Col1 image 2:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_055431_11d841fd-8b41-46a5-82e4-b04f2407a7d8.png&w=1280&q=85
```

Col2 image:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_055451_e317bf2d-28d4-48cc-86b0-6f72f25b6327.png&w=1280&q=85
```

---

## Project 02 — SWIFT

Category:

```text
Sprite Pipeline
```

Project name:

```text
SWIFT
```

Button label:

```text
Open SWIFT
```

Description concept:

```text
3D input becomes 2D game-ready output.
```

Image meanings:

- character turnaround
- sprite sheet
- render pass / mask preview

Keep these image URLs exactly:

Col1 image 1:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_055654_911201c5-36d9-4bc6-bac7-331adfce159f.png&w=1280&q=85
```

Col1 image 2:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_055723_5ceda0b8-d9c2-4665-b2e3-83ba19ba76d1.png&w=1280&q=85
```

Col2 image:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_055753_adc5dcbd-a8e6-49c0-b43a-9b030d835cea.png&w=1280&q=85
```

---

## Project 03 — SHADED

Category:

```text
Visible World Rules
```

Project name:

```text
SHADED
```

Button label:

```text
Open SHADED
```

Description concept:

```text
Shader systems turn world state into readable truth.
```

Image meanings:

- rain / puddles
- snow / footprints
- fire / fog / material change

Keep these image URLs exactly:

Col1 image 1:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_055759_963cfb0b-4bd1-4b0f-9d0a-09bd6cf95b2f.png&w=1280&q=85
```

Col1 image 2:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_060108_438f781a-9846-4dcc-89ab-c4e6cb830f5b.png&w=1280&q=85
```

Col2 image:

```text
https://images.higgs.ai/?default=1&output=webp&url=https%3A%2F%2Fd8j0ntlcm91z4.cloudfront.net%2Fuser_38xzZboKViGWJOttwIXH07lWA1P%2Fhf_20260412_055818_9d062121-ad7e-46b9-999a-1a6a692ef1ee.png&w=1280&q=85
```

---

# REUSABLE COMPONENTS

## ContactButton

Rounded-full pill button with gradient background:

```css
linear-gradient(123deg, #18011F 7%, #B600A8 37%, #7621B0 72%, #BE4C00 100%)
```

Inner box-shadow:

```css
0px 4px 4px rgba(181, 1, 167, 0.25),
4px 4px 12px #7721B1 inset
```

White 2px outline with -3px offset.

Text:

- white
- `font-medium`
- uppercase
- tracking-widest

Sizes:

```text
px-8 py-3 sm:px-10 sm:py-3.5 md:px-12 md:py-4
text-xs sm:text-sm md:text-base
```

Default label:

```text
Enter Workshop
```

---

## LiveProjectButton

Ghost/outline pill button.

Style:

- rounded-full
- border-2 `border-[#D7E2EA]`
- text color `#D7E2EA`
- `font-medium`
- uppercase
- tracking-widest
- sizes `px-8 py-3 sm:px-10 sm:py-3.5`
- text `text-sm sm:text-base`
- hover `bg-[#D7E2EA]/10`

Default label:

```text
Open Project
```

---

## FadeIn

Framer Motion wrapper using `whileInView` with:

```js
viewport={{ once: true, margin: "50px", amount: 0 }}
```

Accepts:

- delay
- duration default 0.7
- x default 0
- y default 30

Easing:

```js
[0.25, 0.1, 0.25, 1]
```

Uses `motion.create()` for dynamic element types.

---

## Magnet

Mouse-following magnetic hover effect.

Tracks mouse position relative to element center and applies `translate3d` transform divided by strength factor.

Activates when cursor is within padding distance of element edge.

Smooth transition in:

```text
0.3s ease-out
```

Smooth transition out:

```text
0.6s ease-in-out
```

Uses:

```js
willChange: 'transform'
```

---

## AnimatedText

Character-by-character scroll-reveal text animation.

Each character goes from opacity 0.2 to 1 based on its position in the text relative to scroll progress.

Uses Framer Motion `useScroll` targeting the paragraph element with offset:

```js
['start 0.8', 'end 0.2']
```

Each character uses invisible placeholder plus absolute positioned animated span.

---

# KEY DEPENDENCIES

```text
react, react-dom (^18.3.1)
framer-motion (^12.38.0)
lucide-react (^0.344.0)
tailwindcss (^3.4.1)
vite
typescript
```

---

# RESPONSIVE BREAKPOINTS

All sections use Tailwind's default breakpoints:

- `sm`: 640px
- `md`: 768px
- `lg`: 1024px

Use a mobile-first approach.

Use heavy `clamp()` for fluid typography.

The entire design scales gracefully from mobile to ultra-wide screens.

---

# Content rules

Do not present the page as a normal designer portfolio.

Do not use:

- fake client claims
- agency language
- NFT/Web3/crypto wording
- generic startup pitch language
- "I am a software engineer"
- "I code"

Instead communicate:

- system thinking
- frictionless creation
- game production tooling
- semantic asset search
- procedural sprite output
- shader-first readable worlds
- evidence-based agents
- language as a production interface
- ideas becoming testable systems

The page should communicate:

- Lootziffer666 thinks in systems.
- Lootziffer666 removes friction.
- Lootziffer666 makes ideas testable.
- WIZARD, SWIFT, and SHADED are parts of one agent-driven game production ecosystem.
- The code is machinery. The visible result is what counts.

Keep every animation, every image URL, every GIF URL, every responsive behavior, every marquee behavior, every magnet behavior, every card stacking behavior, every spacing rule, every typography rule, every layout, every component, and every technical implementation exactly as described. Only transform the narrative, labels, buttons, services, project names, and content into Lootziffer666's WIZARD / SWIFT / SHADED portfolio.
