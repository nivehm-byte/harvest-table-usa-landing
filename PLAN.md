# Plan

## Status (29 Sep 2026)
| Step | Status |
|---|---|
| Brief read, README and brand guide read | Done |
| Reference measured (drinkag1.com Next Gen Pouch, 1024 wide) | Done |
| Pack colours sampled from Amazon listing images | Done |
| First full build, all 11 sections plus sticky bar | Done |
| Lighthouse on the live page (README 15.1) | Done, re-run after every media drop-in |
| Content supply (see HANDOFF.md placeholder list) | Open |
| Stakeholder review (Niveh, Michelle) | Open |
| Launch gate (README section 16.6) | Open |

## Lock log
| Date | Decision | Why |
|---|---|---|
| 2026-09-29 | Single self-contained `index.html`; tokens in one `:root` block instead of a shared `tokens.css` | The brief asks for one file; it is one page with nothing else sharing the tokens. Revisit if branded docs or more pages are added |
| 2026-09-29 | Greyscale wireframe step (README section 7) skipped | The brief already locks section order, hierarchy and the single action. Recorded as a deviation from the README, not a rebuttal of it |
| 2026-09-29 | Pack colours: Bovine #C07C40, Multi #B83C88, Radiance #E4649C, Vegan #636E44 | Modal colour of the pack in each Amazon hero image (canvas histogram). Pack colours are filled shapes only, never text |
| 2026-09-29 | Grounds: navy bar, off-white header and hero, forest trust strip, cream What's Inside, off-white How to Use, forest Reviews, off-white Story, sage Signup, off-white FAQ, navy footer | Alternating grounds separate sections without rules (README 10.4) |
| 2026-09-29 | Primary button navy (#182237) with off-white text, off-white on dark grounds | Matches brand look and feel; gold kept for stars and the offer code only |
| 2026-09-29 | Fonts: Avenir Next / Avenir Next Condensed from the device, Nunito Sans / Barlow Condensed as web fallbacks, Allura standing in for Better Yesterday | Licensed files not supplied. Apple devices (a large share of Meta traffic) render the real brand faces |
| 2026-09-29 | SKU tabs are a 2 x 2 grid at every width | Full names ("Bovine Collagen Granules") do not fit four across even at desktop column width, and the brief forbids shrinking the text |
| 2026-09-29 | Mobile gallery 4:3 with no thumbnails below 600px | At 1:1 the product tabs fell below the first phone screen. At 4:3 they sit inside it at 375 x 812 |
| 2026-09-29 | How to Use step 2 differs per product | The Radiance Amazon listing says it is best in cold drinks, so "stir into coffee" would be wrong for it |
| 2026-09-29 | `?product=` written with `replaceState`, other query parameters kept | Back button stays sane; utm_* and fbclid survive for attribution |
| 2026-09-29 | Rating and review count set to the live Amazon figures, not invented ones | Placeholder star counts on a live page would be fabricated proof |
| 2026-09-29 | v2: white ground, AG1 layout copied closely (pill tabs and buttons, detail accordion, "In one serving" ruled table, dark ingredients rail, AG1 review cards, top sticky bar on desktop). v1 archived in `site/archive/2026-09-29-v1/` | Client direction: "keep it very AG1, their format works in the US". Architecture borrowed; no AG1 copy, imagery or branding used |
| 2026-09-29 | Default product changed to `multi` (Multi Collagen Granules) | Client direction. Supported by SA data: best seller, 202 reviews at 4.79 |
| 2026-09-29 | Headings in Avenir Next Condensed demi, sentence case | Matches both AG1's sentence-case headings and the brand's own infographics |
| 2026-09-29 | Reviews: six real harvestmarket.co.za reviews, clearly labelled South Africa. Every review mentioning pain, joints, arthritis or other conditions excluded | FDA/FTC: testimonials count as claims. Section headline uses the weighted average, 4.8 across 478 reviews |
| 2026-09-29 | Hero ratings use SA figures (labelled "in South Africa") and link to #reviews; Vegan uses Amazon (5.0, 2) as no SA listing was found | Honest source labelling; avoids sending US buyers to the SA store |
| 2026-09-29 | Story adapted from harvesttable.co.za/our-story without the founder's cancer diagnosis | Disease references beside supplements carry FDA risk. Open for Niveh to confirm |
| 2026-09-29 | Supplied "Real people. Real results." artwork not used | One quote on it says joints "aren't as painful", a treatment claim |
| 2026-09-29 | Supplied Pearl Plus artwork not used | Not one of the four US products |
| 2026-09-29 | 15 images generated with Higgsfield GPT Image 2.5 (high quality), packs from Amazon listing photos as references. All images now local JPEGs in `site/assets/img/` (3.5 MB total) | Client direction; removes the Amazon CDN dependency |
| 2026-09-29 | Mobile tabs: two-column grid with names wrapping, pill rows above 480px | Two full names cannot share a 360px row without shrinking text (brief forbids) |
| 2026-09-29 | Desktop hero fits the first screen: header 84 → 68px, gallery square capped at `100svh - 220px`, 64px thumbnails, tighter buy column, claim small print moved below the detail accordion (same section). Measured with Multi (5 benefits): buy box bottom 780 @1440×900, 780 @1470×840, 734 @1366×768, 696 @1280×720 | Client: "first section viewable on the first screen of desktop". Fact chips hide below 760px tall (the facts repeat in benefits and What's Inside) |
| 2026-09-29 | Gallery square reserved on `.g-track` (was on each slide); Google Fonts stylesheet loaded non-blocking (`media="print"` swapped on load); thumb `object-fit` applied at every width | Lighthouse found CLS 0.75 on mobile: the gallery started 40px tall and grew to 363px when the first image arrived, pushing the buy column down. The font stylesheet blocked first paint by about 1.3s |

## Lighthouse log
Lighthouse 12.8.2 CLI, headless Chrome on Niveh's Mac, default throttling (mobile: simulated slow 4G,
4x CPU; desktop: `--preset=desktop`). Live GitHub Pages URL, default product (Multi Collagen Granules).
GitHub Pages sets a 10 minute cache lifetime; that audit stays flagged until the production host.

| Date | Build | Mobile perf | Desktop perf | A11y | Best practices | SEO | Notes |
|---|---|---|---|---|---|---|---|
| 2026-09-29 | `0cc5ba9` | 61, 62 | 90, 78 | 100 | 96 (mobile), 100 | 100 | CLS 0.75 mobile, 0.27 in one desktop run; fonts render blocking 1.3s |
| 2026-09-29 | `310c644` | 97, 99, 98 | 98, 100, 93 | 100 | 100 | 100 | Mobile LCP 2.1 to 2.4s, CLS 0 to 0.05. Left: WebP and responsive sizes (about 900 KB, placeholder 7), cache lifetime (host) |
