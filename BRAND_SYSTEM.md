# flanboyant — Brand System Design

> **Version:** `1.4.0`  
> **Snapshot date:** 2026-06-24  
> **Status:** ✅ Active — Source of Truth

This document is the **single source of truth** for all visual and brand decisions on `flanboyant.com`. Any change to the site's appearance must either comply with this system or trigger a governed update to this document.

---

## Governance Protocol

> [!IMPORTANT]
> Before implementing any visual change, check if it is supported by this System Design.

### Decision Tree for Visual Changes

```
New visual change requested
        │
        ▼
Is this change defined in BRAND_SYSTEM.md?
        │
   YES ─┤─ NO
        │       │
        │       ▼
        │   Does the change CONFLICT with the system?
        │       │
        │   YES ─┤─ NO (new pattern, not covered)
        │       │       │
        │       │       ▼
        │       │   Implement the change AND
        │       │   ADD it to BRAND_SYSTEM.md as a new rule.
        │       │   Log in CHANGELOG.md.
        │       │
        │       ▼
        │   DECISION REQUIRED — ask:
        │   "Which should prevail: the new change or the Brand System?"
        │       │
        │   NEW CHANGE PREVAILS       SYSTEM PREVAILS
        │       │                         │
        │       ▼                         ▼
        │   Update BRAND_SYSTEM.md    Do NOT implement.
        │   THEN implement change.    Log decision in CHANGELOG.md.
        │   Log in CHANGELOG.md.
        │
        ▼
Implement change.
Log in CHANGELOG.md.
```

---

## 1. Brand Identity

### 1.1 Brand Name
- **Wordmark:** `flanboyant`
- **Casing rule:** Always **lowercase**, always set in the primary typeface
- **Tagline:** `founding teams`
- **Full brand expression:** `flanboyant — founding teams`
- **Separator:** em-dash (` — `), not hyphen

### 1.2 Brand Voice
- Precise, direct, founder-to-founder
- No marketing fluff. No exclamation marks.
- All-caps labels for structural UI elements (`FOUNDING MANDATES`, `WHY US`)
- Lowercase for brand name always
- Sentence case for body copy

### 1.3 Favicon
- **Shape:** Sharp square (no border-radius)
- **Background:** `#E02D1B` (brand fire)
- **Mark:** White capital `F`, sans-serif, weight 900, size 65/100
- **Format:** Inline SVG, base64-encoded in `<link>` tag

---

## 2. Color Palette

> [!IMPORTANT]
> These exact hex values are locked. Any deviation requires a BRAND_SYSTEM.md update.

### 2.1 Core Palette

| Token | Hex | Role | Usage |
|---|---|---|---|
| `--bg` | `#FAFAFA` | Page background | `html`, `body`, `header`, `.panel-terms` |
| `--surface` | `#F2EBEA` | Elevated surface | `.logo-badge` bg |
| `--text-main` | `#1A1A1A` | Primary text & borders | All headings, `.big-cta` bg, structural borders |
| `--text-muted` | `#5A5A57` | Secondary text | `.hero-desc`, `.mandate-card p`, `.term-name` |
| `--border-sharp` | `#1A1A1A` | Structural grid lines | All 2px and 1px border rules |
| `--flanboyant-fire` | `#E02D1B` | Brand accent | Logo dot, labels, highlights, hover CTAs, accented hero text |

### 2.2 Fixed Colors (Non-tokenized)

| Value | Role | Location |
|---|---|---|
| `#1A1A1A` | Footer background | `footer` element |
| `#7A7A78` | Footer text & links | `footer`, `.footer-link` |
| `#FFFFFF` | Footer center text, hover text | `.footer-center`, `.big-cta:hover`, `.logo-badge:hover` |

### 2.3 Color Rules
- **No gradients.** Flat fills only.
- **No opacity/transparency.** Solid colors only.
- **Accent color (`--flanboyant-fire`)** is used exclusively for: labels, hover states, hero text highlights, logo dot, numbered markers. Never for body text.
- **Hover state model:** `#1A1A1A` → `#E02D1B` (for CTAs), `#F2EBEA` bg → `#1A1A1A` bg (for badges)

