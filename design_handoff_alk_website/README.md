# Handoff: ALK Netwerk Kinderfysiotherapie — Promotional Website

## Overview
A single-page promotional website for the **ALK Netwerk Kinderfysiotherapie** — a knowledge network of pediatric physiotherapists in the Zwolle region (Netherlands) specialising in **Aanhoudende Lichamelijke Klachten** (persistent physical complaints) in children and young people.

The site introduces the network, explains what ALK is, describes the bio-psychosocial treatment approach and the way the network operates, and provides a **"Find a specialist"** map with all 21 affiliated therapists.

Primary audiences: parents/young patients, and referring GPs/specialists.

## About the Design Files
The HTML file in this bundle is a **design reference** — a working prototype showing the intended look, layout, copy, and interactive behaviour. It is **not** production code to copy directly.

The task is to **recreate this design in the target codebase's existing environment** (React/Vue/Next.js/Astro/etc.) using its established patterns, components, routing and styling system — or, if no environment exists, choose an appropriate framework (Next.js or Astro recommended for a content-heavy promotional site) and implement there.

## Fidelity
**High-fidelity.** Final colours, typography, spacing, copy and interactions are settled and should be reproduced pixel-perfectly within the chosen framework's idioms.

## Screens / Views
This is a **single-page** site with a sticky top navigation that scrolls smoothly between the following sections.

### 1. Top navigation (sticky)
- **Background**: scroll-linked, not a flat fill. A `--shrink` custom property
  goes 0→1 over the first 180px of scroll, and the bar is
  `color-mix(in srgb, #ffffff calc(100% * var(--shrink)), transparent)` — fully
  transparent over the hero, solid white once compacted. The bottom border and
  box-shadow fade on the same variable, and the border keeps its 1px box at zero
  alpha so nothing shifts when it appears.
- **Height**: interpolates 146px → 88px on scroll from 900px up; 74px → 62px below that.
- **Layout**: flex, space-between. Logo SVG on the left, nav `<ul>` on the right. Both the logo height and the nav gap are scroll-linked (see `--shrink` below): logo `104px → 62px` and gap `36px → 30px` at ≥900px; logo `54px → 46px` below that.
- **Nav items**: "Over ons" → `#over-ons`, "Wat is ALK?" → `#wat-is-alk`, "Aanpak" → `#aanpak`, "Werkwijze" → `#werkwijze`, "Vind een specialist" → `#specialisten`, "Educatie" → `#links`.
- **Nav link style**: `18px → 16px` scroll-linked, `var(--ink-soft)` `#4a4a6e`, no underline; hover → `var(--ink)` with a 1.5px navy bottom-border (`var(--accent)` `#2d2c7b`).
- **Below 900px**: the `<ul>` collapses into a burger button (`.nav-toggle`, 44×44 tap target) that toggles `.nav-open` on the header. The panel (`.site-nav`) drops full-width under the bar with 52px-tall rows; it closes on link click, on Escape, on an outside click, and when the viewport crosses back over 900px. The bar itself also loses its scroll-linked transparency while open so the panel reads as solid.

### 2. Hero
- **Background**: `var(--bg)` `#fafbfc` (page default).
- **Padding**: `clamp(36px, 10.7vw, 96px)` top / `clamp(48px, 12.3vw, 110px)` bottom — 96/110 from ~900px up.
- **Layout**: 12-column grid. Headline block spans cols 1–7, `.hero-card` spans cols 8–12, `align-items: end`.
- **Left column**:
  - Eyebrow ("Regio Zwolle en omstreken") — 13px, `letter-spacing: 0.14em`, uppercase, `var(--accent-ink)` `#2d2c7b`, weight 600, 18px bottom margin.
  - H1 — Source Serif 4, 500, `clamp(30px, 5.4vw, 64px)`, line-height 1.08 (1.05 at ≥900px), balanced wrap. **Note:** this ramp caps at ~1185px, not 900px — in a 900px-wide frame it renders 48.6px, not 64px. Copy: *"Kinderfysiotherapie bij Aanhoudende Lichamelijke Klachten."*
  - Lede paragraph — `clamp(17px, 1.6vw + 12px, 21px)` (caps at 562px), line-height 1.5, `var(--ink-soft)`, max-width 36ch.
  - CTA row (28px top; 32px and side-by-side from 480px): primary pill button "Vind een specialist →" (navy bg `#2d2c7b`, white text, 13px×22px padding, border-radius 999px) and ghost pill "Wat is ALK?" (transparent, `var(--rule)` border).
