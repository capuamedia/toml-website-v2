# toml-website-v2

TO Meat Locker Website - New Theme

Static site for **Thousand Oaks Meat Locker** — <https://www.thousandoaksmeatlocker.com>

## Deployment

Deployed by **Cloudflare Pages from the `master` branch**. Pushing to `master`
publishes to production in about a minute. `master` is the default branch and
the only branch that matters.

Site files live at the repo root: `index.html`, `menu.html`, `catering.html`,
`about.html`, `contact.html`, `css/style.css`, `js/main.js`, `images/`.
The server rewrites `/menu.html` to `/menu` (clean URLs).

## Editing prices

Meat-by-the-pound prices are on `menu.html`, **not** `catering.html`, and each
price appears **twice** — both must be updated together:

1. The visible card in the `id="meat-by-pound"` section:
   `<span class="meat-card-price">$X.XX<span class="meat-card-unit">per pound</span></span>`
2. The matching `MenuItem` in the `Menu` JSON-LD block under the
   `"Meat by the Pound"` section: `"price": "X.XX"`

Leaving the JSON-LD stale makes Google serve the old price in rich results.
Several items share the same price, so anchor edits to the item name rather than
doing a blind find/replace on the number. Validate both `application/ld+json`
blocks still parse after editing.

`catering.html` carries per-person package pricing only.
