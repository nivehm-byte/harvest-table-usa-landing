# The Harvest Table: USA landing page

Single product landing page for US Meta ad traffic. A storefront, not a shop: every buy
button goes to that product's Amazon.com listing. Owner: Niveh. Design: Michelle.

## Locked rules (from the brief)
- Brand guide (`THM_Brand Guidelines.pdf`) wins on colour, font and visual style.
- US English. No em or en dashes anywhere. "Serving", never the other word. Full product names always.
- No disease or treatment claims. Benefit lines say "supports". Every claim gets a numbered
  footnote with substantiation in the same section's small print.
- FDA disclaimer verbatim in the footer.
- SKU tabs in this order: bovine, multi, radiance, vegan. Default `radiance`. `?product=<key>` opens that tab.

## File map
- `site/index.html`: the whole page. CSS and JS inline. All content lives in `CONFIG`, `PRODUCTS`
  and `REVIEWS` at the top of the script.
- `site/assets/logo-navy.png`, `logo-light.png`: cropped from `Harvest Table Logo.png`.
- `website-playbook/README.md`: the build method.
- Find unfinished content: search `PLACEHOLDER`, or open the page with `?flags=1`.

## Run locally
`cd site && python3 -m http.server 4321`, then open http://127.0.0.1:4321/?product=radiance