- **Right column** — `.hero-card`: white background, `1px solid var(--rule)` border, 10px radius, `clamp(22px, 5vw, 32px)` padding. H3 18px "Het netwerk is er voor", followed by a 3-item bulleted list.

### 3. Over ons (`#over-ons`)
- Standard section background `var(--bg)`.
- **Layout**: `.two-col` on the 12-column grid, in two rows. Row 1 is the eyebrow spanning cols 1–12, closed by a 1px `var(--rule)` hairline whose first 48px is `var(--accent)` navy — the section marker. Row 2 puts the H2 on cols 1–4 and the two body paragraphs on cols 7–12, both opening 30px under the rule so their first lines share one optical line. From 900px `.label-col` is `display: contents`, so its eyebrow and H2 become grid items in their own right; below 900px it is a plain stacked wrapper and the eyebrow keeps its rule. The body edge is the page's main spine (see *Layout grid*).
- Below the two-column block: **`.audience` grid** — 2 cards side-by-side (1-up below 760px), 24px gap, `var(--block-gap)` top margin. Each `.aud-card` is white, `1px solid var(--rule)`, 10px radius, `clamp(24px, 5vw, 36px)` padding, with:
  - H3 "Voor kinderen & ouders" / "Voor verwijzers".
  - 1 paragraph.

  The stylesheet still carries a `.aud-card .tag` chip rule (12px uppercase, `--accent-soft` background) that the current copy no longer uses — dead CSS, safe to drop.

### 4. Wat is ALK? (`#wat-is-alk`)
- **Background override**: `var(--bg-alt)` `#f1f3f6`.
- Same `.two-col` block (eyebrow, H2, two body paragraphs).
- Below: **`.symptom-grid`** — 5-column grid from 1000px (3-up from 760px, 2-up below), 12px gap, `clamp(28px, 4vw, 36px)` top margin. It hangs off a `.eyebrow.spaced` ("Veelvoorkomende klachten") at `clamp(40px, 6.5vw, 64px)` top margin, not the two-col block, which is why its ramp is tighter than `--block-gap`. The sub-label deliberately carries no rule — the hairline marks a section, not a block inside one.
- Each `.symptom` chip: white card, `1px solid var(--rule-cool)` `#d3d7dd`, 10px radius, `clamp(14px, 3vw, 22px) clamp(8px, 2.2vw, 18px)` padding, centred `clamp(14px, 0.4vw + 13px, 15px)` text. Items: "Vermoeidheid", "Hoofdpijn", "Spier- & gewrichtspijn", "Buikpijn", "Duizeligheid", "Hartkloppingen", "Uitvalsverschijnselen", "Concentratieproblemen", "Slaapproblemen", "Verminderde belastbaarheid".

### 5. Onze aanpak (`#aanpak`)
- Standard section bg.
- `.two-col` block with 1 paragraph.
- **`.bps` grid** — 3 columns from 900px (1-up below), 20px gap, `var(--block-gap)` top margin. Each `.bps-card` is white, `clamp(22px, 4.5vw, 32px)` padding, 10px radius, with a **3px coloured top-border** (`border-top: 3px solid <bps-accent>`):
  - **`.bps-card.bio`** — top-border `var(--brand-orange)` `#f58242`. Number "01 — BIOLOGISCH" in same orange. H3 "Lichamelijke factoren".
  - **`.bps-card.psy`** — top-border `var(--brand-teal)` `#56c2b1`. Number "02 — PSYCHOLOGISCH" in teal. H3 "Gedachten & gevoelens".
  - **`.bps-card.soc`** — top-border `var(--brand-coral)` `#d84a4a`. Number "03 — SOCIAAL" in coral. H3 "Omgeving & context".
- The number itself is Source Serif 4, 13px, weight 600, letter-spacing 0.06em, 18px bottom margin.