---

## 3. Typography

### 3.1 Typeface Stack

```css
--font-main: "Helvetica Neue", "Inter", -apple-system, BlinkMacSystemFont, Arial, sans-serif;
```

- **Primary:** Helvetica Neue (system-installed)
- **Web fallback:** Inter (loaded from Google Fonts, weights: 400, 500, 700, 800, 900)
- **Emergency fallback:** -apple-system, BlinkMacSystemFont, Arial, sans-serif

### 3.2 Google Fonts Load

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;700;800;900&display=swap" rel="stylesheet">
```

### 3.3 Typography Scale

| Role | `font-size` | `font-weight` | `letter-spacing` | `line-height` |
|---|---|---|---|---|
| Logo wordmark | `clamp(20px, 2.5vw, 26px)` | 800 | `-0.05em` | — |
| Hero title (`h1`) | `clamp(36px, 4.8vw, 64px)` | 800 | `-0.05em` | `0.95` |
| Term value | `clamp(18px, 2.5vw, 28px)` | 800 | `-0.03em` | `1` |
| Mandate heading (`h3`) | `clamp(13px, 1.5vw, 16px)` | 700 | — | `1.2` |
| Body / Hero desc | `clamp(14px, 1.5vw, 17px)` | 400 | `-0.01em` | `1.4` |
| Why Us body | `clamp(13px, 1.6vw, 16px)` | 400 | — | `1.45` |
| Header CTA / Big CTA | `clamp(11px, 1.2vw, 13px)` | 700 | `+0.05em` | — |
| Section labels | `clamp(9px, 1vw, 11px)` | 700 | `+0.08em` | — |
| Term label | `clamp(9px, 1vw, 11px)` | 700 | `+0.05em` | — |
| Badge text | `clamp(10px, 1.1vw, 12px)` | 600 | — | — |
| Mandate number | `clamp(12px, 1.3vw, 14px)` | 700 | — | — |
| Footer text | `clamp(9px, 1.1vw, 11px)` | 500 | `+0.05em` | — |

### 3.4 Typography Rules
- **No rounded corners.** Ever. `border-radius: 0 !important` globally.
- **Global letter-spacing:** `-0.02em` on `body` (tightened Swiss editorial rhythm)
- **Font rendering:** `-webkit-font-smoothing: antialiased`, `-moz-osx-font-smoothing: grayscale`
- **`text-box: trim-both cap alphabetic`** applied to `.logo-badge` for precise cap-height alignment (progressive enhancement; safe for non-supporting browsers)
- All UI labels are **uppercase**. Brand name (`flanboyant`) is **always lowercase**.

---

## 4. Spacing & Layout Grid

### 4.1 Viewport Lock
- **Desktop (>= 768px):** Viewport height is strictly locked at 100% of viewport (`height: 100dvh; overflow: hidden`). The header, left column (Hero & Networks), and footer remain fixed in place. The right column (`.right-col`) is a dedicated scrollable area (`overflow-y: auto`) that houses the editorial panels. This keeps the page perfectly anchored and zero-scroll-like as a whole, while ensuring the rich panel content is fully readable and scrollable on any viewport size.
- **Mobile (< 768px):** Converts to a single-column vertical flow. The entire page uses natural browser vertical scrolling (`height: auto; overflow-y: auto`).

### 4.2 Spacing System (8px Tokens)

We use a strict 8px increment spacing scale for UI structure and text rhythms. On desktop, vertical tokens scale dynamically using `clamp()` to prevent zero-scroll viewport breaks when screen height contracts:

**Vertical Spacing Tokens (Height-based on Desktop, Static on Mobile):**
- `--space-xs`: `clamp(6px, 0.8vh, 8px)` (chips gaps, minor margins)
- `--space-sm`: `clamp(10px, 1.5vh, 16px)` (margins, gap between small assets)
- `--space-md`: `clamp(16px, 2.5vh, 24px)` (hero gap, terms padding, pipeline gaps)
- `--space-lg`: `clamp(20px, 3.5vh, 32px)` (panel vertical padding)
- `--space-xl`: `clamp(24px, 4.5vh, 48px)` (left column vertical padding)

**Horizontal Spacing Tokens (Width-based on Desktop, Static on Mobile):**
- `--space-x-sm`: `clamp(12px, 2vw, 16px)`
- `--space-x-md`: `clamp(16px, 3vw, 24px)`
- `--space-x-lg`: `clamp(20px, 4vw, 32px)`
- `--space-x-xl`: `clamp(24px, 5vw, 48px)` (left/right structural horizontal padding)

### 4.3 Padding System

All padding uses Spacing Tokens:

| Zone | Desktop Padding | Mobile (< 768px) Padding |
|---|---|---|
| Header | `0 var(--space-x-xl)` | `var(--space-sm) var(--space-md)` |
| Left column | `var(--space-xl) var(--space-x-xl)` | `var(--space-lg) var(--space-md)` |
| Right panels | `var(--space-lg) var(--space-x-xl)` | `var(--space-lg) var(--space-md)` |
| Footer | `0 var(--space-x-xl)` | `var(--space-md)` |

### 4.4 Gap System

| Element | Gap Spec |
|---|---|
| Logo area (dot + text) | `8px` |
| Hero block internal | `var(--space-md)` |
| CTA container top margin | `var(--space-sm)` |
| Networks badge row | `var(--space-xs)` |
| Mandates 2x2 grid | `var(--space-sm)` vertical · `var(--space-md)` horizontal |
| Mandate card internal | `4px` |
| Term cell internal | `6px` |
| Footer right links | `16px` |
| Footer left internal | `12px` |

### 4.5 Border System

| Usage | Spec |
|---|---|
| Major structural separators | `2px solid #1A1A1A` |
| Terms grid top, term cell dividers | `1px solid #1A1A1A` |
| Badge borders | `1px solid #1A1A1A` |
| Header CTA button border | `2px solid #1A1A1A` |

