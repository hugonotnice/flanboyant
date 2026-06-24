# CHANGELOG

All brand, visual, and content changes to `flanboyant.com` are documented here.

Format follows [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).  
Brand decisions are tagged: `[BRAND]`, `[LAYOUT]`, `[CONTENT]`, `[SEO]`, `[FIX]`.

---

## [Unreleased]

## [2.3.0] — 2026-06-24

### Dual-Audience Candidates & Startups Mode Switch

**[BRAND]** Implemented interactive audience-mode targeting: Candidates mode is the default, focused on attracting high-growth operators with direct-cap-table and life-changing equity copy. Startups mode displays the original founder-to-founder recruitment messaging.

**[LAYOUT]** Added a customized, non-rounded Mode Switch component (`.mode-switch`, `.mode-btn`) to the sticky header. Button states and layouts adhere strictly to the Swiss minimalist aesthetic with solid flat fills, no borders on children, and sharp vertical dividers.

**[CONTENT]** Developed full editorial candidate-specific copy:
  - **The Roles:** Six founding-level opportunities with high-growth definitions.
  - **What You Get:** Clear visual comparisons of "What This Isn't" vs "What It Is" to align expectation around real equity, compensation floors, and direct founder lines.
  - **Who We Place:** Quality criteria highlighting shipped work, ownership, startup-readiness, and long-term thinking.
  - **How It Works:** A clear, frictionless 4-step placement model (Reach Out &rarr; Handpicked Match &rarr; Paid Work Trial &rarr; Signed Offer).

**[BRAND]** Structured conditional views using utility class styling (`.for-candidates`, `.for-startups`) tied to a root `[data-mode]` attribute, ensuring layout blocks toggle instantly without content overlap or pagination issues.

**[FIX]** Added smooth container scrolling resets on mode toggle, instantly scrolling left and right columns back to top upon mode changes to maximize focus and avoid scroll disorientation.

## [2.2.0] — 2026-06-21

### Unified Right-Column Panel Blueprint and Typography Scale

**[LAYOUT]** Redesigned and standardized all 4 right-column panels (`Founding Mandates`, `Why Us`, `Pipeline`, `Our Terms`) to follow a single, unified visual layout blueprint: `panel-label` &rarr; `panel-desc` &rarr; `panel-cols` (2 columns of items separated by a vertical 2px solid `.panel-divider`).

**[LAYOUT]** Added adaptive fallback container queries (`max-width: 420px`) inside the panel container, automatically collapsing the two-column grid into a single column vertical stack and rotating the 2px vertical divider into a horizontal 1px separator for absolute mobile alignment.

**[TOKENS]** Introduced a unified typographic scale using 5 precise, fluid, height/width-based font-size tokens (`--fs-eyebrow`, `--fs-desc`, `--fs-num`, `--fs-title`, `--fs-sub`) re-used identically across all panels to guarantee mathematical symmetry.

**[BRAND]** Cleaned up the stylesheet by completely removing all old, orphan, and complex per-panel styling layers (`mandates-grid`, `mandate-card`, `pipeline-list`, `pipeline-item`, `terms-grid`, `term-cell`, etc.), reducing CSS footprint and complexity.

**[FIX]** Updated the desktop Safety Clamp (`@media (min-width: 768px) and (max-height: 680px)`) under `@layer utilities`. Discovered that it was targeting the deleted `.mandate-card p` class (legacy code), and modernized it to target our new standardized `.item-sub` class, ensuring flawless card compression on short viewports.

---

## [2.1.0] — 2026-06-21

### Re-implemented Desktop Viewport Lock and Fixed Spacing Gaps

**[GOVERNANCE]** Formally approved and documented the definitive responsive desktop model in `BRAND_SYSTEM.md`: Viewport-height lock (`height: 100dvh; overflow: hidden`) is active above 768px with a native vertical scrollbar enabled *only* on the right column (`.right-col`). This preserves the premium, zero-scroll visual balance for the hero branding blocks while offering flawless vertical legibility for the editorial grid panels at any height.

**[LAYOUT]** Re-implemented desktop viewport lock (`height: 100dvb; overflow: hidden;`) above 768px as requested by the user, ensuring the site fits entirely on a single screen on desktop without pagination or scroll.