### 6. Werkwijze (`#werkwijze`)
- **Background override**: `var(--bg-warm)` `#ffffff`.
- `.two-col` intro.
- **`.werk-grid`** — 4 columns from 900px (2-up from 600px, 1-up below), 20px gap, `var(--block-gap)` top margin. Each `.werk-card`: white, `1px solid var(--rule)`, 10px radius, `clamp(22px, 4.5vw, 28px)` padding. Number — Source Serif 4, `clamp(30px, 1.6vw + 25px, 36px)`, `var(--brand-teal)` `#56c2b1`, weight 500. H3 18px. Body 14px line-height 1.5.
  - 01 "Drie bijeenkomsten per jaar"
  - 02 "Gedeeld behandelprotocol"
  - 03 "Continue kennisuitwisseling"
  - 04 "Collegiale consultatie"
- **`.lid-block`** below grid (20px top margin; 32px at ≥900px): white card, `1px solid var(--rule)`, 10px radius, `clamp(24px, 5vw, 48px)` padding. Inner grid `minmax(0, 1fr) var(--col5)` from **1180px** (stacked below), `48px` gap, items center. The split waits for 1180px because below that the aside cannot set "BIJEENKOMSTEN" — one unbreakable word — without clipping.
  - **Left** (`.lid-info`): muted eyebrow "Lidmaatschap", H3 "Aansluiten bij het netwerk" (`clamp(20px, 1.2vw + 17px, 24px)`), two paragraphs.
  - **Right** (`.lid-meta`): `repeat(3, minmax(0, 1fr))` from 600px, with a left border `1px solid var(--rule)` and 48px left padding from 900px. Each `.meta-item` has a big number (`Source Serif 4`, `clamp(28px, 2.6vw + 20px, 38px)`, `var(--brand-orange)` `#f58242`) and a 12px uppercase muted label. The tracks must be `minmax(0, 1fr)`, not `1fr` — in this narrow column plain `1fr` sizes to min-content and the three metrics come out unequal.
    - "€25 / Jaarlijkse contributie"
    - "3× / Bijeenkomsten per jaar"
    - "22 / Aangesloten therapeuten" — note this says 22 while the dataset holds 21; see *Known content drift* below.
  - Below 600px each metric becomes a number-beside-label row: the number gets `min-width: 3ch` so the labels share a left edge, and the row is `align-items: center` so the 12px label centres on the numeral. Baseline alignment is wrong here — against a 28px numeral it drops the label onto the numeral's foot and the three rows read as sagging. Below 900px the border-left becomes a border-top with 24px top padding.

### 7. Vind een specialist (`#specialisten`)
- **Background override**: `var(--bg-alt)` `#f1f3f6`.
- `.two-col` intro ("21 kinderfysiotherapeuten in de regio."). The heading carries a `&shy;` in `kinderfysio&shy;therapeuten`: it is the one word wider than the 4-column label track, and the soft hyphen puts the break between the compound's parts rather than wherever the dictionary lands it.
- **`.map-shell`** below (`var(--block-gap)` top): grid `minmax(0, 1fr) var(--col5)` and 640px tall from 900px — the list lands on the same column line as the hero card; below that it stacks, with `#map` at `clamp(300px, 50dvh, 440px)` and the list capped at `70dvh`. White background, `1px solid var(--rule)`, 10px radius, `overflow: hidden`.
  - **Left**: `#map` — Leaflet container, 100% × 100%. Tile layer = **PDOK BRT-Achtergrondkaart** (`https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0/standaard/EPSG:3857/{z}/{x}/{y}.png`), attribution credits Kadaster + PDOK. Initial view fits all 21 marker bounds with `pad(0.18)` (`minZoom: 6`, `maxZoom: 19`). `scrollWheelZoom` is disabled by default and enabled on map click; disabled again on `mouseout`.
  - **Right**: `.specialist-list` — scrollable list, `border-left` from 900px and `border-top` below. Sticky top `.filter-bar` with a search input ("Zoek op naam of plaats…") and a 12px counter ("21 specialisten" / "N van 21 specialisten"). The input is 16px on phones — anything smaller makes iOS Safari zoom on focus — dropping to 14px at ≥900px. Below, one `.sp-item` per specialist (`14px 20px` padding, `16px 20px` at ≥900px, bottom border, hover `var(--bg-alt)`, active `var(--accent-soft)`):
    - `.sp-name` (15px weight 600)
    - `.sp-place` (12px uppercase navy)
    - phone, email, website rows (13px, soft ink, hover navy). Each is a 36px-min-height tap target on touch, collapsing to inline text at ≥900px — so the mobile list is deliberately airier than the desktop one.

    The horizontal padding here is intentionally a literal 20px rather than `var(--gutter)`: it is card-internal spacing and must not ride the page gutter, which would otherwise swell it to ~28px around 768px and snap back at 900px.