**Rule:** No `border-radius` anywhere. Zero. `border-radius: 0 !important` is set globally.

---

## 5. Component Library

### 5.1 Logo

```html
<div class="logo-area">
  <div class="logo-dot"></div>        <!-- 10–14px fire square -->
  <div class="logo-text">flanboyant</div>
</div>
```

**Spec:**
- Logo dot: `clamp(10px, 1.2vw, 14px)` square, color `#E02D1B`
- Wordmark: lowercase, weight 800, `clamp(20px, 2.5vw, 26px)`, color `#1A1A1A`
- Gap between dot and text: `8px`

### 5.2 Header CTA Button (`.header-link`)

**Default state:**
- Border: `2px solid #1A1A1A`
- Background: transparent
- Text: `#1A1A1A`, uppercase, weight 700, `letter-spacing: 0.05em`
- Padding: `8px 16px`
- Font size: `clamp(11px, 1.2vw, 13px)`

**Hover state:**
- Background: `#E02D1B`
- Text: `#FFFFFF`
- Border: `#E02D1B`
- Transition: `all 0.15s ease-in-out`

### 5.3 Primary CTA Button (`.big-cta`)

**Default state:**
- Background: `#1A1A1A`
- Text: `#FFFFFF`, uppercase, weight 700, `letter-spacing: 0.05em`
- Padding: `clamp(12px, 2vh, 18px)` vertical · `clamp(24px, 3vw, 40px)` horizontal
- Font size: `clamp(11px, 1.2vw, 13px)`
- No border

**Hover state:**
- Background: `#E02D1B`
- Transition: `all 0.15s ease-in-out`

### 5.4 Section Label (`.panel-label`)

