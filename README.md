# VU Customizers — knowledge transfer

Maintenance documentation for the VU Custom 3D customizers on Peak Achievement
Athletics: myBauer skates/steel and Cascade Maverik helmets. Static HTML, no build step,
no dependencies.

Open `docs/vu-guide/index.html`, or serve the folder on any static host.

## Pages

| Page | Covers |
|---|---|
| `index.html` | Scope, responsibility split, status, page map |
| `glossary.html` | Project-specific terms only (`data_variant` vs slug, recipe, elements, the two "environment"s) |
| `bauer.html` | Architecture, files, boot order, config layers, dependencies, known issues |
| `operations-guide.html` | Product setup, full settings reference, metafields, lead-time logic, live CA catalog |
| `sentry.html` | Load order, DSN, environments, tags, capture paths, alert rules, open items |
| `restore.html` | Restore-selections POC and the VU element API |
| `cascade.html` | Engine hosts, overrides, stores, catalog, gaps |
| `troubleshooting.html` | Symptom → cause → fix, both brands |
| `roadmap.html` | Goalie gear and sticks: state, outstanding work, next steps |
| `dependencies.html` | External services, assets, accounts, config outside git, deliberate decisions |

`guide.css` / `guide.js` are shared. JS builds the sidebar navigation from a single `NAV`
array, and handles dark mode, scrollspy, heading permalinks and the terms filter. To add a
page, create the file and add one line to `NAV`.

Styling follows VU Custom's own brand: Open Sans, green `#90bd3e`, near-black text.

## Vendor

The vendor is **VU Custom** (<https://vucustom.com>). Their platform is **VU OS**, with three
modules: the Front-End Customizer, VU Admin, and VU OMS. Their documentation is at
<https://vu-custom.gitbook.io/vu-custom/> — useful for VU OS concepts, but note it documents a
different embedding pattern than either of our integrations uses.

## Scope

Bauer: `sites/bauer-ca` + `sites/_shared`. Cascade: `sites/cascade-maverik`.

Not in this repo, by design or by omission:

- **Product templates and `settings_data.json`** — Shopify keeps them in the Theme Editor.
  There is no git reference binding a customizer to a product; that binding is admin-side.
- **Cascade's `jtb_custom_helmet_src` / `_environment`** — required at runtime, absent from
  the schema. Publishing without them blanks the engine URL. See `dependencies.html`.
- **Other Bauer markets** — only CA was pulled. Missing JSON there is expected.

## Accuracy

Catalog, settings and metafield values were read from live `ca.bauer.com` and
`cascademaverik.com` on **26 August 2026**, and cross-checked against the source in `sites/`.

Where this guide and the
[Product/Customizer Details sheet](https://docs.google.com/spreadsheets/d/1e-8J2PVp018qaePiCoRkoFjLID9DR0Hog-YtBezDUHI/edit)
disagree, believe the live PDP.
Update the sheet first when a product changes, then `operations-guide.html`.

## Hosting

GitHub Pages only serves `/` or `/docs` as root, so a nested folder cannot be the site root.
Either copy this folder into a small repo and publish from `main` / `(root)`, or publish from
`docs` with a `docs/index.html` redirect to `vu-guide/`.

---

Nine15, August 2026.