- **Markers**: custom `divIcon` with class `.alk-marker` — 28×28px, navy `var(--accent)` background, 50%/50%/50%/0 radius rotated -45° to form a teardrop, 2px white border, soft drop-shadow, 8px white dot in centre.
- **Marker popup**: name (Source Serif 4, 600, 15px), place (12px uppercase muted), phone/email/website rows with emoji prefixes (📞 ✉ 🌐).
- Clicking a list item: `map.setView(coords, 12, animate)`, opens that marker's popup, sets `.active` on the item.

### 8. Educatie (`#links`)
- **Background override**: `var(--bg-warm)` `#ffffff`.
- `.two-col` intro.
- **`.links-grid`** — 2 columns from 760px (1-up below), 24px gap, `var(--block-gap)` top margin. Each `.link-card`: white, `1px solid var(--rule)`, 10px radius, `--card-pad: clamp(20px, 4.5vw, 32px)`. H3 19px, 18px bottom margin.
- Inside is a `<ul>` with no bullets. **The whole row is the link**: each `<li>` holds one `a.link-row` — a column flexbox, `min-height: 44px`, `padding: 14px var(--card-pad)` with `margin: 0 calc(-1 * var(--card-pad))` so the hover surface bleeds to the card edges. The `<ul>` carries `margin: -14px 0` to cancel the first and last row's own padding, which keeps the true H3→first-label gap at 18px and the last-label→card-bottom gap at 32px. Bottom border on every row except the last.
  - `.lt-label` — 14px ink, weight 500.
  - `.lt-src` — 13px muted, `word-break: break-all`, 4px gap from label. Both turn navy on row hover.
- **Left card** "Educatie over pijn" (4 rows) — podcast (henw.org), pijn-educatiefilmpje, struggle switch, neuroplasticiteit.
- **Right card** "Hoofdpijn" (3 rows) — Isala folder 7208, Headache Relief Guide, Alles over hoofdpijn (BE).

### 9. Footer
- **Background**: `var(--bg-alt)` `#f1f3f6`, top border `1px solid var(--rule)`.
- **Padding**: `clamp(40px, 6.3vw, 56px)` top / `clamp(44px, 7.2vw, 64px)` bottom.
- Column-stacked below 760px; from 760px a wrapping flex row with `space-between` and `align-items: center` (the logo is much taller than either paragraph, so top-aligning them reads as unbalanced).
- Logo height 56px, 64px at ≥900px. Middle paragraph "© 2026 ALK Regio Zwolle en omstreken / Kennisnetwerk voor gespecialiseerde kinderfysiotherapie" (the line break is a literal `<br>`), then the attribution "Kaartdata © OpenStreetMap-bijdragers".
- The middle paragraph sits where `space-between` puts it; it is *not* centred on the container, and forcing that would squeeze the attribution into a second line between 768px and ~1010px.

## Layout grid
Everything on desktop sits on **one 12-column grid**, engaged at 900px:

```
col  = (100% - 11 * var(--grid-gap)) / 12
--grid-gap: 24px          /* the gutter, and the gap of every card row */
--col5: calc((5 * 100% - 7 * var(--grid-gap)) / 12)
```

`--col5` is a 5-column span expressed as a width, for the two containers that
cannot carry a grid gap: the map shell (its divider is flush) and the lid-block
(a padded card, so its interior is its own context).

At the 1180px container this gives 71px columns and these spans:

| Block | Columns | Width |
|---|---|---|
| Intro eyebrow | 1–12 | 1116 |
| Intro heading | 1–4 | 356 |
| Intro body | 7–12 | 546 |
| Hero headline | 1–7 | 641 |
| Hero card / specialist list | 8–12 | 451 |
| 2-up cards (audience, links) | 6 + 6 | 546 each |
| 3-up cards (bps) | 4 + 4 + 4 | 356 each |
| 4-up cards (werkwijze) | 3 × 4 | 261 each |

The payoff is that the page has **two recurring vertical edges** instead of six
competing ones: the intro body column at col 7, which is also the second card
of any 2-up row and the third of a 4-up row; and the aside at col 8, shared by
the hero card and the specialist list.

The intro heading stops at col 4 rather than col 5 on purpose. A 5/6 split
reads as two equal slabs; 4 against 6, with the full-width eyebrow rule tying
them together, reads as a label, a heading and its body. The heading is the
one block that does not sit on the col-7 spine, and the trailing air in its
row is the section's breathing room, not a missing column.

**The one exception** is `.symptom-grid`, which stays 5-up. Twelve columns do
not divide by five, and the long Dutch compounds ("Uitvalsverschijnselen")
need the width — forcing it to 6-up would reintroduce the hyphenation the
5-up layout exists to avoid.

Card interiors are deliberately *not* page-grid-aligned: the page grid governs
where cards sit, a card's own padding governs what is inside it.

## Responsive strategy
The stylesheet is **mobile-first**: every base rule describes the narrowest
viewport and each component is followed by the `min-width` queries that add to
it. There is no `max-width` query in the file.

Breakpoint ladder:

| Min-width | What changes |
|---|---|
| base | single-column everywhere; symptom chips 2-up; burger nav; stacked map + list |
| 480px | CTA buttons sit side by side instead of full-width |
| 600px | werk-grid 2-up; lid-meta returns to three side-by-side metrics |
| 760px | audience + links cards 2-up; symptom chips 3-up |
| 900px | the design's own desktop switch — **the 12-column grid engages**: two-col grids, bps 3-up, werk-grid 4-up, map beside the list, inline nav, tall header |
| 1000px | symptom chips 5-up (the handoff layout) |
| 1180px | lid-block splits into info + metrics (waits for the container's max-width so the metric labels don't clip) |

Block-level vertical gaps are **not** on this ladder — they ramp fluidly via
`--block-gap` (see Spacing), so every section's intro→block gap is identical at
every viewport width rather than stepping at whichever breakpoint that
particular grid happens to change column count.

Long Dutch compounds ("Uitvalsverschijnselen", "Concentratieproblemen") are
wider than a phone column, so grid tracks use `minmax(0, 1fr)` and those two
chips carry a `&shy;` at the compound boundary; from 1000px the tracks revert
to the design's `1fr` and the chips need no break at all. Hyphenation is
`manual` everywhere — headings and chips break only where a soft hyphen says
they may, so no viewport can produce a dictionary break like
"kinderfysi-otherapeuten".

## Interactions & Behavior
- **Smooth scroll** on every in-page anchor link. The offset is computed, not a
  fixed number: the bar is read from `--row-short` (88px at ≥900px, 62px below),
  the height it is about to shed on shrink is subtracted too, and a further 16px
  of clearance is added — so a section lands 16px under the settled bar at any
  width. Do not hard-code 60px.
- **Hover transitions**: nav underline, button `transform: translateY(-1px)` and `.btn .arr` arrow translate 3px, list items background fade.
- **Map**:
  - `scrollWheelZoom: false` initially → enable on `click`, disable on `mouseout`. (Prevents accidental wheel-zoom while scrolling the page.)
  - Marker popup opens on marker click.
  - Clicking a list item pans/zooms (`setView(..., 12)`) and opens that marker's popup; the active list item gets the `.active` class (highlighted background).
  - Filter input does case-insensitive substring match against `name + " " + place`. Counter updates live.
- **Map on touch** (`pointer: coarse`): dragging and pinch-zoom start disabled and a `.map-gate` overlay ("Tik om de kaart te gebruiken") covers the map, so a one-finger swipe scrolls the page instead of panning the map. Tapping the gate — or any specialist in the list — releases it; scrolling the map out of view re-arms it.