- Color: `#E02D1B`
- Text: uppercase, weight 700
- Font size: `clamp(9px, 1vw, 11px)`
- Letter-spacing: `0.08em`
- Margin-bottom: `clamp(12px, 2vh, 20px)`

### 5.5 Networks Section (`.ecosystem-container`) — **Updated v1.3.0**

- **Title:** `NETWORKS` (uppercase, Fire Accent)
- **Container padding-top:** `var(--space-md)`
- **Title margin-bottom:** `var(--space-sm)`

**Ecosystem Badge (`.logo-badge`):**
- **Default state:**
  - Border: `1px solid #1A1A1A`
  - Background: `#F2EBEA`
  - Text: `#1A1A1A`, weight 600
  - Font size: `clamp(10px, 1.1vw, 12px)`
  - Padding: `clamp(4px, 0.8vh, 8px)` vertical · `clamp(10px, 1vw, 14px)` horizontal
  - `text-box: trim-both cap alphabetic`

**Hover state:**
- Background: `#1A1A1A`
- Text: `#FFFFFF`
- Transition: `all 0.15s ease-in-out`

### 5.6 Right-Column Panel Grid System (`.section-panel` / `.panel-cols`)

All four right-column panels (Founding Mandates, Why Us, Pipeline, Our Terms) follow an identical, per-pixel standardized layout grid and typography scale for unified Swiss editorial symmetry.

**Hierarchy Model:**
```
[panel-label]        ← var(--fs-eyebrow), fire color, weight 700, uppercase
[panel-desc]         ← var(--fs-desc), text-main, weight 500, line-height 1.45
──────────────────────────────────────────────────────────────────────────
[col 1]              │ [panel-divider] │ [col 2]
- [item 1]           │ 2px solid line  │ - [item 4]
  - [item-num]       │                 │   - [item-num]
  - [item-title]     │                 │   - [item-title]
  - [item-sub]       │                 │   - [item-sub]
- [item 2]           │                 │ - [item 5]
```

**Core Classes:**
- `.section-panel`: Standard container with `border-bottom: 2px solid var(--border-sharp)`. Last panel has `border-bottom: none`.
- `.panel-label`: Section eyebrow, uppercase label.
- `.panel-desc`: Leading introductory text block.
- `.panel-cols`: Two-column grid (`grid-template-columns: 1fr auto 1fr`) with a `panel-divider` (2px solid black line) in between.
- `.col`: Flex vertical stack of items with standard `clamp(10px, 1.6vh, 16px)` gaps.
- `.col-heading`: Section sub-header inside a column (Why Us lists).
- `.item`: Container for list elements (number + title + subtitle/description).
  - `.item-num`: Step/mandate index number.
  - `.item-title`: Term/stage/mandate primary name.
  - `.item-sub`: Secondary descriptive text.
- `.why-item`: Bullet text for list comparisons in Why Us.

**Adaptive Fallback (< 420px):**
On narrow viewport widths or container dimensions, the split columns collapse to a single column vertical flow. The vertical 2px line (`.panel-divider`) rotates to become a horizontal 1px separator:
```css
@container panel (max-width: 420px) {
  .panel-cols { grid-template-columns: 1fr; gap: var(--space-md) 0; }
  .panel-divider { inline-size: 100%; block-size: 1px; }
}
```

### 5.7 Footer Strip

- Height: `clamp(40px, 6vh, 56px)`
- Background: `#1A1A1A` (not `--bg`, not `--text-main`)
- Text color: `#7A7A78`
- Center text: `#FFFFFF`, weight 700
- Font: uppercase, `clamp(9px, 1.1vw, 11px)`, `letter-spacing: 0.05em`
- Layout: 3-zone `space-between` (left: copyright · center: key params · right: social links)

### 5.8 Mode Switch

