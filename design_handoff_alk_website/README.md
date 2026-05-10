# Handoff: ALK Netwerk Kinderfysiotherapie — Promotional Website

## Overview
A single-page promotional website for the **ALK Netwerk Kinderfysiotherapie** — a knowledge network of pediatric physiotherapists in the Zwolle region (Netherlands) specialising in **Aanhoudende Lichamelijke Klachten** (persistent physical complaints) in children and young people.

The site introduces the network, explains what ALK is, describes the bio-psychosocial treatment approach and the way the network operates, and provides a **"Find a specialist"** map with all 22 affiliated therapists.

Primary audiences: parents/young patients, and referring GPs/specialists.

## About the Design Files
The HTML file in this bundle is a **design reference** — a working prototype showing the intended look, layout, copy, and interactive behaviour. It is **not** production code to copy directly.

The task is to **recreate this design in the target codebase's existing environment** (React/Vue/Next.js/Astro/etc.) using its established patterns, components, routing and styling system — or, if no environment exists, choose an appropriate framework (Next.js or Astro recommended for a content-heavy promotional site) and implement there.

## Fidelity
**High-fidelity.** Final colours, typography, spacing, copy and interactions are settled and should be reproduced pixel-perfectly within the chosen framework's idioms.

## Screens / Views
This is a **single-page** site with a sticky top navigation that scrolls smoothly between the following sections.

### 1. Top navigation (sticky)
- **Background**: `#ffffff`, bottom border `1px solid var(--rule)` (`#dadde3`).
- **Height**: 84px.
- **Layout**: flex, space-between. Logo SVG on the left (`height: 56px`), nav `<ul>` on the right with 28px gap.
- **Nav items**: "Over ons" → `#over-ons`, "Wat is ALK?" → `#wat-is-alk`, "Aanpak" → `#aanpak`, "Werkwijze" → `#werkwijze`, "Vind een specialist" → `#specialisten`, "Educatie" → `#links`.
- **Nav link style**: 15px, `var(--ink-soft)` `#4a4a6e`, no underline; hover → `var(--ink)` with a 1.5px navy bottom-border (`var(--accent)` `#2d2c7b`).
- **On mobile (<900px)**: hide the nav `<ul>`.

### 2. Hero
- **Background**: `var(--bg)` `#fafbfc` (page default).
- **Padding**: 120px top / 110px bottom.
- **Layout**: 2-column grid `1.15fr 0.85fr`, 64px gap, items `align-items: end`.
- **Left column**:
  - Eyebrow ("Regio Zwolle en omstreken") — 13px, `letter-spacing: 0.14em`, uppercase, `var(--accent-ink)` `#2d2c7b`, weight 600, 18px bottom margin.
  - H1 — Source Serif 4, 500, clamp(40px, 5.4vw, 64px), line-height 1.05, balanced wrap. Copy: *"Kinderfysiotherapie bij Aanhoudende Lichamelijke Klachten."*
  - Lede paragraph — 21px, line-height 1.5, `var(--ink-soft)`, max-width 36ch.
  - CTA row (32px top): primary pill button "Vind een specialist →" (navy bg `#2d2c7b`, white text, 13px×22px padding, border-radius 999px) and ghost pill "Wat is ALK?" (transparent, `var(--rule)` border).
- **Right column** — `.hero-card`: white background, `1px solid var(--rule)` border, 10px radius, 32px padding. H3 18px "Het netwerk is er voor", followed by a 3-item bulleted list.

### 3. Over ons (`#over-ons`)
- Standard section background `var(--bg)`.
- **Layout**: `.two-col` grid `1fr 1.4fr`, 72px gap. Left has eyebrow + H2; right has 2 paragraphs (18px body).
- Below the two-column block: **`.audience` grid** — 2 cards side-by-side, 24px gap. Each `.aud-card` is white, `1px solid var(--rule)`, 10px radius, 36px padding, with:
  - A `.tag` chip — 12px uppercase, `var(--accent-soft)` `#e2e1ee` background, `var(--accent-ink)` `#2d2c7b` text, 5px×10px padding, 4px radius.
  - H3 "Begeleiding op maat" / "Gericht doorverwijzen".
  - 1 paragraph.

### 4. Wat is ALK? (`#wat-is-alk`)
- **Background override**: `var(--bg-alt)` `#f1f3f6`.
- Same `.two-col` block (eyebrow, H2, two body paragraphs).
- Below: **`.symptom-grid`** — 5-column grid (2-column on mobile), 12px gap, 36px top margin.
- Each `.symptom` chip: white card, `1px solid var(--rule-cool)` `#d3d7dd`, 10px radius, 22px×18px padding, centred 15px text. Items: "Vermoeidheid", "Hoofdpijn", "Spier- & gewrichtspijn", "Buikpijn", "Duizeligheid", "Hartkloppingen", "Uitvalsverschijnselen", "Concentratieproblemen", "Slaapproblemen", "Verminderde belastbaarheid".

