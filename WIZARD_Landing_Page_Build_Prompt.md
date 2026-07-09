# WIZARD Landing Page Build Prompt

Create a landing page called **WIZARD** with 4 sections, using a dark magical production-studio theme. The page uses video backgrounds served from CloudFront, a liquid glass UI effect, and a specific color/font system. Recreate it exactly as described below.

WIZARD is an intelligent production assistant for game development. It translates game ideas into production-ready asset kits, semantic asset search results, missing asset reports, style matches, environment suggestions, character suggestions, prop suggestions, material suggestions, UI suggestions, VFX suggestions, audio suggestions, and template recommendations.

WIZARD is not an asset browser. It understands production intent.

A user describes a game idea, and WIZARD responds with usable production direction.

The overall feeling should be:

- an archive
- a spellbook
- a production room
- an AI game master
- an intelligent workshop

The page should communicate intelligent production, semantic search, game development, asset orchestration, production planning, playable prototypes, atmosphere, environmental storytelling, and rapid iteration.

Do not mention NFTs, blockchain, wallets, minting, ownership, crypto, marketplaces, tokens, rarity, or NFT collections anywhere.

Keep every video URL exactly as provided. Treat all videos as atmospheric background footage.

---

## FONTS (Google Fonts)

Anton - Used for all headings and navigation text (aliased as font-grotesk in Tailwind)

Condiment - A cursive script used for accent/overlay text (aliased as font-condiment in Tailwind)

System monospace font (font-mono) - Used for body/description paragraphs

Load via Google Fonts in index.html:

https://fonts.googleapis.com/css2?family=Anton&family=Condiment&display=swap

---

## COLOR SYSTEM (Tailwind config)

Background: #010828 (deep dark navy blue)

cream: #EFF4FF (off-white, used for all text)

neon: #6FFF00 (bright green, used for accent cursive text and underline bars)

---

## LIQUID GLASS CSS EFFECT

Applied via a `.liquid-glass` class. This is used on the navbar, social icon buttons, production kit cards, and card overlays:

```css
.liquid-glass {
  background: rgba(255, 255, 255, 0.01);
  background-blend-mode: luminosity;
  backdrop-filter: blur(4px);
  -webkit-backdrop-filter: blur(4px);
  border: none;
  box-shadow: inset 0 1px 1px rgba(255, 255, 255, 0.1);
  position: relative;
  overflow: hidden;
}
.liquid-glass::before {
  content: '';
  position: absolute;
  inset: 0;
  border-radius: inherit;
  padding: 1.4px;
  background: linear-gradient(180deg,
    rgba(255,255,255,0.45) 0%, rgba(255,255,255,0.15) 20%,
    rgba(255,255,255,0) 40%, rgba(255,255,255,0) 60%,
    rgba(255,255,255,0.15) 80%, rgba(255,255,255,0.45) 100%);
  -webkit-mask: linear-gradient(#fff 0 0) content-box, linear-gradient(#fff 0 0);
  -webkit-mask-composite: xor;
  mask-composite: exclude;
  pointer-events: none;
}
```

---

## TEXTURE OVERLAY

A full-screen fixed texture overlay sits on top of everything (z-50, pointer-events-none). It uses a `/texture.png` image with `mix-blend-mode: lighten` at opacity: 0.6, covering the entire viewport with `background-size: cover`.

---

# SECTION 1: HERO (Full viewport)

Background: Full-bleed looping muted autoplaying video covering the entire section with `object-cover`.

Video URL:

https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260331_045634_e1c98c76-1265-4f5c-882a-4276f2080894.mp4

Container: `max-w-[1831px]` centered with responsive horizontal padding.

Section has `rounded-b-[32px]` bottom corners, clipping the video.

---

## Header

Left: `WIZARD` logo text in Anton, 16px, uppercase.

Center: Navigation bar with liquid-glass effect, `rounded-[28px]`, `px-[52px] py-[24px]`.

Contains 5 links:

- Overview
- Starter Kits
- Search
- Production
- Contact

Each link is Anton 13px uppercase. Links have `hover:text-neon` transition. Nav is hidden on mobile (`hidden lg:block`).