- **Layout:** Flex horizontal container (`.mode-switch`) with 2px solid `#1A1A1A` border.
- **Buttons (`.mode-btn`):** Uppercase, weight 700, font size `clamp(10px, 1.1vw, 12px)`, `letter-spacing: 0.06em`, no border, padding `clamp(6px, 1vh, 10px)` vertical · `clamp(14px, 2vw, 22px)` horizontal.
- **Divider:** Sibling buttons are separated by a `border-left: 2px solid var(--border-sharp)`.
- **Active state:** Background `#1A1A1A`, text `#FFFFFF`.
- **Inactive hover state:** Background `#F2EBEA`, text `#1A1A1A`.

---

## 6. Interaction Model

| Element | Default | Hover | Transition |
|---|---|---|---|
| `.header-link` | `#1A1A1A` border + transparent bg | `#E02D1B` bg + white text | `0.15s ease-in-out` |
| `.big-cta` | `#1A1A1A` bg + white text | `#E02D1B` bg + white text | `0.15s ease-in-out` |
| `.logo-badge` | `#F2EBEA` bg + `#1A1A1A` text + `#1A1A1A` border | `#1A1A1A` bg + white text | `0.15s ease-in-out` |
| `.footer-link` | `#7A7A78` | `#FFFFFF` | `0.15s ease-in-out` |
| `.mode-btn:not(.active)` | transparent bg + muted text | `#F2EBEA` bg + `#1A1A1A` text | `0.15s` |

**Rules:**
- All transitions are `0.15s ease-in-out` or simple `0.15s`. No exceptions without system update.
- No animations on page load.
- **JavaScript Interaction:** Snappy, instant toggle of the root `[data-mode]` attribute between `"candidates"` and `"startups"`. Classes `.for-candidates` and `.for-startups` are used to control conditional element visibility (`display: none` for non-active states). On toggle, both columns scroll back to the top (`scrollTop = 0`).

---

## 7. Responsive Behaviour

### 7.1 Breakpoints

- **Desktop (>= 768px):** Horizontal split-screen layout. Viewport height is locked (`height: 100dvh; overflow: hidden`). Only the right column (`.right-col`) has an independent vertical scrollbar to allow panel contents to scroll smoothly.
- **Mobile (< 768px):** Converts to single column flex-flow stack (`flex-direction: column`). Scrolling is enabled naturally on the entire page (`overflow-y: auto`, `height: auto` on document structures).

### 7.2 Safety Clamp (max-height: 680px)
Applied on desktop screen sizes when viewport height is critically small:
```css
@media (max-height: 680px) {
  .hero-desc { -webkit-line-clamp: 2; }       /* Truncate to 2 lines */
  .mandate-card p { -webkit-line-clamp: 1; }  /* Truncate to 1 line */
}
```

---

## 8. SEO & Meta

| Field | Value |
|---|---|
| `<title>` | `flanboyant — founding teams` |
| `meta description` | `flanboyant is the premier founder-to-founder talent partner for elite seed and Series A startups. We secure high-signal founding engineers, GTM leaders, and chiefs of staff with zero recruitment overhead.` |
| `og:title` | `flanboyant — founding teams` |
| `og:image` | `https://flanboyant.com/og-image.png` |
| `twitter:card` | `summary_large_image` |
| `robots` | `index, follow` |
| `canonical` | `https://flanboyant.com` |

---

## 9. Copy & Content Rules

### 9.1 Fixed Business Parameters
These values are locked and must not be changed in the site without explicit business decision:

```
Location:         San Francisco (with Remote Option)
Base salary floor: $150K
Contingency fee:  15% Remote · 25% In-Person
Payment terms:    Net 30 Days
Replacement:      90 Days Guarantee
Equity option:    Up to 1/3 Fee Paid in Stocks
Contact method:   WhatsApp (wa.me link)
```

### 9.2 Current Content Inventory (Dual-Mode)

#### Candidates Mode (Default Mode)

**H1 Hero:**
> The move that defines the **rest of your career.**

*(italic/highlight = `<span>` with `--flanboyant-fire` color)*

**Hero description:**
> We match high-signal operators with the founding teams building the next generation of breakout companies. One role. Real equity. Direct line to the founder.