## State Management
The page is content-driven; only one piece of dynamic state exists:
- **Filter query** (string) → re-renders the list items. Drives the visible count in the meta line.
- **Active list item** (id) → adds `.active` class to one `.sp-item`, syncs with the open Leaflet popup.

The 21-therapist dataset is embedded in the page as a plain JS array (`SPECIALISTS`) — in a real codebase this should move to a typed data file (e.g. `data/specialists.ts`) or a CMS-backed source. Each entry has: `name`, `phone`, `email`, `website`, `url`, `place`, `coords: [lat, lng]`.

## Design Tokens

### Colors
| Token | Hex | Use |
|---|---|---|
| `--bg` | `#fafbfc` | Page background (almost white) |
| `--bg-alt` | `#f1f3f6` | Alt section bg + footer (cool neutral) |
| `--bg-warm` | `#ffffff` | "Warm" section override (currently pure white) |
| `--bg-card` | `#ffffff` | Cards |
| `--ink` | `#1a1944` | Body text + headings |
| `--ink-soft` | `#4a4a6e` | Soft body text |
| `--ink-mute` | `#7d7f95` | Muted labels |
| `--rule` | `#dadde3` | Default border/divider |
| `--rule-cool` | `#d3d7dd` | Cooler border (symptom chips) |
| `--rule-warm` | `#dadde3` | Warm-section border (currently same as default) |
| `--accent` / `--accent-ink` | `#2d2c7b` | Primary navy — links, buttons, accent |
| `--accent-soft` | `#e2e1ee` | Soft pale-navy chip background |
| `--brand-navy` | `#2d2c7b` | (logo) |
| `--brand-teal` | `#56c2b1` | (logo) — werkwijze numbers, "psy" BPS card |
| `--brand-orange` / `--warm` | `#f58242` | (logo) — meta numbers, "bio" BPS card |
| `--brand-coral` | `#d84a4a` | (logo) — "soc" BPS card |
| Marker fill | `#2d2c7b` | Custom map marker (navy) |

### Typography
- **Display / headings**: `"Source Serif 4"`, weight 500, letter-spacing -0.01em, `text-wrap: balance`. Loaded from Google Fonts (`opsz,wght@8..60,400;500;600`).
- **Body / UI**: `"Public Sans"`, weights 400 / 500 / 600. Loaded from Google Fonts.
- **Sizes**:
  - H1: `clamp(30px, 5.4vw, 64px)` / line-height 1.08, 1.05 at ≥900px
  - H2: `clamp(24px, 3.4vw, 44px)` / 1.18, 1.15 at ≥900px. In the 4-column label track the H2 also carries a `margin-top: calc(37px - 0.255em)` at ≥900px: 0.255em is Source Serif's cap-top offset inside its line box and 6.8px is Public Sans's at 18px, so the lift is exactly what puts the heading's cap-height on the body's, whatever the ramp has done to either size.
  - H3: `clamp(19px, 1vw + 15px, 22px)` / 1.25 (cards override to 18–24px)
  - Body: 17px / 1.55, paragraphs in `.body-col` are `clamp(16px, 0.8vw + 14px, 18px)`
  - Lede: `clamp(17px, 1.6vw + 12px, 21px)` / 1.5
  - Eyebrow: 13px uppercase, letter-spacing 0.14em
  - Symptom / nav / button: 14–15px

### Spacing
The vertical rhythm is fluid. Most **spacing** ramps reach their full desktop
value at or just before 900px, so from 900px up the figures below match to the
pixel. `--block-gap` is the exception — it keeps growing to 1067px, so a
900px-wide frame shows 40px where the desktop design shows 64px:

| Ramp | Caps at |
|---|---|
| `--gutter` | 889px |
| `--block-gap` | ~1067px (40px at 900px, not 64px) |
| `--section-y`, hero padding | ~897px |

The **type** ramps do not, and this is the one place where reading the figures
as "the 900px design" will mislead you — H1 and H2 keep growing well past the
desktop switch:

