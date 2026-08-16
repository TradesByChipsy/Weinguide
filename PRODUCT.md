# Product

<!-- impeccable:product-schema 1 -->

## Platform

web

## Stack

Vanilla HTML/CSS/JS, single-file app (`index.html`), no build step, no framework. Data lives in `wines.json` in the same folder, fetched at runtime. Deployed via GitHub Pages (`https://tradesbychipsy.github.io/Weinguide/`).

## Users

Primary user: the owner, tracking their private collection of Spanish wines (currently focused on Comunidad Valenciana — DO Valencia / Utiel-Requena / Alicante). Used both on the phone (added to the home screen, glanced at while standing in front of the actual wine rack) and on desktop/tablet — both form factors are equally important, not mobile-only.

Secondary/future: the owner may share access with others later (family/friends browsing the same cellar), so per-user or per-device assumptions should stay easy to extend rather than being hard-baked as single-user-only. No shared/multi-user backend exists today — ratings and notes are stored in `localStorage` per device.

## Product Purpose

A personal digital wine cellar and tasting log: browse the owner's Spanish wines, see what's actually in the cellar (`owned`) vs. the wider reference list, filter/sort by type, region, and food pairing, and record personal ratings/notes per bottle. Success = the owner can quickly answer "what do I have, what goes with dinner tonight, and what did I think of it."

## Positioning

Not a public product or a general wine database — it's a bespoke, hand-curated catalog of one person's actual cellar and tasting opinions, editorial in tone (regions, food pairings, and descriptions are written/maintained specifically for this collection, not scraped or generic).

## Operating Context

- Data (`wines.json`: wine list + region metadata) is maintained centrally, outside the app itself — the footer text tells the user star ratings/notes typed in the app stay local-only ("· lokal"), while everything else comes from the maintained JSON.
- Regions are DO (Denominación de Origen) zones within Comunidad Valenciana today; the color-coding is data-driven so new Spanish regions can be added without code changes.
- Core interactions: filter by wine type/region/food pairing/owned/rated, free-text search, sort (region/rating/critic score/price/name), star-rate (1–5) and free-text note per wine (device-local), a "spectrum" strip to jump straight to a wine by color/price position, and per-region grouping when sorted by region.
- Food-pairing uses emoji shorthand (🍷🍕🍝🍖🥘🦐🧀 etc.) mapped to labels.

## Capabilities and Constraints

- Must keep working as a static, buildless site deployable on GitHub Pages (no server, no backend).
- Must keep reading `wines.json` as-is (id, n, w, region, regionName, zone, type, grape, price, priceNum, score, owned, food[], pills[], desc, rating, note) and `regions` metadata (name, do, zone, color) — redesign must not require a data-format migration.
- Ratings/notes entered in the app persist only in `localStorage` per device/browser (`wein_<id>` keys) and are explicitly marked "· lokal" vs. the centrally maintained data.
- Existing functional surface to preserve through the redesign: rating stars, local notes, the color "spectrum" jump-bar, the legend (food/wine-type/region key), region grouping, sorting, and food-pairing filters — all must survive, only the visual/interaction design is up for a full overhaul.
- Undecided: whether the app name/brand stays "Cata" or changes — open for the redesign to propose (owner is open to a new name/look).

## Brand Commitments

Current title "Cata" / tagline "Meine Weinkarte" is not locked in — the owner is open to a new name or visual identity as part of this redesign. No other brand assets (logo, colors) are binding; the current cream/serif/cobalt look is explicitly being replaced, not preserved.

## Evidence on Hand

- `wines.json` — real, current data: 77 wines, 15 owned, 3 regions (Terres dels Alforins, Utiel-Requena, DO Alicante), each wine with real name/bodega/grape/price/description/food pairing.
- Reference for liked visual direction (not to be copied literally, but evidence of the owner's taste): `https://tradesbychipsy.github.io/MobilityRoutine/` — dark, saturated canvas base with light cream content cards floating on top as distinct objects, "Bricolage Grotesque" as a bold/characterful display face paired with Inter for body text, two clear accent colors (amber + aqua) rather than gradients or glass effects.
- Rejected directions from prior exploration in this project: warm cream/paper background with a soft display serif (felt too safe/generic), dark glassmorphism with blur and violet-rose gradients (felt templated), neo-brutalist poster/ticket look with hard shadows and tilt (felt off, not disliked for boldness but for fit).

## Product Principles

1. Preserve all existing data and interactions exactly (rating, notes, filters, sort, spectrum jump, legend, region grouping) — this is a visual and interaction-design overhaul, not a feature rebuild.
2. Main filters (type, owned/rated, search) must be directly visible and usable without opening a collapsed panel — this was an explicit, repeated complaint about the incumbent design.
3. Stay a static, buildless, single-file-friendly app deployable on GitHub Pages — no backend, no build step.
4. The design should read as distinctly made for this owner's actual cellar (real regions, real bodegas), not as a generic "wine app" template.
5. Equal quality bar on mobile and desktop — this is used in both contexts regularly.

## Accessibility & Inclusion

No formal standard specified by the owner. Keep sensible defaults: readable contrast, visible focus states, reduced-motion support (already present in the incumbent CSS) should carry forward.