**Ecosystem Title:**
> Alumni From

**The Roles (3×2 grid on desktop):**
> Six founding-level mandates. Each one the kind of move that reshapes a career — not just a next job.

| # | Title | Description |
|---|---|---|
| 01 | Founding Engineer | Own the architecture from commit one. Real equity. Real ownership. |
| 02 | Founding AE / GTM Lead | Build the first pipeline. Close the first deals. Shape the playbook. |
| 03 | Chief of Staff | Run the org alongside the founder. Total visibility from day one. |
| 04 | Head of People | Set the hiring bar and culture before anyone else does. |
| 05 | Founding Designer | Own product and brand identity from v1. |
| 06 | Founding PM | Ship the first roadmap. No committee. No bureaucracy. |

**What You Get:**
- **What This Isn't:** A corporate ladder climb. A 2% annual raise cycle. A role where someone else owns the roadmap. Another recruiter spamming your inbox.
- **What It Is:** $150k+ base floor. Real equity upside. Direct line to the founder, not to HR. Work trial before you commit — no black holes. A reference that opens every next door.

**Who We Place:**
- **01 / Track Record of Shipped Work:** Demonstrable output — code, revenue, product, culture. Not tenure.
- **02 / Ownership Mentality:** You've taken a problem from zero to working, without being asked twice.
- **03 / Startup-Ready:** Either you've been in a fast-moving environment, or you're built for one.
- **04 / Long-term Thinker:** You want equity, not just a salary. You're thinking in decades.

**How It Works:**
- **01 / You Reach Out:** A 30-min call with us. No resume required to start.
- **02 / We Match You:** 1–2 introductions to founders. Handpicked, not a pipeline blast.
- **03 / Work Trial:** 1–5 day paid trial on real scope. You evaluate them too.
- **04 / Signed Offer:** Comp, equity, relocation and visa support as needed.

**Footer center strip:**
> SF & Remote &bull; $150K Base Floor &bull; Real Equity Upside

---

#### Startups Mode

**H1 Hero:**
> The talent partner for your core **founding team.**

*(italic/highlight = `<span>` with `--flanboyant-fire` color)*

**Hero description:**
> We operate founder-to-founder to secure high-signal human capital for elite seed and Series A ventures. No recruiting overhead. Direct cap-table alignment.

**Ecosystem Title:**
> Networks

**Founding Mandates (3×2 grid on desktop):**
> Six roles we place across the founding bench, each sourced against a track record of shipped, measurable work.

| # | Title | Description |
|---|---|---|
| 01 | Founding Engineer | Owns architecture from commit one. |
| 02 | Founding AE / GTM Lead | Builds and closes the first pipeline. |
| 03 | Chief of Staff | Extends founder bandwidth across the org. |
| 04 | Head of People | Sets comp, hiring bar, and culture early. |
| 05 | Founding Designer | Owns product and brand from v1. |
| 06 | Founding PM | Sets the first roadmap and ships it. |

**Why Us:**
> Generalist agencies optimize for resume volume. We screen exclusively for proven execution and shipping speed.

**Pipeline:**
- **01 / Sourcing:** Targeted outreach into our networks.
- **02 / Shortlist:** 3–4 vetted, reference-checked candidates.
- **03 / Interview Loop:** Runs on your team's process.
- **04 / Work Trial:** 1–5 day paid trial on real scope.
- **05 / Offer & Close:** Comp, equity, relocation and visa support.

**Our Terms:**
- **15% · 25%:** Placement fee — remote · in-person
- **$150k:** Minimum base salary covered
- **Net 30:** Invoice payment window
- **90 Days:** Free replacement guarantee
- **Up to 1/3:** Of fee payable in equity

**Footer center strip:**
> SF & Remote Option &bull; $150K Base Floor &bull; 15% / 25% Fee Structure

---

## 10. Snapshot History

### v1.4.0 — 2026-06-24 (Dual Audience Modes & Mode Switch)