### 5. Onze aanpak (`#aanpak`)
- Standard section bg.
- `.two-col` block with 1 paragraph.
- **`.bps` grid** — 3 columns, 20px gap. Each `.bps-card` is white, 32px padding, 10px radius, with a **3px coloured top-border** (`border-top: 3px solid <bps-accent>`):
  - **`.bps-card.bio`** — top-border `var(--brand-orange)` `#f58242`. Number "01 — BIOLOGISCH" in same orange. H3 "Lichamelijke factoren".
  - **`.bps-card.psy`** — top-border `var(--brand-teal)` `#56c2b1`. Number "02 — PSYCHOLOGISCH" in teal. H3 "Gedachten & gevoelens".
  - **`.bps-card.soc`** — top-border `var(--brand-coral)` `#d84a4a`. Number "03 — SOCIAAL" in coral. H3 "Omgeving & context".
- The number itself is Source Serif 4, 13px, weight 600, letter-spacing 0.06em, 18px bottom margin.

### 6. Werkwijze (`#werkwijze`)
- **Background override**: `var(--bg-warm)` `#ffffff`.
- `.two-col` intro.
- **`.werk-grid`** — 4 columns (2 on mobile), 20px gap. Each `.werk-card`: white, `1px solid var(--rule)`, 10px radius, 28px padding. Number — Source Serif 4, **36px**, `var(--brand-teal)` `#56c2b1`, weight 500. H3 18px. Body 14px line-height 1.5.
  - 01 "Drie bijeenkomsten per jaar"
  - 02 "Gedeeld behandelprotocol"
  - 03 "Continue kennisuitwisseling"
  - 04 "Collegiale consultatie"
- **`.lid-block`** below grid (32px top margin): white card, `1px solid var(--rule)`, 10px radius, 48px padding. Inner grid `1.4fr 1fr`, 56px gap, items center.
  - **Left** (`.lid-info`): muted eyebrow "Lidmaatschap", H3 "Aansluiten bij het netwerk" (24px), two paragraphs.
  - **Right** (`.lid-meta`): 3-column grid with a left border `1px solid var(--rule)` and 48px left padding. Each `.meta-item` has a big number (`Source Serif 4`, 38px, `var(--brand-orange)` `#f58242`) and a 12px uppercase muted label.
    - "€25 / Jaarlijkse contributie"
    - "3× / Bijeenkomsten per jaar"
    - "22 / Aangesloten therapeuten"
  - On mobile: stack to a single column, border-left becomes border-top with 24px top padding.

### 7. Vind een specialist (`#specialisten`)
- **Background override**: `var(--bg-alt)` `#f1f3f6`.
- `.two-col` intro ("22 kinderfysiotherapeuten in de regio.").
- **`.map-shell`** below (40px top): grid `1fr 380px`, 640px tall, white background, `1px solid var(--rule)`, 10px radius, `overflow: hidden`.
  - **Left**: `#map` — Leaflet container, 100% × 100%. Tile layer = **PDOK BRT-Achtergrondkaart** (`https://service.pdok.nl/brt/achtergrondkaart/wmts/v2_0/standaard/EPSG:3857/{z}/{x}/{y}.png`), attribution credits Kadaster + PDOK. Initial view fits all 22 marker bounds with `pad(0.18)`. `scrollWheelZoom` is disabled by default and enabled on map click; disabled again on `mouseout`.
  - **Right**: `.specialist-list` — left-bordered scrollable list. Sticky top `.filter-bar` containing a 14px search input ("Zoek op naam of plaats…") and a 12px counter ("22 specialisten" / "N van 22 specialisten"). Below, one `.sp-item` per specialist (16px×20px padding, bottom border, hover `var(--bg-alt)`, active `var(--accent-soft)`):
    - `.sp-name` (15px weight 600)
    - `.sp-place` (12px uppercase navy)
    - phone, email, website rows (13px, soft ink, hover navy).
- **Markers**: custom `divIcon` with class `.alk-marker` — 28×28px, navy `var(--accent)` background, 50%/50%/50%/0 radius rotated -45° to form a teardrop, 2px white border, soft drop-shadow, 8px white dot in centre.
- **Marker popup**: name (Source Serif 4, 600, 15px), place (12px uppercase muted), phone/email/website rows with emoji prefixes (📞 ✉ 🌐).
- Clicking a list item: `map.setView(coords, 12, animate)`, opens that marker's popup, sets `.active` on the item.

