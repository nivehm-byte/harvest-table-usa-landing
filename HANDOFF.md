# Handoff (29 Sep 2026, v2, repo set up)

## Where things stand
v2 of `site/index.html` (white, AG1 layout, Multi Collagen Granules as hero) is done and tested in the browser at 1440, 375 and 360 wide:
tab switching, `?product=` deep links (invalid values fall back to Multi Collagen Granules, utm parameters kept),
keyboard arrows, Home and End on the tabs, gallery swipe, arrows and thumbnails, sticky mobile bar,
Meta events (ViewContent, AmazonClick, Lead), and the signup form's placeholder path. No text pair
measured below 4.5:1. No horizontal scroll at 360.

## To supply before launch (search `PLACEHOLDER` or open with `?flags=1`)
1. Offer code and wording (`CONFIG.offer`)
2. Meta pixel ID (`window.META_PIXEL_ID` in the head), then uncomment the noscript pixel
3. Amazon Attribution tag per product (`amazonUrl` and `reviewsUrl`)
4. MailerLite form action URL and group ID (`CONFIG.mailerlite`), then test one live signup
5. Badges, descriptors and benefit lines per product for sign off
6. Substantiation text for every footnoted claim (`sub` fields)
7. Real alt text for the Amazon detail images (`*-2.jpg`, `*-3.jpg`); optionally WebP versions of all images
8. Real guide cover artwork (the current one is a generated mockup)
9. Permission to reuse the six SA reviews on a US page
10. Trust strip proof points, Our Story copy, FAQ answers
11. Social URLs, privacy policy URL, US postal address
12. Official "Available at Amazon" badge artwork
13. Live domain for canonical and og tags, a 1200 x 630 share image, favicon set
14. Licensed web fonts (Avenir Next, Avenir Next Condensed, Better Yesterday) as woff2, if licensed for web

## Questions for Niveh
- Story: leave out the founder's diagnosis (current), or include it after compliance review?
- The "Best-seller" artwork refers to South Africa. The badge says so; confirm that's acceptable.
- Ingredient sources per product (rail cards) come from the Amazon listings. Confirm with formulation.
- The Amazon listing is titled "Vegan Collagen Booster Powder"; the brief and pack say "Vegan Protein Powder". The page uses the brief.
- "Halal certified" is in the trust strip because every Amazon listing claims it. Confirm or remove.
- Vegan Protein Powder shows its Amazon rating (5.0 from 2 reviews). Keep it, or hide it until there are more?

## Repo
Private GitHub repo, whole project: https://github.com/nivehm-byte/harvest-table-usa-landing
(branch `main`, remote `origin` over SSH). The project folder is its own repo, nested inside the
home-folder repo at `~`; always run git from this folder. `gh` and Homebrew are not installed;
SSH push works, so none are needed for day-to-day commits.

Live on GitHub Pages: https://nivehm-byte.github.io/harvest-table-usa-landing/
`.github/workflows/pages.yml` publishes only `site/` on every push to `main`, so the brand guide
and project notes are not served. The repo itself is public (Pages needs that on the free plan),
so those files can still be read on github.com. Staging only: the canonical and og tags still wait
on the live domain (placeholder 13).

## Next session starts with
Drop in whatever content has arrived (placeholder list above), then run Lighthouse (README 15.1)
now that images are local. Commit and push when done.