---

## Hero Content

Large heading in Anton font, responsive sizing: 40px mobile / 60px sm / 75px md / 90px lg. Uppercase. `leading-[1.05]` mobile, `leading-[1]` tablet+. Max width 780px on desktop, offset with `lg:ml-32`.

Text reads:

```text
Turn ideas
into playable starter kits
```

Overlaid cursive accent text `Asset spellbook` in Condiment font (24px-48px responsive), positioned absolute to the right side of the heading, slightly rotated (`-rotate-1`), in neon green (`text-neon`), with `mix-blend-exclusion` and `opacity-90`.

Add supporting copy in monospace, uppercase, cream color, compact and production-focused:

```text
Describe a game idea.
WIZARD searches thousands of production assets,
understands atmosphere,
builds starter kits,
and tells you what is still missing.
```

---

## Social Icons (Desktop)

3 square buttons (56x56px) stacked vertically in top-right corner, each with liquid-glass and `rounded-[1rem]`.

Icons: Mail, Twitter, Github from `lucide-react` (20x20px). `hover:bg-white/10` transition.

---

## Social Icons (Mobile)

Same 3 buttons but centered horizontally below the heading, shown only below `lg` breakpoint.

---

# SECTION 2: ABOUT / INTRO (Full viewport)

Background: Full-bleed looping muted autoplaying video with `object-cover`.

Video URL:

https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260331_151551_992053d1-3d3e-4b8c-abac-45f22158f411.mp4

Container: Same `max-w-[1831px]` centered, with generous vertical padding (64px-96px responsive).

---

## Top Row

Flex row on desktop, column on mobile.

Left: Heading in Anton, responsive 32px-60px, uppercase:

```text
Hello!
I'm wizard
```

With an overlaid `WIZARD` in Condiment cursive, neon green, `mix-blend-exclusion`, 36px-68px responsive, positioned absolute at bottom-right of heading, slightly rotated.

Right: Short paragraph in monospace 14px-16px, uppercase, cream color, max-width 266px:

```text
An intelligent production lead for game creators. Describe a world, mood, genre, or prototype, and WIZARD turns it into assets, kits, gaps, and next steps.
```

---

## Bottom Row

Flex row, space-between.

Two columns left and right, each containing 2 identical decorative paragraphs. Use the same monospace style as above but at opacity-10, nearly invisible and decorative. Right column hidden below `lg`. On mobile, text uses `text-[#010828]` dark so it is effectively invisible against the video.

Decorative paragraph text:

```text
SEMANTIC SEARCH. STARTER KITS. PRODUCTION BRIEFS. MISSING ASSETS. ENVIRONMENTS. CHARACTERS. PROPS. MATERIALS. TEMPLATES. UI. VFX. AUDIO.
```

---

# SECTION 3: PRODUCTION KIT GRID

Background: Solid `#010828` with no video.

Container: Same `max-w-[1831px]` centered.

---

## Header Row

Left: Heading in Anton, 32px-60px responsive, uppercase:

```text
Collection of
  [indented] Game worlds
```

Where `Game` is in Condiment cursive neon green, and `worlds` is in Anton. The second line is indented with `ml-12 / ml-24 / ml-32` responsive.

Right: A button reading:

```text
EXPLORE
ALL
KITS
```

`EXPLORE` is large (32px-60px), `ALL` and `KITS` are stacked smaller (20px-36px) next to it. Below the text is a neon green bar (`bg-neon`, height 6px-10px responsive, full width of button).

---

## Production Kit Card Grid

3-column grid on desktop (`lg:grid-cols-3`), 2 on tablet, 1 on mobile. Gap 24px.

Each card: liquid-glass container with `rounded-[32px]`, padding 18px, `hover:bg-white/10` transition.

Inside each card: a square video container (`pb-[100%]` aspect ratio trick) with `rounded-[24px]` overflow hidden.

Video URLs:

https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260331_053923_22c0a6a5-313c-474c-85ff-3b50d25e944a.mp4 (Match Score: 9.2/10)

https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260331_054411_511c1b7a-fb2f-42ef-bf6c-32c0b1a06e79.mp4 (Match Score: 8.9/10)