**Change:** Interactive Candidate/Startup view modes with a modern toggle switch.
- **Audience Isolation:** Split layout and copy into `.for-candidates` and `.for-startups` blocks. Default view is Candidates.
- **Component Pattern:** Added a customized flat Mode Switch (`.mode-switch`, `.mode-btn`) with no border radius in the sticky header.
- **Interaction Rules:** Integrated native JavaScript toggle logic that manages root `[data-mode]` state, button states, and scrolls columns back to top upon view change.
- **Copy Alignment:** Authored rich, career-defining candidate copy covering "The Roles", "What You Get" (with comparative "What It Is/Isn't" blocks), "Who We Place", and "How It Works".

---

### v1.3.0 — 2026-06-20 (Refactoring & Layout Update)

**Change:** Spacing and responsive layout update.
- Spacing: 8px-based CSS spacing tokens.
- Layout: Zero-scroll on desktop, fluid vertical flow with native scrolling on mobile (< 768px).
- Matrix: Generous cell padding (`var(--space-md)`) added to `.term-cell`.
- Content: Renamed section to `NETWORKS`, stripped suffixes like "Alum", expanded brand portfolio to 20 firms.

---

### v1.2.0 — 2026-06-20 (Minimalismo Vibrante / Vermelho Premium)

**Change:** Updated core brand colors.
- `--bg`: `#FAFAFA`
- `--surface`: `#F2EBEA`
- `--text-main`: `#1A1A1A`
- `--border-sharp`: `#1A1A1A`
- `--flanboyant-fire`: `#E02D1B`
- Footer background: `#1A1A1A`
- Favicon: `#E02D1B` background

---

### v1.1.0 — 2026-06-20 (PIPELINE section added)

**Change:** New `PIPELINE` section inserted between WHY US and OUR TERMS.

**Governance decisions recorded:**
- **Tailwind CSS requested → REJECTED**: Brand System mandates vanilla CSS. No build dependencies. Decision: Brand System prevailed.
- **4th grid row added**: Right column grid updated from `1.1fr 0.9fr 1fr` to `1.05fr 0.85fr 0.7fr 0.85fr` to maintain zero-scroll.
- **New component added** to Brand System: Section 5.7 Pipeline.

**Token snapshot:** unchanged from v1.0.0

**Layout snapshot:**
- Grid rows: `1.05fr 0.85fr 0.7fr 0.85fr` (4 rows)
- Zero scroll: maintained ✅

**Components added:**
- [x] Pipeline 5-column stage grid

---

### v1.0.0 — 2026-06-20 (Initial Production Snapshot)

**State:** First production-ready version of the site.

**Token snapshot:**
```css
--bg:               #FBFBFA
--surface:          #FFFFFF
--text-main:        #111111
--text-muted:       #5A5A57
--border-sharp:     #111111
--flanboyant-fire:  #FF2A00
--font-main:        "Helvetica Neue", "Inter", -apple-system, BlinkMacSystemFont, Arial, sans-serif
```

**Layout snapshot:**
- Grid: `1.15fr 1fr` (left:right split)
- Right rows: `1.1fr 0.9fr 1fr`
- Header height: `clamp(60px, 8vh, 80px)`
- Footer height: `clamp(40px, 6vh, 56px)`
- Zero scroll: confirmed ✅
- Page height = viewport height at 1336×760: confirmed ✅

**Components present:**
- [x] Logo (dot + wordmark)
- [x] Header CTA (`Message Us ↗`)
- [x] Hero H1 with fire accent
- [x] Hero description paragraph
- [x] Primary CTA button (`Message Us`)
- [x] Ecosystem badge strip (7 badges)
- [x] Founding Mandates 2×2 grid
- [x] Why Us text block
- [x] Our Terms 3-column matrix
- [x] Footer strip (copyright + params + social)

**Files:**
- `index.html` — 540 lines, 18.3KB
- Favicon: base64 SVG inline
- Fonts: Google Fonts Inter (400, 500, 700, 800, 900)