**[LAYOUT]** Mobile (< 768px) retains natural vertical scrolling.

**[LAYOUT]** Eliminated excessive blank spaces in the left column between the "Message Us" CTA and "Networks" section by changing `.left-col`'s layout on desktop to `justify-content: flex-start` with a controlled, dynamic height-based gap (`var(--space-xl)`).

**[LAYOUT]** Removed fixed row fractional heights (`repeat(4, 1fr)`) and `overflow: hidden` on desktop panel items. Refactored `.right-col` to use `display: flex; flex-direction: column` on desktop (and cleaned up mobile template overrides) so heights are allocated adaptively based on each grid's natural content size. This guarantees that each panel occupies its own distinct block with separate border lines, eliminating any possibility of visual overlapping or "Why Us" blending into "Founding Mandates" as reported by the user. Explicitly defined and named each grid in both the HTML and CSS (`.grid-mandates`, `.grid-why`, `.grid-pipeline`, and `.grid-terms`) with `min-block-size: fit-content` and `overflow: visible` to ensure absolute containment.

**[TOKENS]** Re-integrated height-based vertical tokens on desktop and static tokens on mobile to guarantee strict layout fit.

**[BRAND]** Removed the colored background (`var(--surface)`) from the "Why Us" panel (`.panel-why`), making it transparent/blend with the page background for a cleaner, ultra-minimalist aesthetic as requested by the user. Updated `BRAND_SYSTEM.md` to reflect this visual governance adjustment.

**[BRAND]** Standardized panel typography: aligned all labels (`.panel-label`, `.term-name`) to the exact same sizing, weights, line-heights, letter-spacing, and word-spacing. Unified all secondary headings (`.mandate-card h3`, `.pipeline-name`) and all body/description copy (`.mandate-card p`, `.grid-why p`, `.pipeline-desc`, `.pipeline-item`) to use identical font sizes, line heights, letter-spacings, and word-spacings across all grids for perfect typographic symmetry.