### 8. Educatie (`#links`)
- **Background override**: `var(--bg-warm)` `#ffffff`.
- `.two-col` intro.
- **`.links-grid`** — 2 columns. Each `.link-card`: white, `1px solid var(--rule)`, 10px radius, 32px padding. H3 19px. Inside is a `<ul>` with no bullets; each `<li>` has a 12px×0px vertical pad, 1px bottom border (none on last), with:
  - `.lt-label` — 14px ink, weight 500.
  - `<a>` — 13px muted, hover navy, 4px gap from label.
- **Left card** "Educatie over pijn" — podcast (henw.org), pijn-educatiefilmpje, struggle switch, neuroplasticiteit.
- **Right card** "Hoofdpijn" — Isala folder 7208, Headache Relief Guide, Alles over hoofdpijn (BE), Migraine YouTube (EN).

### 9. Footer
- **Background**: `var(--bg-alt)` `#f1f3f6`, top border `1px solid var(--rule)`.
- **Padding**: 56px top / 64px bottom.
- Flex row, space-between, wraps. Logo (height 64px), centre paragraph "Regio Zwolle en omstreken / Kennisnetwerk voor gespecialiseerde kinderfysiotherapie", right-aligned attribution "Kaartdata © OpenStreetMap-bijdragers".

## Interactions & Behavior
- **Smooth scroll** on every in-page anchor link. Subtract 60px to compensate for the sticky header.
- **Hover transitions**: nav underline, button `transform: translateY(-1px)` and `.btn .arr` arrow translate 3px, list items background fade.
- **Map**:
  - `scrollWheelZoom: false` initially → enable on `click`, disable on `mouseout`. (Prevents accidental wheel-zoom while scrolling the page.)
  - Marker popup opens on marker click.
  - Clicking a list item pans/zooms (`setView(..., 12)`) and opens that marker's popup; the active list item gets the `.active` class (highlighted background).
  - Filter input does case-insensitive substring match against `name + " " + place`. Counter updates live.
- **Responsive breakpoint**: `max-width: 900px` collapses the 2-column grids, the 4-column werk-grid (→ 2 cols), the 5-column symptom-grid (→ 2 cols), the lid-block and map-shell. Top nav `<ul>` is hidden (no replacement; if a real nav menu/burger is desired, add one in implementation).

## State Management
The page is content-driven; only one piece of dynamic state exists:
- **Filter query** (string) → re-renders the list items. Drives the visible count in the meta line.
- **Active list item** (id) → adds `.active` class to one `.sp-item`, syncs with the open Leaflet popup.

The 22-therapist dataset is embedded in the page as a plain JS array (`SPECIALISTS`) — in a real codebase this should move to a typed data file (e.g. `data/specialists.ts`) or a CMS-backed source. Each entry has: `name`, `phone`, `email`, `website`, `url`, `place`, `coords: [lat, lng]`.

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
  - H1: `clamp(40px, 5.4vw, 64px)` / line-height 1.05
  - H2: `clamp(28px, 3.2vw, 38px)` / 1.15
  - H3: 22px / 1.25 (some cards override to 18–24px)
  - Body: 17px / 1.55, paragraphs in `.body-col` are 18px
  - Lede: 21px / 1.5
  - Eyebrow: 13px uppercase, letter-spacing 0.14em
  - Symptom / nav / button: 14–15px

### Spacing
- Section vertical padding: **96px** (desktop), **64px** (mobile)
- Hero vertical padding: **120/110** (desktop), **64** (mobile)
- Container max-width: **1180px**, side-padding 32px
- Card padding range: 28–48px
- Grid gaps: 12px (chips) / 20–24px (cards) / 56–72px (two-col)

### Radii & shadows
- Standard radius: `10px` (cards, map shell, inputs)
- Pill button radius: `999px`
- Map marker shadow: `0 2px 8px rgba(0,0,0,.18)`

## Assets
- **`logo.svg`** — Brand logo with five fill classes (`cls-1` navy `#2d2c7b`, `cls-2` coral `#d84a4a`, `cls-3` white, `cls-4` orange `#f58242`, `cls-5` teal `#56c2b1`). The fill rules are defined in the SVG's own `<defs><style>` block; consume as-is or inline if your bundler prefers. Used at 56px height in the header and 64px in the footer.
- **Map tiles** — PDOK / Kadaster BRT-Achtergrondkaart (open data, no API key). Attribution must remain visible.
- **Leaflet** — `leaflet@1.9.4` (CSS + JS, with SRI hashes in the HTML). Replace with your codebase's preferred React wrapper (`react-leaflet`) or vanilla integration.

## External libraries currently referenced
- `leaflet@1.9.4` (CSS + JS, with integrity hashes)
- Google Fonts: Source Serif 4 + Public Sans

## Files
- `ALK Netwerk Kinderfysiotherapie.html` — the full prototype. Read top-to-bottom: tokens → component CSS → HTML body (top → footer) → vanilla JS for the specialist list + map.
- `logo.svg` — the brand logo.
