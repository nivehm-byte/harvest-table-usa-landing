# Website build playbook

**What this is.** Everything learned building nivehmarnitz.com v2 (Aug–Sep 2026),
turned into a method for future website builds. Copy this file into the root of
every new site project as its README. Read it before the first line of code.

**How to read it.** Sections 1–3 are the *order of work*: do not skip ahead.
Sections 4–15 are the *craft*: reference them while building. Section 16 is the
*launch gate*. Section 17 is the *bug index*: problems that looked fine and were
wrong, so they never have to be found twice.

Worked examples from nivehmarnitz.com are marked **▸ NM:**. They are there to
show a rule in use. They are not values to copy into another brand.

---

## Contents
1. [The order of work](#1--the-order-of-work)
2. [The brief and the definition of done](#2--the-brief-and-the-definition-of-done)
3. [Decisions: lock, log, and record the overrules](#3--decisions-lock-log-and-record-the-overrules)
4. [Inspiration: read references as evidence](#4--inspiration-read-references-as-evidence)
5. [Mimicking a site by analysis: measure, don't eyeball](#5--mimicking-a-site-by-analysis-measure-dont-eyeball)
6. [Building from screenshots](#6--building-from-screenshots)
7. [The wireframe: function first](#7--the-wireframe-function-first)
8. [Project structure and asset files](#8--project-structure-and-asset-files)
9. [Design tokens: colour, type, space, shape, motion](#9--design-tokens-colour-type-space-shape-motion)
10. [Layout, containers and flow](#10--layout-containers-and-flow)
11. [Mobile and responsiveness](#11--mobile-and-responsiveness)
12. [Components: patterns that worked](#12--components-patterns-that-worked)
13. [Motion](#13--motion)
14. [Accessibility](#14--accessibility)
15. [Performance, metadata and sharing](#15--performance-metadata-and-sharing)
16. [Verification, tooling and the launch gate](#16--verification-tooling-and-the-launch-gate)
17. [Bug index](#17--bug-index)

---

## 1 · The order of work

v1 of nivehmarnitz.com never launched. Its positioning changed mid-build, the copy
arrived after the layout and broke it, and the type system was applied after most
of the page existed. **Decisions were made downstream of a build instead of
upstream of a brand.** v2 shipped because it ran the other way.

**The rule: no step starts until the step above it is locked and logged.**

| # | Step | Output | Why it is here |
|---|---|---|---|
| 0 | **Evidence** | Real demand, the alternatives the buyer compares you to, capacity maths | A position you work out from evidence holds up. One you simply assert doesn't |
| 1 | **Position, services, pricing** | Positioning line, offer shape, and **the definition of "done"** | v1 had no launch bar, so it never launched |
| 2 | **Inspiration** | Named references, what is borrowed from each and why | Adjectives are not direction |
| 3 | **Voice, persona, look and feel** | Voice rules, **imagery art direction**, **motion principles** | Imagery and motion need room designed for them |
| 4 | **Visual identity** | Palette with roles, type scale, grid, mark, component inventory, **a not-building list** | |
| A | *Parallel:* **Proof inventory** | Every publishable number, name, quote, before/after | **Nothing goes on the site that is not in it** |
| B | *Parallel:* **Photography** | Booked shoot with a shot list | Longest lead time in the project |
| C | *Parallel:* **Infrastructure** | Domain, mailbox, booking link, hosting, analytics | This is what killed v1's launch |
| 5 | **Messaging platform** | One-line answer, three provable claims, objections + answers, refused words | The layer v1 skipped |
| 6 | **Wireframe** | Greyscale structure with **real copy** | See §7 |
| 7 | **Visual design** | The styled page | Built on locked copy and locked tokens |
| 8 | **Animation** | The motion vocabulary, implemented | |
| 9 | **Technical bar** | 360px responsive · a11y · reduced motion · Lighthouse 90+ | See §14–16 |
| 10 | **Social system** | Post templates, profile kit | Can run from Step 4 onward |
| 11 | **Post-click experience** | Booking → call → proposal → agreement → invoice | If the site produces calls, an unstructured call wastes them |

**Start the parallel tracks on day one.** Testimonials take five minutes to ask for
and two weeks to arrive. Mailboxes and booking tools have setup lead time. The
photography edit ran two weeks longer than planned. None of them are build tasks,
and no amount of build work substitutes for them.

**Design to the proof you have, not the proof you want.** v1 had twenty
`[CONTENT NEEDED]` markers and one verifiable case study. Launch was blocked on
content that did not exist.

---

## 2 · The brief and the definition of done

Write the brief in the client's own words, then derive what it forces.

▸ **NM:** *"A 'check me out.' It validates experience and showcases work,
complementary to word of mouth. Impactful, but not overwhelming."* From that:

- **Validation, not discovery.** Visitors arrive warm from a referral or a LinkedIn
  post. The page confirms; it does not persuade from cold. → short, proof-dense,
  fast to scan, **one obvious next action.**
- **Not a destination.** No loader, no cinematic build-up, no page per project. The
  acquisition channel (LinkedIn) does the discovery; the site is the reference.
- **A tie-breaker phrase.** "Impactful but not overwhelming" settled every design
  argument: when in doubt, remove. Find the equivalent phrase in every brief and
  name it as the tie-breaker.
- **Style and function must live together.** Neither is allowed to win.

**Define "done" before building.** A minimum launch bar in writing: which sections,
which proof, which links must resolve, which scores must hold. Everything past the
bar is v2 of the site.

---

## 3 · Decisions: lock, log, and record the overrules

Keep three files at the project root:

| File | Job |
|---|---|
| `CLAUDE.md` | Auto-loaded context: the brief, the locked rules, the file map. Short |
| `PLAN.md` | The steps, their status, and the **lock log**: a table of every decision, dated, with its reason |
| `HANDOFF.md` | Where things stand *today* and what the next session does first. Written at the end of every session |

**Lock log rules**

- One row per decision: date · what was locked · why. Reopening a locked decision is
  a deliberate act with a recorded reason, never drift.
- **The decision-recording rule.** When the client chooses against the analysis, log
  it as **"chosen against the recommendation"** and leave the unrebutted argument
  standing. Do not rewrite the analysis to agree. An analysis that *loses* an
  argument gets updated. One that is simply *overruled* stays on the record. (This
  exists because three mutually exclusive colour decisions were once each written
  up as "the best answer", which made the analysis worthless as a check.)
- **Revise rules that nobody follows.** A rule overridden four times no longer
  describes the site, and a rule nobody follows makes the rest of the list
  unenforceable. Re-derive it from an audit of what is actually built, then
  enforce the new version.
- **Log measurements, not impressions.** "Card 479 → 448px at 1440×900" is a
  decision record. "Looks better" is not.
- **Archive, don't delete.** Rejected sections go to `site/archive/YYYY-MM-DD-name/`
  with a line saying why. Designs come back more often than you'd think.

---

## 4 · Inspiration: read references as evidence

1. **Collect real references**: websites, social posts, photography, palettes.
   Aim for ~20–30, and cover *every channel the brand will live in*, not just the
   site.
2. **Count the devices, don't describe the mood.** Go through every image and list
   the recurring moves, ranked by how often they appear.
   ▸ **NM:** display serif with one word in italic (8+ instances) · big serif
   numerals as proof (all three saved sites) · small dot + uppercase eyebrow ·
   ruled rows for lists · giant footer wordmark · grain · one saturated pop against
   a muted ground.
3. **Let the evidence overrule the old build.** v1 set everything in Ultralight 200.
   All 26 references used real-weight serif display. The references won.
4. **Spot template tells.** Two of the three saved sites were Framer templates.
   Cards, pill buttons and drop-shadowed panels are the tell, and going on a
   *not-building list* is what stops the site looking like a template.
5. **Name the two aesthetics.** A reference folder often holds two directions that
   don't merge on their own (NM: film-editorial *style* vs agency-structure
   *function*). Say which one owns what, or the build flips between them.
6. **Note the gaps.** NM's folder had no mobile screenshots. Anything the references
   don't cover is a decision you'll make without evidence, so flag it.
7. **Write the direction as one paragraph** and state, for each reference, what is
   borrowed and why.

---

## 5 · Mimicking a site by analysis: measure, don't eyeball

The best way to learn from a site you admire is to **measure its system**: its
spacing scale, gutter, measure, type ratios and mechanics. Then **translate** it
into your own palette, faces and scale. Borrow the architecture. Never lift its
copy, imagery, logos or brand identity.

### 5.1 · The procedure

1. **Open the reference in the browser at 1440, 1024 and 375 wide.** Most systems
   change at ~1024 and ~768.
2. **Run the measurement snippets below** in the console. Record the numbers.
3. **Write a spec** (e.g. `strategy/layout-system.md`) with *two columns*: the
   reference's measurement and your translated value. Keeping the source figure
   lets you tune on purpose later.
4. **Build the section in your tokens**, then re-measure your build against the spec.
5. **Record the deliberate divergences**, and say why for each.

### 5.2 · Measurement snippets (paste into the console)

```js
// One element: box, type and paint
const m = (sel) => { const el = document.querySelector(sel), cs = getComputedStyle(el), r = el.getBoundingClientRect();
  return { w: r.width, h: r.height, left: r.left, top: r.top + scrollY,
    font: cs.fontFamily, size: cs.fontSize, weight: cs.fontWeight, lh: cs.lineHeight, ls: cs.letterSpacing,
    color: cs.color, bg: cs.backgroundColor, pad: cs.padding, margin: cs.margin, radius: cs.borderRadius, maxW: cs.maxWidth }; };
m('h1');

// Every section's vertical rhythm and ground colour
[...document.querySelectorAll('section, footer')].map(s => { const cs = getComputedStyle(s);
  return [s.className.slice(0,30), cs.paddingTop, cs.paddingBottom, cs.backgroundColor, Math.round(s.offsetHeight)]; });

// The content column: where does text actually start and stop?
[...document.querySelectorAll('h1,h2,p')].slice(0,12).map(e => { const r = e.getBoundingClientRect();
  return [e.tagName, Math.round(r.left), Math.round(r.width)]; });

// The type scale in use
[...new Set([...document.querySelectorAll('h1,h2,h3,p,a,li,span')].map(e => { const c = getComputedStyle(e);
  return `${c.fontSize}/${c.lineHeight} ${c.fontWeight} ${c.fontFamily.split(',')[0]}`; }))];

// Mechanics: is it really a scroll container? snapping? transforms?
[...document.querySelectorAll('*')].filter(e => { const c = getComputedStyle(e);
  return /auto|scroll/.test(c.overflowX) || c.scrollSnapType !== 'none' || c.willChange.includes('transform'); })
  .map(e => [e.className.toString().slice(0,40), getComputedStyle(e).overflowX, getComputedStyle(e).scrollSnapType]);
```

### 5.3 · What measuring found that eyeballing never would

▸ **NM:** these came from studying superside.com.

- **The gutter is the whole game.** 16px at 375 → 112px at 1440, content capped at
  1216px, copy held to a 600–720px measure. → `padding-inline: clamp(16px, 7.8vw, 112px)`.
- **Negative space does the grouping.** Section padding came from a small 8px-based
  vocabulary (88 · 96 · 128 · 160 · 208). Whitespace isn't just breathing room: it
  tells the reader which blocks belong together.
- **A "statement" is paragraph scale, not display scale.** Their centred statement
  was 32px / 1.25 in a 1064px box. Ours had been 66px. The smaller size is what
  makes it read calm instead of loud.
- **Their "carousel" was not a carousel.** No `overflow-x`, no `scroll-snap`. Cards
  were absolutely positioned with JS-recomputed `translateX` and a compositor layer
  each. Measured, then **not adopted**: too expensive against a 90+ Lighthouse floor.
- **Context-dependent numbers don't transfer.** Their 32% card width assumes a
  *ten*-card rail. With three cards it gave only 151–211px of travel. Ours became
  38vw capped at 620px. Before you copy a ratio, check the conditions it depends on.
- **References ship below AA.** Their captions sat at ~3.8:1. We hold 4.5:1+ on
  purpose, and the token comment says so.
- **Some of their gates are wrong.** They hid the cursor on a *viewport-width*
  query, so a touchscreen laptop at desktop width lost its pointer. Gate on
  `(hover: hover) and (pointer: fine)` instead.

### 5.4 · Porting components (React / Tailwind / GSAP) to vanilla

Components are often supplied as React + Tailwind + a motion library. **Port the
mechanic, reject the dependencies.** Every time on NM, the valuable part was one or
two lines:

| Supplied | What came across | What was rejected |
|---|---|---|
| `BrandScroller` (React/Tailwind) | `mask-image: linear-gradient(to right, transparent, #000 12%, #000 88%, transparent)` for the edge fade | React, Tailwind, react-icons |
| `LinkButton` | Underline rests at `scaleX(0)` from the right, grows from the left, `0.5s cubic-bezier(.62,.05,.01,.99)`, arrow rotates −45° | JS tap-toggle (done in CSS with a hover media query) |
| `FlowArt` (GSAP ScrollTrigger) | The idea only | GSAP, `pinSpacing:false` + `min-h-screen` (breaks when content height changes), rotating full-screen live text |
| MouseFollower cursor (Cuberto) | **One fixed-size disc, every state a `scale()` of it**; lag 0.12 lerp; skew only on enlarged states, capped at 0.15 | Animating width/height (layout properties) |
| Motion Primitives `TextEffect` | Per-word blur-in, `aria-hidden` words + `aria-label` on the parent | Per-character on long text (hundreds of simultaneous blur filters) |

Read the library's shipped CSS/JS for its real constants (`*.min.css`, `*.min.js`)
rather than guessing them.

---

## 6 · Building from screenshots

The v2 page was built **section by section, out of order**, from screenshots of
reference sections the client liked. It works if each screenshot goes through the
same checklist:

1. **Screenshot = composition, not values.** It tells you *what* (hierarchy,
   alignment, proportion). The system tells you *how* (tokens). Never sample
   colours or fonts off a screenshot.
2. **Ground**: light or dark, following the page's ground plan (§10.4).
3. **Gutter and measure**: the content wrapper; copy ≤ ~720px.
4. **Vertical**: the one section padding outside, the gap token inside.
5. **Type**: your faces at your scale. Emphasis via italic only.
6. **One idea per section**, with air around it. Left-aligned unless the
   screenshot argues otherwise.
7. **Check against the locks**: accent budget per viewport, not-building list, dot
   ceiling. If the reference breaks one, either adapt it (▸ **NM:** a white
   testimonial card with shadow and stars became a squared 8% tint strip with an
   italic quote) or log the exception.
8. **Responsive**: test at 360 / 768 / 1024 / 1440 before calling it built.
9. **Build unknowns as test pages first.** Put a standalone page in
   `site/archive/YYYY-MM-DD-tests/` with a live toggle between options (NM: accent
   colour, label face, packages layout). Promote the winner into the real page, and
   archive the rest.
10. **Build the slot, drop the asset in later.** Missing photography and video get a
    named slot (`--hero-photo`, `.av-media`) with a placeholder of the right
    proportions, so real media is a drop-in, not a rebuild.

---

## 7 · The wireframe: function first

▸ **NM:** the first Step 6 attempt was **rejected and deleted**. It was a styled
page under the wireframe's label, so the structural step had been skipped, not just
brought forward.

A wireframe is:

- **Greyscale, system font, boxes.** No brand type, no palette, no components.
- **Real copy from the messaging platform, never lorem.** A wireframe full of
  placeholder text produces a container the message doesn't fit.
- **Structure only:** page count, section order, hierarchy, the one next action,
  the paths through the page.
- **Annotated.** Put the reasoning in visible note blocks beside each section: why
  it's there, what it proves, what's open.
- **Placeholders labelled with shot-list number and aspect ratio**, not "image".
- **Gated.** Show it to 3–5 people who look like buyers before styling. Test copy
  and structure in the same conversation.

**Reading order is an argument.** Define before you prove. ▸ **NM:** the Argument
(which defines the two disciplines) sat after two sections of evidence, so visitors
saw proof of two things before being told what they were. Final flow: *claim →
definition → proof → measured proof → why this over the alternative → offer → who →
one action.*

---

## 8 · Project structure and asset files

```
project/
├── CLAUDE.md · PLAN.md · HANDOFF.md · README.md (this file)
├── strategy/                 # the locked foundation, numbered by step
│   ├── colour-system.md · typography.md · layout-system.md · mark-system.md
│   ├── proof-inventory.md · voice-guide.md · messaging-platform.md
├── assets/                   # canonical home for shared files
│   ├── tokens.css            # ONE source of design tokens
│   ├── fonts/                # licensed woff2 (never public)
│   ├── mark/                 # build script + generated svg/ and raster/
│   │   ├── build-marks.py
│   │   ├── og/og-card.html   # share image source, rendered to raster/
│   │   ├── svg/  raster/
│   └── placeholders/         # stand-in media, deleted before launch
├── site/                     # the build root that gets served
│   ├── index.html · wireframe.html · brand-guide.html
│   ├── assets -> ../assets   # symlink (deploy must dereference it)
│   └── archive/YYYY-MM-DD-*/ # rejected sections and test pages
├── templates/                # branded docs rendered locally (PDF/PNG)
└── .claude/launch.json · .claude/serve.js
```

### 8.1 · Fonts

- **Self-host woff2.** Serve only `woff2` to browsers. Keep `otf/ttf` in a
  subfolder for tooling (glyph extraction, headless rendering).
- **One `@font-face` per weight/style actually used.** Nothing else ships.
- **`font-display: swap`** on every face, with metric-similar fallbacks in the stack.
- **Preload only the faces that paint in the first viewport**, usually 2–3. Preload
  more and they compete for the same throttled bandwidth, which slows down the ones
  that matter. ▸ **NM:** the loader wordmark face, the hero lede face (Lighthouse's
  mobile LCP element) and the button/h1 face.
- **Every retired face is a byte saving.** ▸ **NM:** retiring the mono (labels
  became small caps in the sans) removed one file, 72KB, and one typographic voice.
  Delete its `@font-face` so it can never be fetched.
- **Licensing.** Licensed fonts never go to a public repo, a hosted design tool, or
  any domain the client doesn't own. The logo ships as **outlined vector paths** for
  this reason. Branded documents are rendered locally with headless Chrome, so only
  the PDF/PNG leaves the machine.

```css
@font-face{font-family:'Display';src:url('../assets/fonts/Display-Regular.woff2') format('woff2');font-weight:400;font-style:normal;font-display:swap}
@font-face{font-family:'Display';src:url('../assets/fonts/Display-Italic.woff2') format('woff2');font-weight:400;font-style:italic;font-display:swap}
@font-face{font-family:'Body';src:url('../assets/fonts/Body-Book.woff2') format('woff2');font-weight:400;font-style:normal;font-display:swap}
```

```html
<!-- only what the first viewport paints; crossorigin is required even same-origin -->
<link rel="preload" href="assets/fonts/Body-Book.woff2" as="font" type="font/woff2" crossorigin>
```

### 8.2 · The mark / logo asset set

Build the whole logo set **from one source path, by script**, so every variant
regenerates identically. ▸ **NM:** `assets/mark/build-marks.py` uses `fontTools` to
extract the italic `n` from the licensed OTF into one SVG path. It normalises it
into a 100×100 box, applies a 2% optical-centre nudge for the italic lean, and
writes 13 SVG variants plus the rasters.

The set to produce:

| File | Spec |
|---|---|
| `favicon.ico` | 16 / 32 / 48, each rendered at that size (not scaled from one) |
| `favicon-src.svg` | SVG favicon. Use a **filled shape** (tabs render square; hairlines vanish) |
| `apple-touch-icon.png` | 180×180, **opaque** background |
| `icon-192.png`, `icon-512.png` | Maskable, content inside the safe zone |
| `og-image.png` | 1200×630 (§15.4) |
| Social avatars | 400 and 800 square, per ground colour |
| Single-ink versions | For print, stamps, embossing |

Write the minimum sizes down after testing them (NM: disc 16px, ring 24px, bare
monogram 28px, clear space 0.3× diameter). **Below a minimum, switch variants.
Never thin the stroke to fit.** Knockouts use one `fill-rule="evenodd"` path.

---

## 9 · Design tokens: colour, type, space, shape, motion

**One `tokens.css`, imported everywhere** (site, brand guide, templates). Tokens
are named by *role*, and every token carries a comment saying what it is for.

▸ **NM:** the page kept its own inline copy of the tokens and `tokens.css` was
extracted afterwards. Start with the shared file on day one instead.

### 9.1 · Starter `tokens.css`

```css
:root{
  /* ---- colour: roles, not swatches ---- */
  --ground-dark:#00253D;  --ground-dark-2:#114B60;  --ground-dark-3:#001B2E;
  --ground-light:#F8F8F5; --surface:#FFFFFF;
  --accent:#C3FDB8;       /* the pop: see accent rules */
  --accent-press:#A7EE8C; /* hover/pressed only */
  /* tints of locked hues, never new hues */
  --muted:rgba(0,37,61,.68);           /* secondary text on light, 5.4:1 */
  --muted-dark:rgba(248,248,245,.72);  /* secondary text on dark */
  --rule:rgba(0,37,61,.16);  --rule-dark:rgba(248,248,245,.22);

  /* ---- type ---- */
  --display:'Display',Georgia,serif;
  --sans:'Sans','Helvetica Neue',Arial,sans-serif;     /* UI, labels, setup */
  --body:'Body','Helvetica Neue',Arial,sans-serif;     /* running copy */

  /* ---- space ---- */
  --gutter:clamp(16px,7.8vw,112px);   /* 16 @375 → 112 @1440 */
  --content:1216px;                   /* content column */
  --measure:700px;                    /* max line length for copy */
  --space-section:clamp(64px,8.9vw,128px);  /* ONE section padding, top = bottom */
  --space-gap:clamp(32px,5.6vw,80px);       /* heading → content */
  --grid-gap:16px;

  /* ---- shape: nested radius = inner + padding ---- */
  --radius:12px;  --btn-r:14px;  --btn-r-sm:10px;
  --card-r:20px;  --tray-pad:8px; /* tray radius = 20 + 8 = 28 */

  /* ---- motion ---- */
  --ease-out:cubic-bezier(.2,.7,.2,1);
  --ease-std:cubic-bezier(.4,0,.2,1);
  --ease-bloom:cubic-bezier(.16,1,.3,1);

  /* ---- elevation: name the uses, keep it to two ---- */
  --shadow-raised:0 18px 40px -18px rgba(0,27,46,.45);
  --shadow-menu:0 0 0 1px rgba(0,37,61,.08),0 18px 40px -18px rgba(0,27,46,.35);
}
```

### 9.2 · Colour

- **Roles before values.** Decide what does the legible work (NM: navy + off-white
  carry every default surface and all body copy). Everything else is seasoning.
- **Extend with tints and shades of the locked hues, never new hues.** Extra darks
  give a long dark page tonal movement instead of one flat colour.
- **Measure every contrast pair, and write the figure in the token comment.**
  4.5:1 for text, 3:1 for UI and focus indicators. Hold AA even where references
  don't.
- **Pastel accents vanish on light grounds.** ▸ **NM:** jade on off-white measures
  **1.09:1**. So the rule: accent *text* only on dark grounds; on light grounds the
  accent is a *filled shape* only, never text, never a hairline. That rule held in
  100% of the built page, and it is why the footer went navy.
- **An accent budget per viewport.** "At most two accent elements in one viewport,
  doing different jobs. Never three." List the roles the accent may take (primary
  CTA, a stop/full point, one italic phrase, a state dot, a quote mark), and audit by
  scrolling the page viewport by viewport.
- **Focus rings invert the ground**: dark on light, light on dark. The accent is
  never a focus ring if it fails 3:1.
- **Some ideas need something behind them to work.** Glassmorphism on a flat ground
  just looks like boxes: blurring a flat colour gives back the same flat colour.
  Glass needs a photograph behind it.
- **Grain / texture lives in the imagery, not the interface**, unless it's a
  deliberate brand call.

### 9.3 · Typography

- **Two or three voices, each with one job.** ▸ **NM:** serif display (headlines,
  figures, emphasis) · sans text cut (body) · sans medium small-caps (labels). A
  fourth voice (mono) was retired: *impactful, not overwhelming*.
- **Emphasis is italic, never bold.** The house move is a roman headline with a
  single italic run.
- **A serif floor.** High-contrast display serifs break up small and in social feeds.
  NM: 20px minimum, never for body copy.
- **Labels:** small all-caps, tracking 0.09–0.1em, 11px floor.
- **Numbers:** `font-variant-numeric: tabular-nums` wherever figures align or animate.
- **Fluid scale with `clamp(min, vw, max)`**, tuned so the max lands exactly on the
  1440 target. Display line-height 1.0–1.2; body 1.5–1.6.

| Role | Size (clamp) | Line | Tracking |
|---|---|---|---|
| Display | 48 → 104 | 0.98 | −0.01em |
| H1 | 34 → 60 | 1.0 | −0.01em |
| H2 | 26 → 40 | 1.05 | −0.01em |
| H3 | 20 → 26 | 1.2 | — |
| Stat | 44 → 88, tabular | 1.0 | −0.02em |
| Lead | 18 → 21 | 1.5 | — |
| Body | 16 → 19 | 1.6 | — |
| Label | 11–13, caps | — | 0.09–0.1em |

```css
.h1{font:400 clamp(34px,4.2vw,60px)/1.0 var(--display);letter-spacing:-.01em}
.body{font:400 clamp(16px,1.3vw,19px)/1.6 var(--body)}
.label{font:500 12px/1 var(--sans);text-transform:uppercase;letter-spacing:.1em}
```

- **Size wordmarks to fit, not to bleed.** Measure the string's width as a multiple
  of font-size (NM: 5.79×) and derive the clamp so it clears the content box at every
  width.
- **Italic headings: check the overhang.** Italic glyphs lean past their box; leave
  room or nudge optically.

### 9.4 · Space

- **One section padding, top = bottom, every section.** ▸ **NM:** an asymmetric
  208/88 rhythm picked up four exceptions and read lopsided on dark sections. It was
  replaced by one token (128 @1440, 64 on phones). Tune one value and every section
  follows.
- **Padding only does visible work at a colour change.** Two adjacent same-colour
  sections with full padding each read as a hole. When space has to give, take it
  from the invisible boundary, not the coloured one.
- **Name exceptions as tokens** (`--work-pad-top`) and read that same token wherever
  the value is used in a `calc()`, so the two can't drift apart.

### 9.5 · Shape

- **A radius scale with nesting maths.** Outer radius = inner radius + padding
  (NM: card 20 + tray pad 8 = tray 28). A mismatched nested radius is the most
  common "something looks off".
- **Buttons vs controls.** Buttons squared-soft (14px / 10px small); switch tracks
  and icon discs stay round, because they're controls, not buttons.

---

## 10 · Layout, containers and flow

### 10.1 · The shell

```css
.shell{padding-inline:var(--gutter)}                       /* full-bleed ground */
.content{max-width:var(--content);margin-inline:auto}      /* the column */
.measure{max-width:var(--measure)}                         /* copy blocks */
section{padding-block:var(--space-section)}
```

- Grounds are **full-bleed**; content is **capped**; copy is **measured**. Don't fill
  the gutters. The emptiness is doing a job.
- **Align the nav to the content column**, not the viewport: `max-width: calc(var(--content) + 2 * var(--gutter))`.
  ▸ **NM:** before this fix the mark sat 144px outside the content edge at 1728.
- **A two-column asymmetric grid, not 12 columns**, for editorial sites. Twelve
  columns invite the card grids a restrained system refuses. (The About bento is the
  exception where a 12-col grid earns its place.)
- **True centring in a three-part bar:** `grid-template-columns: 1fr auto 1fr`.
  With flex, the middle item centres in the *leftover* space (NM: nav links sat 38px
  off centre).
- **DOM order follows visual order**, so tab order matches what the eye does.

### 10.2 · Aligning rows across columns: subgrid

When two cards/columns must share baselines however their copy wraps, declare the
rows on the parent and have children adopt them:

```css
.panel{display:grid;grid-template-rows:auto auto 1fr;gap:0 24px;grid-auto-flow:column}
.item{display:grid;grid-row:span 3;grid-template-rows:subgrid}
```

▸ **NM:** without it, two lists started exactly one line apart, because one
description wrapped to one line and its neighbour to two. The bug was latent in the
other tab too, because both of its descriptions happened to be two lines. Subgrid
fixes the whole class of bug. The fallback is simply unaligned.

**Take decorations out of flow if they change row heights** (NM: a "Flagship" chip
pushed one card's text 11px lower than its neighbour's).

### 10.3 · Page flow

- **Fewer sections.** NM went 8 → 6 → 5 + footer. Each cut was "impactful, not
  overwhelming" in practice.
- **One next action**, repeated, never competing with a second one. Every CTA goes
  straight to the booking tool (new tab, with "(opens in a new tab)" for screen
  readers).
- **Modal vs a page per item: let content volume decide.** ~120 words per project
  reads complete in a modal and thin on its own page. Separate pages mean a fresh
  document, fonts and LCP per click, and each must hold 90+. For a validation site
  the SEO argument doesn't apply.
- **Give modals real URLs** (`pushState` on open, `popstate` closes). Then Back works
  on Android, items are linkable in a DM, and pages can be added server-side later.
- **Motion content: link out, don't embed** (§15.3).

### 10.4 · Ground rhythm

Plan the light/dark sequence of section grounds as its own decision, and redraw it
whenever sections move.

- Alternate grounds so sections separate without rules.
- Watch for **long runs of one ground**: ▸ **NM:** ~5 screens of off-white after one
  section was removed. It was fixed by bringing back a dark section, not by adding
  lines.
- A section with dark children (dark cards, dark tiles) is **forced light**. Two
  forced-light sections adjacent will collide.
- Hairlines: never *between* sections. Only where they carry meaning (under figures,
  the footer bar).

---

## 11 · Mobile and responsiveness

**Test widths: 360 · 375/390 · 768 · 1024 · 1440 · 1920.** 360 is the floor.

- **The gutter shrinks, type steps down, columns collapse to one.** Mobile section
  padding is roughly a third of desktop.
- **Gate hover effects on capability, not width:**
  ```css
  @media (hover:hover) and (pointer:fine){ /* custom cursor, hover reveals, bloom */ }
  @media (hover:none){ /* resting state visible: e.g. link underline shown */ }
  ```
  Width queries break touchscreen laptops and give phones hover states they can
  never trigger.
- **Tap targets ≥44×44**, on the button, not the icon. An icon can be 14px inside a
  44px hit area.
- **Stack order on mobile is a decision** (NM: the modal flips to caption-above-media).
- **Expensive effects off below desktop.** A full-viewport `backdrop-filter` is a GPU
  pass per frame. Below 1024, NM uses a solid backdrop instead (86% ink let the page
  read through on phones).
- **Shape changes with the viewport.** A frame that opens full-bleed on desktop opens
  to a **square** on phones (NM's Argument: side = content width, capped by screen
  height), and every derived gap is recalculated from the square.
- **Buttons don't inherit `font-size`.** Set `font: inherit` on buttons or
  em-sized children render at 12px.

**Horizontal-overflow check** (run at each width):

```js
[...document.querySelectorAll('body *')].filter(e => e.getBoundingClientRect().right > innerWidth + 1)
  .map(e => [e.tagName, e.className.toString().slice(0,40), Math.round(e.getBoundingClientRect().right)]);
document.documentElement.scrollWidth > innerWidth; // must be false
```

---

## 12 · Components: patterns that worked

**Keep a component inventory and a not-building list**, and write down *why* each
thing is on the list. ▸ **NM not-building:** cards (template tell) · pill buttons ·
drop-shadowed panels · accordions · comparison and pricing tables · a loader · logo
walls. Some came back at the client's request. Each return was logged, not quietly
absorbed.

### Buttons: two roles, tokens on the ground
- **Primary** and **secondary** as real classes (`.btn-primary`, `.btn-secondary`).
  New buttons need one class, nothing else.
- **Put the fill colour on the section ground, not on the button**
  (`--bloom-fill` / `--bloom-ink` set per ground). Change the ground and its buttons
  follow.
- No outline buttons. No fourth colour just for "secondary": if nothing in the
  palette works on both grounds, use the ground-inverse.
- **Origin-fill bloom:** the fill grows from the pointer's entry point, with
  diameter = 2 × distance to the furthest corner. Keyboard focus blooms from centre.

### Modal: native `<dialog>`
- `showModal()` gives you a focus trap, Escape, focus restore, top-layer stacking
  and `::backdrop` for free. Don't hand-build `role="dialog"` on a div.
- **The top layer paints above every z-index.** Anything that must show over the
  dialog (a custom cursor) has to be *moved into* the dialog on open, and back on
  close, *before* you clear the dialog's contents.
- Lock scroll, restore scroll position, and prefetch the modal's images on card
  hover/focus so opening never shows empty boxes.

### Carousel / rail
- Native scroll: `overflow-x:auto`, `padding-inline` to align card 1 with the grid.
- **Scroll-snap fights drag-to-scroll** when several cards are visible. `mandatory`
  springs short drags back; `proximity` does the same because Chrome's threshold is
  ~half the scrollport. Snap only when one item fills the view (NM keeps `mandatory`
  in the modal's image strip, where each image is full width).
- Drag-to-scroll with a **6px slop**: a drag past it swallows the click.
- A plain mouse wheel doesn't scroll horizontally. If you remove arrows/indices,
  add drag or the rail becomes unreachable.
- Partial cards bleeding off both edges says "there's more" without an instruction.
- **Auto-ticker:** clone the set (clones `aria-hidden`, untabbable), fold the
  position into one set's width for a seamless loop. Pause on hover, focus, touch,
  modal open, hidden tab and off-screen (WCAG 2.2.2), and turn it off under reduced
  motion.

### Marquee / name scroller
- Content-width tracks, cloned enough times to cover the widest screen (NM: 7 @1920,
  4 @360). A `min-width:100%` track with `space-around` makes the gap token do nothing.
- Edge fade via `mask-image`, not blur layers.
- Hold speed constant (px/s) when distance changes by recomputing duration.
- Names beat logos when you have few clients: three logos on a loop read as "only
  three clients".

### Nav
- Hide on scroll down, return on scroll up, on focus, and while the pointer sits in
  the top strip. Pin it open while the mobile menu is open.
- **Treat the pointer as state, not an event.** `scroll-behavior: smooth` fires
  scroll events for the whole of an anchor jump (28 measured in one move), which will
  undo a one-shot reveal.
- Hamburger: `aria-expanded` is the single source of truth. CSS draws the X from it,
  and `aria-label` stays constant. Rewriting `textContent` deletes the icon bars.
- `html{scroll-padding-top:<nav height>}` so anchor jumps clear a sticky nav.

### Digit reel (number odometer)
- Build from the **rendered text** (it carries ×, M, commas the data doesn't).
- Reels `aria-hidden`; the real value in a `.sr-only` span.
- Zero layout shift: reserve each column's width.
- No JS / reduced motion: the static number in the markup.

### Custom cursor
- Ride **alongside** the system cursor; don't hide it with `cursor:none`. Hiding it
  caused two "no cursor at all" bugs (before first mousemove; inside the modal) and
  overrides the visitor's OS cursor size/contrast settings.
- One fixed-size element, `pointer-events:none`, moved and scaled by `transform`
  only. States are scales, labels ("Expand", "Drag", "Watch ↗") appear at scale 1.
- Keep a list of dark containers inside light sections (`DARK`), or the cursor goes
  navy-on-navy. The same list fixes focus-ring colour.
- Set the right colour on first move with transitions off, or it flashes the
  default colour.

### Splitting text for animation
- `display:inline-block` spans **break kerning** (NM: +35px, 2.96%, on a 205px
  wordmark, enough to overflow). `display:inline` keeps kerning and still takes
  `filter: blur()`.

---

## 13 · Motion

**Motion delivers information. It never decorates.** If a motion can be removed and
nothing is lost, remove it.

- **Animate `transform`, `opacity`, `clip-path`, `filter` only.** Never width, height,
  top or left. To "grow" a frame, clip it (`clip-path: inset()`) rather than
  `scale()`, so media and type inside never resize.
- **Reveals:** a short rise and fade at most. No parallax.
- **One pinned / scroll-linked section per page, maximum**, and it must be
  scroll-*linked* (speed untouched, nothing intercepted), not scroll-*jacked*.
- **No loader** on a validation site. If one exists, run it once per session and skip
  it for reduced motion, no-JS and any storage error, decided in an inline `<head>`
  script before first paint.
- **`prefers-reduced-motion`**: every animation has a static end state. Smooth
  scrolling only under `no-preference`.
- **Scroll triggers: geometry read + throttle**, not IntersectionObserver alone and
  not `requestAnimationFrame`:
  - rAF is **paused in background tabs**. NM's v1 digit reel started inside a double
    rAF and a page opened in a background tab showed a column of zeros. Commit start
    states with a synchronous reflow instead (`el.offsetWidth`).
  - IntersectionObserver never fired in the preview tool (hidden visibility state),
    so behaviour built on it could not be verified.
  - Use a plain 80–120ms throttle, fire once, then remove the listener.
- **No motion libraries by default.** Vanilla JS was ~40 lines for the pinned frame.
  GSAP/ScrollTrigger/framer-motion cost bytes against the Lighthouse floor and break
  when content height changes. Revisit only for fixed-height, genuinely complex
  choreography.
- **Reuse one gesture.** NM's footer wordmark reveals with the loader's exact
  keyframes and tokens, so the page opens and closes on the same motion.

---

## 14 · Accessibility

The floor: **Lighthouse accessibility 100.** NM held it through every change.

- Semantic landmarks: `header`, `nav`, `main`, `section` with headings, `footer`.
  `lang` on `<html>` (NM: `en-ZA`).
- `:focus-visible` on every interactive element: 2px outline, 3px offset, colour
  inverting the ground. Re-check inside dark children of light sections.
- A control straddling two grounds gets a double ring (light inside, dark outside).
- `.sr-only` for real values behind animated text, for "(opens in a new tab)", and for
  full sentences behind split or chip-ified headings (`aria-label` on the heading).
  ```css
  .sr-only{position:absolute;width:1px;height:1px;padding:0;margin:-1px;overflow:hidden;clip:rect(0,0,0,0);white-space:nowrap;border:0}
  ```
- Real `<button>`s for actions, `<a>` for navigation. A whole-card hit area is a
  button with a stretched `::before`; inner links sit above it at a higher z-index.
- Tablists are real tablists (`role="tablist"`, `aria-selected`, arrow keys).
- Dropdowns: one open at a time, Escape returns focus, click-outside closes, clamped
  to the viewport.
- Scrollable strips: `tabindex="0"` and an accessible name.
- Alt text on every meaningful image; `alt=""` on decorative ones.
- Auto-moving content pauses (hover, focus, touch, hidden tab) or stops (reduced
  motion).
- **Contrast: measure it, don't assume it.** Over photographs, measure the pixels
  under the text (§16.3).

---

## 15 · Performance, metadata and sharing

### 15.1 · Performance floor: Lighthouse 90+ on mobile

▸ **NM trajectory:** 92 → 90 → 89 → **95** mobile, 100 desktop, 100 a11y/BP/SEO.

- **Text compression is a hosting requirement.** Most of one "score drop" was the
  local server serving 90KB uncompressed. With gzip/brotli: 27KB, and mobile 89 → 95.
  Make the local server compress (`.claude/serve.js` does), and confirm compression
  on the production host before trusting any score.
- **Preload the LCP element.** Find it in the Lighthouse report. When a hero photo
  lands it will likely become the LCP: serve it as an `<img>` with
  `fetchpriority="high"` (a CSS background can't be discovered early), sized
  correctly, AVIF/WebP.
- **Everything below the fold:** `loading="lazy"`, `decoding="async"`, explicit
  `width`/`height` or `aspect-ratio` (CLS 0).
- **Prefetch on intent** (hover/focus) for things that open, e.g. modal images from
  `data-src`.
- **Budget new per-frame costs** (rAF loops, CSS animations, `backdrop-filter`) and
  write each one down.
- **Deploy build:** strip comments (they were 40%+ of NM's HTML), minify inline
  CSS/JS, remove unused CSS from parked sections.
- **Re-run Lighthouse after every media drop-in.** Don't claim a score you haven't
  run; log the date, tool version and conditions.

```bash
npx lighthouse@12 http://localhost:4321/ --only-categories=performance,accessibility,best-practices,seo --output=html --output-path=./lh-mobile.html --chrome-flags="--headless=new"
```

```bash
npx lighthouse@12 http://localhost:4321/ --preset=desktop --output=html --output-path=./lh-desktop.html --chrome-flags="--headless=new"
```

Run mobile three times and log all three. Use a fresh profile so first-visit
behaviour (loaders) is measured. A `no-store` dev server fails bf-cache; ignore that
locally.

### 15.2 · The `<head>`

```html
<!DOCTYPE html>
<html lang="en-ZA">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Name · The headline.</title>
<meta name="description" content="The hero lede, 140–160 characters, true today.">
<link rel="canonical" href="https://example.com/">
<meta name="theme-color" content="#00253D">

<!-- icons -->
<link rel="icon" href="assets/mark/favicon.ico" sizes="any">
<link rel="icon" href="assets/mark/svg/favicon-src.svg" type="image/svg+xml">
<link rel="apple-touch-icon" href="assets/mark/raster/apple-touch-icon.png">

<!-- share preview: og:url and og:image MUST be absolute -->
<meta property="og:type" content="website">
<meta property="og:site_name" content="Name">
<meta property="og:locale" content="en_ZA">
<meta property="og:url" content="https://example.com/">
<meta property="og:title" content="Name · The headline.">
<meta property="og:description" content="One sentence.">
<meta property="og:image" content="https://example.com/assets/mark/raster/og-image.png">
<meta property="og:image:type" content="image/png">
<meta property="og:image:width" content="1200">
<meta property="og:image:height" content="630">
<meta property="og:image:alt" content="What the card says, in words.">
<meta name="twitter:card" content="summary_large_image">
<meta name="twitter:title" content="Name · The headline.">
<meta name="twitter:description" content="One sentence.">
<meta name="twitter:image" content="https://example.com/assets/mark/raster/og-image.png">

<!-- before-paint guards (loader, js class), then first-viewport font preloads, then CSS -->
</head>
```

- **Rewrite the description whenever the page changes.** NM's still said "first 90
  days" after the numbers it described had gone.
- Title, description, OG and Twitter text should agree with the hero.
- Add structured data (`Person` / `Organization` / `ProfessionalService` JSON-LD)
  when the site needs to be found by search.

### 15.3 · Video and third parties

- **Never embed YouTube/Vimeo iframes directly.** ~500KB–1MB of third-party JS before
  anyone presses play, plus tracking cookies on load (which drags the site into
  cookie-consent territory). Link out (`target="_blank" rel="noopener"`), or use a
  facade: your own poster + play button, inject the iframe on click.
- Background loops: muted, `playsinline`, short, compressed, poster frame, static
  under reduced motion. The message must read with the sound off.
- Every third-party script needs a written reason and a measured cost.

### 15.4 · The share image (OG)

The share card is most visitors' first impression when the acquisition channel is
social. Build it **as HTML in the real fonts and render it locally**:

```bash
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --headless=new --hide-scrollbars --force-device-scale-factor=1 --window-size=1200,630 --virtual-time-budget=4000 --screenshot=assets/mark/raster/og-image.png "file://$PWD/assets/mark/og/og-card.html"
```

- 1200×630, under ~300KB (NM: 48KB). Keep text inside a safe centre area: platforms
  crop.
- One accent element, the name readable, headline set exactly as the hero sets it.
- Build it **after the headline locks**.
- After launch, re-scrape in LinkedIn Post Inspector (it caches ~7 days) and the
  Facebook Sharing Debugger.

### 15.5 · Branded documents from the same tokens

Invoices, proposals, agreements, post slides and profile banners are HTML templates
reading `tokens.css`, filled from JSON and rendered to PDF/PNG by headless Chrome
(`templates/render.mjs`). The fonts stay local. Business details live in one
`practice.json`, never hard-coded. Posts render at exact pixel sizes (1080×1350
slides; LinkedIn banner 1584×396; Featured 1200×627).

---

## 16 · Verification, tooling and the launch gate

### 16.1 · Local server

`file://` runs no JS and doesn't behave like a host. Serve the build root with a
tiny zero-dependency Node server that **compresses text** (so Lighthouse is honest),
sends correct MIME types for woff2/mp4/svg, and blocks path traversal. Register it in
`.claude/launch.json`:

```json
{ "version": "0.0.1", "configurations": [
  { "name": "site-live", "runtimeExecutable": "node", "runtimeArgs": [".claude/serve.js", "site", "4321"], "port": 4321 } ] }
```

Copy `.claude/serve.js` from the nivehmarnitz.com repo as the starting point.

### 16.2 · Measure, then look

- **Verify programmatically. Ask the client to judge the feel.** Numbers catch what
  eyes miss. Eyes catch what numbers can't.
- **Preview-pane quirks:** the embedded browser can report
  `document.visibilityState === "hidden"`. That pauses transitions, animations and
  rAF, stops IntersectionObserver firing, and makes screenshots blank or offset.
  Before measuring anything animated:
  ```js
  document.getAnimations().forEach(a => a.finish());
  ```
  Two "contrast failures" and one "6px misalignment" on NM were frozen first frames,
  not bugs.
- `scroll-snap-stop` and real gesture feel can't be verified by synthetic scrolls.
  Hand those to a human.
- **Audit the page viewport by viewport** for the rules that are per-viewport
  (accent count, dot count, cursor colour). NM sampled the cursor colour at 1,216
  points and found zero mismatches.

### 16.3 · Contrast

```js
const L = c => { const [r,g,b] = c.match(/\d+(\.\d+)?/g).slice(0,3).map(v => { v/=255; return v<=.03928 ? v/12.92 : ((v+.055)/1.055)**2.4; }); return .2126*r+.7152*g+.0722*b; };
const ratio = (a,b) => { const [x,y] = [L(a),L(b)].sort((p,q)=>q-p); return ((x+.05)/(y+.05)).toFixed(2); };
ratio('rgb(248,248,245)','rgb(0,37,61)'); // 14.82
```

**Text over photographs:** hide the text, take headless screenshots at 1440/1024/375,
and check every pixel under each text line against the text colour. Report the
*worst* pixel. Re-measure whenever the photo changes, because a tint tuned on a
placeholder is not tuned for the real image.

### 16.4 · CSS discipline

- **Component-role rules go last in the stylesheet.** Two selectors with identical
  specificity are separated only by source order. ▸ **NM:** this caused an invisible
  (1.09:1) hover label three separate times.
- **Global rules bite dark sections.** A global `.dot{color:navy}` went invisible on
  every new dark ground. Scope colour to grounds.
- **Measure what CSS can't know and publish it as a custom property from JS**
  (e.g. `--head-h` for a heading whose height depends on the webfont).

### 16.5 · Version control

- Git from day one; **commit after each change set** with a message that says what
  and why. Reverting a rejected design should be a `git checkout <sha> -- file`.
- **Never push licensed fonts to a public remote.** Keep the repo private or
  git-ignore the fonts folder.
- Symlinks (`site/assets → ../assets`) must be dereferenced at deploy, or every
  asset 404s.

### 16.6 · The launch gate

Nothing ships until every line is true:

- [ ] **Every CTA resolves to a real destination** (booking link live, mailbox exists and receives)
- [ ] No `#` placeholder links; no dead anchors; social links real
- [ ] No placeholder or stock media left; `assets/placeholders/` deleted
- [ ] Every figure on the page is in the proof inventory, with permission where needed
- [ ] No two published figures multiply out to a withheld one (▸ **NM:** ROAS × spend = revenue, so absolute ROAS came off the page)
- [ ] Copy locked against the messaging platform; description/OG text match the page
- [ ] OG image rendered from the locked headline; absolute URLs on the real domain
- [ ] Responsive at 360, no horizontal scroll at any width
- [ ] Keyboard pass: every control reachable, visible focus, dialog traps and restores
- [ ] Reduced-motion pass: every animation has a static end state
- [ ] Lighthouse mobile ≥90 (×3) and desktop, on the **live domain**, with the real media
- [ ] Text compression on in production; comments stripped; CSS/JS minified
- [ ] Symlinks dereferenced; fonts served only from the client's own domain
- [ ] Analytics installed and tested (a marketer's site with no measurement is a credibility problem)
- [ ] Post-launch: re-scrape share previews; re-measure any published speed figure on the live domain (publish seconds, never the Lighthouse score)

---

## 17 · Bug index

Every one of these looked fine and was wrong. Search here before debugging.

| Symptom | Cause | Fix |
|---|---|---|
| Film frame renders flatter than its `aspect-ratio` (2.05 vs 1.78) | A competing `max-height` wins over `aspect-ratio` | Size from whichever dimension binds: height on landscape, width on portrait |
| `height:100%` child measures 0 | A flex-grown scroll container isn't a definite height | Explicit `calc()` height; publish unknowns (`--head-h`) from JS |
| Media frame squashed to 3.5:1 | A leftover `flex:1` on the copy block split the card 50/50 | Only the media flexes |
| Card stops growing between 700–800px windows | `min-height` clamp on the rail | Lower the floor; test the range between breakpoints |
| Page yanked 558px on approach | `scroll-snap-type: mandatory` armed early | Don't snap long sections; let the layout produce the catch |
| Rail drags spring back | Snap point further than a drag; `proximity` threshold ≈ half the scrollport | No snapping on multi-card rails |
| Hover label invisible (1.09:1) | Equal specificity, role rules earlier in source | Role rules last |
| Focus ring / cursor invisible on dark cards | Light section's navy focus colour inherited into dark children | Invert inside dark containers; keep a `DARK` list |
| No cursor at all on load / in the modal | `cursor:none` before first move; dialog top layer above all z-index | Don't hide the system cursor; move overlays' dependants into the dialog |
| Cursor flashes wrong colour on first appearance | Default colour + colour transition | Set ground colour on first move with transition off |
| Numbers show zeros in a background tab | Animation started inside rAF, which is paused | Synchronous reflow; throttle not rAF |
| Scroll-triggered effect never fires in preview | IntersectionObserver silent under hidden visibility | Geometry read on a throttled scroll listener |
| Nav reveal immediately undone | `scroll-behavior:smooth` keeps firing scroll events | Treat pointer position as state |
| Burger icon disappears on first tap | Script rewrote `textContent` | `aria-expanded` drives CSS; constant `aria-label` |
| Wordmark overflows once animated | `inline-block` spans break kerning | `display:inline` spans |
| Marquee gap token does nothing | `min-width:100%` + `space-around` | Content-width tracks, cloned to cover |
| Two columns' lists one line apart | Descriptions wrap differently | CSS subgrid |
| Section taller than its panels | The *other* column set the height | Measure every column before trimming |
| Em-sized icon inside a button renders at 12px | Buttons don't inherit `font-size` | `button{font:inherit}` |
| Chip grows with paragraph line-height | Inline chip inherits 1.6 | Pin the chip's own line-height |
| Lighthouse drops ~6 points locally | Dev server not compressing | Compress in `serve.js`; confirm on host |
| Muted text fails AA on a tinted card (4.15:1) | A second, fainter "tier" of muted | One muted value; hierarchy from size and position |
| Accent invisible on light ground (1.09:1) | Pastel accent used as text/hairline on light | Accent text on dark only; filled shapes on light |
| Glass effect looks like boxes | Blurring a flat colour | Glass only over a photograph |
| Stale meta description | Page copy changed, head didn't | Head copy is part of every copy pass |