**[CONTENT]** Expanded and updated "Our Terms" pricing matrix to match the new commercial terms requested by the user:
  - Updated the fee structure to: `15% · 25%` / `Remote · In-Person` (15% for remote, 25% for in-person).
  - Removed the separate `In-Person SF` / `Location Focus` cell.
  - Added `Net 30 Days` / `Payment Window` (payment terms within 30 days).
  - Added `90 Days` / `Replacement Guarantee` (90-day talent replacement guarantee if they leave).
  - Added `Up to 1/3` / `Fee Paid in Equity` (option to pay up to 1/3 of our recruitment fee in company stocks/equity to make it clear that this applies to the recruitment fee rather than the candidate's compensation).
  - Updated the footer center parameters copy to: `SF & Remote Option • $150K Base Floor • 15% / 25% Fee Structure`.
  Updated `BRAND_SYSTEM.md` Section 9.1 to reflect these new locked business parameters.

**[CONTENT]** Expanded "Founding Mandates" from 4 to 6 items to include the two most common founding startup roles:
  - Added `05 / Founding Designer`: "Zero-to-one product architects."
  - Added `06 / Founding Product Manager`: "First product roadmap owners."
  - Added a high-impact editorial lead paragraph: *"The essential hiring blueprint for early-stage startups. Securing high-signal talent for your core founding team is not about filling headcount — it is about underwriting your venture’s future."*
  Updated `BRAND_SYSTEM.md` Section 9.2 content inventory to document these new active mandates.

**[BRAND]** Removed the horizontal header borders (lines underneath) directly below the panel labels for "Pipeline" and "Our Terms" to make the editorial grid layout feel lighter and more cohesive.

**[LAYOUT]** Redesigned the "Our Terms" section to use a premium, left-aligned tabular row layout instead of a grid of columns. Each cell is now structured with a fixed left column (`clamp(110px, 15vw, 140px)`) for metrics/values and a fluid right column (`minmax(0, 1fr)`) for parameters/names, perfectly aligning titles and subtitles with zero text wrapping or selective line breaks on all device screens. This mirrors the design of the "Pipeline" section for stunning typographic symmetry.

**[LAYOUT]** Enforced absolute layout containment and overflow safety: added `overflow-wrap: break-word` globally in the CSS reset to prevent long text overflows.

**[FIX]** Solved the missing "Pipeline" (and other panels') titles bug on short viewports. Changed `.section-panel` alignment from `justify-content: center` to `justify-content: flex-start`, ensuring titles are always anchored safely at the top padding boundary of each panel and never clipped by `overflow: hidden`.

---

## [2.0.0] — 2026-06-20

### Responsive Architecture Refactor (breaking: layout strategy)

**[LAYOUT]** Dropped `100dvh + overflow:hidden` viewport lock. Page now uses natural scroll (`min-block-size: 100dvb` on html, `flex: 1` on main). Content breathes instead of clipping.

**[LAYOUT]** Replaced all `@media` breakpoint-per-panel rules with **container queries** (`container-type: inline-size`). Three named containers: `left-col`, `right-col`, `panel`. Two `@container` rules handle edge-case collapses (pipeline at < 320px, terms at < 300px). Only **one** `@media` rule remains — the gross layout flip at 680px viewport.

**[LAYOUT]** Introduced `@layer reset, tokens, layout, components, utilities` cascade layers for predictable override order without BEM or specificity wars.

**[LAYOUT]** `mandates-grid` and `terms-grid` converted to `repeat(auto-fit, minmax(..., 1fr))` — browser decides column count, no hardcoded breakpoints. Mandates collapse from 2→1 column below 340px panel width; Terms below 300px panel width.

**[LAYOUT]** `pipeline-item` grid changed to `2rem max-content minmax(0, 1fr)` — pipeline name never clips, description truncates with ellipsis at narrow widths.

**[TOKENS]** Spacing tokens renamed to `--space-{N}` (N = px value at mid-range) and converted to `vi`-unit preferred values for better logical-property alignment. New `--pad-inline` token unifies all horizontal padding.

**[TOKENS]** Typography now uses `cqi` (container query inline units) inside panels, bounded by `clamp()`. Font sizes scale relative to the panel's own width, not the viewport.

**[BRAND]** Added `text-wrap: balance` to headings, labels, and footer center — prevents orphan words on wrap.

**[BRAND]** Added `prefers-reduced-motion` utility layer that suppresses all transitions for users who request it.

**[FIX]** `min-inline-size: 0` added to all flex/grid children that contain text — prevents the common CSS overflow bug where flex items refuse to shrink below their content size.

**[FIX]** Header is now `position: sticky` on desktop (stays visible when right column scrolls); reverts to `static` on mobile to save vertical space.

---

## [1.3.1] — 2026-06-20

### Pipeline Layout Refinement

**[LAYOUT]** Removed vertical dividers (`border-left`) inside desktop pipeline grid to prevent squeezed layouts on narrower widths.

**[LAYOUT]** Merged stage numbers and headings onto a single line (`<h3><span class="pipeline-num">01 /</span>Hunting</h3>`) saving vertical height.

**[LAYOUT]** Changed grid columns to a flexible flex row layout (`display: flex; justify-content: space-between`) with subtle horizontal gaps to allow the text blocks to layout naturally.

**[LAYOUT]** Configured mobile media query overrides to convert `.pipeline-grid` into a column flex vertical stack.

---

## [1.3.0] — 2026-06-20

### Layout Refactoring, Spacing & Content Expansion

**[LAYOUT]** Standardized spacing system using 8px-based spacing tokens (`--space-xs` to `--space-xl` and `--space-x-sm` to `--space-x-xl`). On desktop, vertical tokens utilize a dynamic `clamp()` system tied to viewport height (`vh`) and width (`vw`) to prevent zero-scroll viewport breaks when screen height shrinks. On mobile, these values override to clean static pixel sizes.

**[LAYOUT]** Restructured `OUR TERMS` cell padding using `--space-md` (`24px` padding on all sides) to prevent text/data from being squeezed against border grids.

**[LAYOUT]** Implemented full responsiveness for mobile screens (`< 768px`):
- Restores natural page scrolling (`overflow-y: auto`, `height: auto` on document elements).
- Layout collapses to vertical column stack (`flex-direction: column`).
- Inner panels, mandates, pipeline, and terms grids flatten to single columns.
- Desktop layout remains locked in zero-scroll mode.

**[CONTENT]** Renamed ecosystem badge list title to `NETWORKS`.

**[CONTENT]** Expanded brand portfolio to 20 firms, stripping suffixes (e.g., "Alum") for a cleaner look. Included companies: Y Combinator, 500 Startups, Cubo Itaú, Stripe, Plaid, Brex, Vercel, Figma, Notion, OpenAI, Airbnb, Uber, Coinbase, Revolut, HashiCorp, Snowflake, Datadog, Linear, Retool, Deel.

---

## [1.2.0] — 2026-06-20

### Brand Color Migration: "Minimalismo Vibrante (Vermelho Premium)"

**[BRAND]** Migrated brand visual identity with new design tokens:
- `--bg` background: `#FBFBFA` &rarr; `#FAFAFA`
- `--surface` surface elements: `#FFFFFF` &rarr; `#F2EBEA`
- `--text-main` primary text: `#111111` &rarr; `#1A1A1A`
- `--border-sharp` structural borders: `#111111` &rarr; `#1A1A1A`
- `--flanboyant-fire` brand accent: `#FF2A00` &rarr; `#E02D1B`
- Footer background: `#000000` &rarr; `#1A1A1A`

**[BRAND]** Re-encoded inline SVG favicon to use the new red-orange accent `#E02D1B`.

**[BRAND]** Updated visual specs, color guidelines, component libraries, and tables in `BRAND_SYSTEM.md`.

---

## [1.1.0] — 2026-06-20

### PIPELINE section added

**[LAYOUT]** Right column grid updated: `1.1fr 0.9fr 1fr` → `1.05fr 0.85fr 0.7fr 0.85fr` (4 rows, zero-scroll maintained).

**[BRAND]** New component `PIPELINE` added to Brand System (section 5.7). Spec documented.

**[CONTENT]** Pipeline stages (5): Hunting → Shortlist → Internal Loop → Work Trial → Offer.

**[GOVERNANCE]** Tailwind CSS requested and **rejected** — Brand System (vanilla CSS, zero dependencies) prevailed. Decision logged per governance protocol.

---

## [1.0.0] — 2026-06-20

### Initial Production Release

**[BRAND]** Established complete Brand System Design in `BRAND_SYSTEM.md`.

**[LAYOUT]** Built single-page zero-scroll Swiss editorial layout:
- Horizontal split-screen: left hero (1.15fr) + right editorial panels (1fr)
- Right column: 3 asymmetric rows (1.1fr · 0.9fr · 1fr)
- Header: `clamp(60px, 8vh, 80px)` with 2px black separator
- Footer: compressed black strip `clamp(40px, 6vh, 56px)`

**[BRAND]** Locked design tokens:
- `--bg: #FBFBFA` (raw off-white)
- `--flanboyant-fire: #FF2A00` (brand accent)
- `--text-main: #111111`
- `--text-muted: #5A5A57`
- Font: Helvetica Neue → Inter fallback

**[BRAND]** Logo: fire dot (■) + `flanboyant` lowercase wordmark, weight 800.

**[BRAND]** Favicon: base64 inline SVG — red square (#FF2A00) + white 'F'.

**[CONTENT]** Hero H1: *"The talent partner for your core founding team."*  
Fire accent on `founding team.`

**[CONTENT]** Ecosystem badges (7): Y Combinator, 500 Global, Cubo Itaú, Stripe Alum, Plaid Alum, Brex Alum, Vercel Alum.

**[CONTENT]** Founding Mandates (4): Engineers, GTM & AEs, Chief of Staff, People Ops.

**[CONTENT]** Business parameters locked: In-Person SF · $150K base · 20%-25% fee.

**[SEO]** Full SEO head: title, meta description, Open Graph, Twitter Cards, canonical, robots.

**[FIX]** Favicon migrated from raw inline SVG string to base64 encoding to avoid HTML parser ambiguity.

---

*To add an entry: describe what changed, why, and tag the type. If the change affects `BRAND_SYSTEM.md`, note the section updated.*