| Ramp | Caps at | Value at 900px |
|---|---|---|
| Lede | 562px | 21px |
| H3 | 700px | 22px |
| H1 | ~1185px | **48.6px**, not 64px |
| H2 | ~1294px | **30.6px**, not 44px |

So H1 only renders at its documented 64px from ~1185px up, and H2 its 44px only
from ~1294px — past the 1180px container, so the H2 never quite reaches its cap
inside `.wrap`. If you are building to a 900px-wide frame, expect 48.6px / 30.6px.

- Section vertical padding: `clamp(56px, 10.7vw, 96px)`
- Hero vertical padding: `clamp(36px, 10.7vw, 96px)` top / `clamp(48px, 12.3vw, 110px)` bottom
- Container max-width: **1180px**, side-padding `clamp(20px, 3.6vw, 32px)`
- Card padding is a scale keyed to how many columns the card spans:

  | Token | Desktop | Used by |
  |---|---|---|
  | `--pad-sm` | 20px | symptom chips |
  | `var(--grid-gap)` | 24px | 3-column werk cards (the narrowest) |
  | `--pad-md` | 32px | hero, audience, bps, link cards |
  | `--pad-lg` | 48px | lid-block (the full-width feature panel) |

  Each is a `clamp()` bottoming out at 14–24px on phones.
- Intro→block gap: `--block-gap: clamp(40px, 6vw, 64px)`, shared by
  `.audience`, `.bps`, `.werk-grid`, `.links-grid` and `.map-shell`. The chip
  grid is the one deliberate exception at `clamp(28px, 4vw, 36px)`, because it
  measures an eyebrow→chips gap rather than intro→block.
- Gap scale: **4 / 8 / 12 / 16 / 24 / 32 / 48 / 64**. 4px is a hairline for
  label+source pairs; 24px is the grid gutter and the gap of every card row;
  64px is reserved for `--block-gap`, the one gap that separates a section's
  intro from the block under it. *Horizontal* asymmetric splits still get their
  gap from an empty column, not a large gap value.
- Minimum tap target: `--tap: 44px` (buttons, burger, search field; 52px nav rows)

### Radii & shadows
- Standard radius: `10px` (cards, map shell, inputs)
- Pill button radius: `999px`
- Map marker shadow: `0 2px 8px rgba(0,0,0,.18)`

## Assets
- **`logo.svg`** — Brand logo with five fill classes (`cls-1` navy `#2d2c7b`, `cls-2` coral `#d84a4a`, `cls-3` white, `cls-4` orange `#f58242`, `cls-5` teal `#56c2b1`). The fill rules are defined in the SVG's own `<defs><style>` block; consume as-is or inline if your bundler prefers. Used in the header at a scroll-linked 104px→62px (54px→46px below 900px), and in the footer at 56px, 64px from 900px.
- **Map tiles** — PDOK / Kadaster BRT-Achtergrondkaart (open data, no API key). Attribution must remain visible.
- **Leaflet** — `leaflet@1.9.4` (CSS + JS, with SRI hashes in the HTML). Replace with your codebase's preferred React wrapper (`react-leaflet`) or vanilla integration.

## External libraries currently referenced
- `leaflet@1.9.4` (CSS + JS, with integrity hashes)
- Google Fonts: Source Serif 4 + Public Sans

## Known content drift
Two things in the prototype disagree with each other. Neither is a styling
issue; both need a content decision before or during implementation.

- **21 vs 22 therapists.** The `SPECIALISTS` array holds **21** entries, and the
  section heading and list counter both say 21. But the membership block's third
  metric still reads **"22 / Aangesloten therapeuten"**. Either the network has
  22 members with one not yet listed, or the metric is stale — confirm which.
- **Section backgrounds are inline attributes.** `#wat-is-alk`, `#werkwijze`,
  `#specialisten` and `#links` set their background via a `style="…"` attribute
  on the `<section>`, not a class. `#specialisten` *also* has an equivalent CSS
  rule, so that one is declared twice. When porting, move all four to the
  styling system and drop the duplicate.

## Files
- `index.html` — the full prototype. Read top-to-bottom: tokens → component CSS → HTML body (top → footer) → vanilla JS for the specialist list + map.
- `logo.svg` — the brand logo.