https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260331_055427_ac7035b5-9f3b-4289-86fc-941b2432317d.mp4 (Match Score: 9.4/10)

Each card has an overlay bar at the bottom: a liquid-glass bar with `rounded-[20px]`, `px-5 py-4`, showing `MATCH SCORE:` label (11px, cream/70% opacity) and score value (16px). On the right side of the bar is a circular purple gradient button (48x48px, `bg-gradient-to-br from-[#b724ff] to-[#7c3aed]`) with a right-arrow chevron SVG inside, with `shadow-lg shadow-purple-500/50` and `hover:scale-110` transition.

---

## Card Content

### Card 1

Title:

```text
DESERT SETTLEMENT
```

Category:

```text
Environment
```

Bottom label:

```text
MATCH SCORE:
9.2 / 10
```

Reason:

```text
Warm lighting,
explorable streets,
dust,
small-scale storytelling.
```

---

### Card 2

Title:

```text
SCRAP WORKSHOP
```

Category:

```text
Props
```

Bottom label:

```text
MATCH SCORE:
8.9 / 10
```

Reason:

```text
Improvised technology,
crafting,
mechanical storytelling.
```

---

### Card 3

Title:

```text
COOP STARTER KIT
```

Category:

```text
Template
```

Bottom label:

```text
MATCH SCORE:
9.4 / 10
```

Reason:

```text
Playable immediately.

Characters,
environment,
UI,
props,
and production direction already connected.
```

Keep every card layout, overlay, glass panel, button, and animation unchanged.

---

# SECTION 4: CTA / FINAL SECTION

Background: Full-width video, NOT `object-cover`, instead `w-full h-auto block` so it displays at native aspect ratio.

Video URL:

https://d8j0ntlcm91z4.cloudfront.net/user_38xzZboKViGWJOttwIXH07lWA1P/hf_20260331_055729_72d66327-b59e-4ae9-bb70-de6ccb5ecdb0.mp4

---

## Text Content

Positioned absolute over the video.

Right-aligned block, offset with `lg:pr-[20%] lg:pl-[15%]`.

Small `Start here` text in Condiment cursive, neon green, `mix-blend-exclusion`, positioned absolute at top-left of the heading block. Sizes: 17px-68px responsive.

Heading in Anton, responsive 16px-60px, uppercase:

```text
DESCRIBE
YOUR
WORLD.

LET WIZARD
BUILD THE
FIRST STEP.
```

`DESCRIBE YOUR WORLD.` has extra bottom margin (`mb-4` to `mb-12` responsive) before the remaining lines.

Add supporting CTA feeling:

```text
YOUR FIRST PLAYABLE IDEA
STARTS HERE.
```

Keep the same heading hierarchy and visual positioning as the original final section.

---

## Social Icons (Bottom-left, absolute positioned)

Positioned at `left-[8%]`, `bottom-[12%]` to `bottom-[20%]` with responsive breakpoints.

A vertical liquid-glass container with `rounded-[0.5rem]` to `rounded-[1.25rem]` responsive, containing 3 stacked icon buttons:

- Mail
- Twitter
- Github

Buttons have responsive widths using viewport units and rem values, for example `w-[14vw] sm:w-[14.375rem] md:w-[10.78125rem] lg:w-[16.77rem]`, and similar responsive heights.

Buttons are separated by `border-b border-white/10` dividers except the last one.

---

# KEY TECHNICAL DETAILS

Framework: React + TypeScript + Vite + Tailwind CSS.

Icons: `lucide-react` (Mail, Twitter, Github).

No additional packages needed beyond what Vite + React + Tailwind provides.

All videos: `autoPlay loop muted playsInline` attributes.

Responsive: Mobile-first with `sm:`, `md:`, `lg:` breakpoints throughout.

Max content width: `1831px` across all sections.

All text is uppercase except the Condiment cursive accents which are normal-case.

Keep every animation, every video, every responsive behavior, every liquid glass effect, every spacing rule, every typography rule, every layout, and every technical implementation exactly as described. Only transform the narrative, copywriting, navigation labels, and card content into WIZARD's production workflow.
