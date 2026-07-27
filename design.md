---
version: anydesign-1
name: KLG Weekly Snapshot — Fleet Performance Dashboard
source: /private/tmp/claude-501/-Users-roman/e7412506-d07f-4abe-b723-9cbe950e428a/scratchpad/klg_weekly_snapshot.html
captured_at: 2026-07-26
description: |
  A single-file HTML/CSS/JS weekly ops report for a trucking company, built for owner-operator
  drivers rather than executives. Reads as a restrained, Carbon-Design-System-influenced data
  dashboard: mostly neutral surfaces, category color reserved strictly for data identity
  (trailer type, metric type), never used decoratively. Trustworthy-by-restraint rather than
  flashy — the opposite instinct of a marketing landing page.

colors:
  page: "#f2f5f8"
  surface: "#ffffff"
  layer-1: "#f7f9fb"
  layer-2: "#eef1f5"
  text-primary: "#0c1420"
  text-secondary: "#5b6472"
  text-muted: "#5c636f"
  border: "rgba(11,20,32,0.10)"
  gridline: "#e4e8ec"
  good: "#006300"
  bad: "#c93a3a"
  warning: "#8a5a00"
  warning-bg: "#fbf1de"
  reefer: "#2a78d6"
  dryvan: "#1baf7a"
  gross-accent: "#2F6F4E"
  rpm-accent: "#3D5A99"
  fuel-accent: "#B77A2A"
  deadhead-accent: "#7357A6"
  dark-bg: "#0a1420"
  dark-accent: "#5aa2ef"
  dark-good: "#3ec93e"

typography:
  display:
    fontFamily: "system-ui, -apple-system, 'Segoe UI', sans-serif"
    fontSize: 34px
    fontWeight: 800
  stat:
    fontFamily: "system-ui, -apple-system, 'Segoe UI', sans-serif"
    fontSize: 22px
    fontWeight: 800
  title:
    fontSize: 20px
    fontWeight: 700
  subtitle:
    fontSize: 16px
    fontWeight: 600
  body:
    fontSize: 14px
    fontWeight: 400
  label:
    fontSize: 12px
    fontWeight: 700
    letterSpacing: "6-7%"
  micro:
    fontSize: 11px
  caption:
    fontSize: 10px

spacing:
  base: 4px
  scale: [4, 6, 8, 10, 12, 14, 16, 18, 20, 22, 24]

rounded:
  sm: 8px
  md: 14px
  lg: 16px
  pill: 999px

components:
  hero-card:
    backgroundColor: "tinted per metric family, e.g. {colors.gross-accent} at 4% "
    border: "1px solid, colored at 14-16% alpha"
    rounded: "{rounded.md}"
    boxShadow: "0 4px 14px rgba(20,32,48,0.035)"
    padding: 16px
  trend-card:
    backgroundColor: "{colors.surface}"
    border: "1px dashed {colors.gridline} (was dashed for demo data; now solid-eligible since data is real)"
    rounded: "{rounded.md}"
  trailer-compare-card:
    backgroundColor: "lightened trailer-brand hex at 92%"
    rounded: "{rounded.md}"
    padding: "18px 20px"
  market-card:
    backgroundColor: "{colors.surface}"
    border: "1px solid {colors.gridline}"
    rounded: "{rounded.sm}"
  footer-bar:
    backgroundColor: "{colors.dark-bg} gradient"
    rounded: "{rounded.md}"
  pill-badge:
    rounded: "{rounded.pill}"
    use: "hero-eyebrow, date chips on bar charts — never on data cards"
  delta-indicator:
    textColor: "{colors.good} or {colors.bad} by direction"
    typography: "{typography.label}, weight 700"
  icon-chip:
    backgroundColor: "family hex at ~13% alpha"
    rounded: "{rounded.pill}"
  tab:
    activeBorder: "2px, family accent color"
    inactiveBorder: "1px {colors.gridline}"
  gross-bar-chart-rpm-line-chart-toggle:
    canvas: "560x170 shared viewBox"
  no-approved-gross-data-warning-banner:
    backgroundColor: "{colors.warning-bg}"
    textColor: "{colors.warning}"
---

# Design Analysis — KLG Weekly Snapshot

> Analysis generated with the `anydesign` skill.
> Date: 2026-07-26
> Analysis emphasis: design system (token audit + consistency rules), with reconstruction notes for future sections.

---

## Source

- **Source type**: local file (static HTML, embedded CSS, no build step)
- **Path**: `klg_weekly_snapshot.html`
- **Capture method**: direct read of `:root` CSS custom properties + full-session component history (this file was built and iterated live across one long working session, so component behavior is known first-hand, not just inferred from markup)
- **Detected limitations**: no separate stylesheet to diff against — all styles are inline `<style>`, so "extracted CSS vars" here is the literal source of truth, not an approximation

---

## TL;DR

A restrained, Carbon-Design-System-influenced ops dashboard for truck drivers, not executives — neutral grays dominate, and every chromatic hue is reserved for data identity (trailer type or metric family), never decoration. The system's main risk isn't garishness (it avoids that well) but **semantic color leakage**: the `good` (success/positive-delta) token is reused decoratively for the header date and footer wordmark, which is a small but real inconsistency in an otherwise disciplined token system.

---

## 1. Visual identity

### 1.1 Surface description

**Personality**: restrained, numerate, trustworthy, unglamorous, quietly confident.

**Mood**: a payslip you can trust, not a pitch deck.

**Detectable stylistic references**: IBM Carbon Design System (layer-01/layer-02 nesting, sober grid-first data density) more than Material Design's dynamic-color expressiveness; the categorical color system (reefer=blue, dryvan=green, fuel=amber, deadhead=violet) follows dataviz-skill discipline (fixed hue order, never cycled) rather than a single-brand-accent marketing palette.

**Information density**: balanced — hero cards are spacious, comparison/trend sections are denser, matching a natural "headline → detail" reading order.

**Implicit positioning**: owner-operator truck drivers reading a weekly performance report on a phone, not a boardroom audience — plain language, no jargon, direct $ and %.

**Confidence**: ✅ high (built and reviewed line-by-line across the whole session, not inferred from a cold read).

### 1.2 Brand voice / Atmosphere

This design believes its reader is busy, skeptical of being spun, and looking for a straight answer to "did I do well this week, and can I trust this number." Every restraint decision — no gradients on data cards, no decorative illustration, "Avg" spelled out explicitly rather than implied, warning banners instead of fabricated zeros when data is missing — exists to protect that trust. The one place the system allows itself real personality is the header/footer dark-navy band, which reads as "this is still a real company with a logo and a truck," bookending an otherwise almost admin-tool-plain body.

The categorical color system is not decoration — it is the report's actual information architecture. A driver scanning fast should be able to tell "this number is about Reefer" from color alone before reading the label, which is why reefer-blue and dryvan-green are never reused for anything else in the data body (they *are* reused, deliberately, for the hero-card money/rate colors' near-neighbors — see the Do/Don't on this below).

### 1.3 The "ONE brand thing"

- **The thing**: the dark-navy gradient header/footer band (`#0a1420` → `#123055`), bookending an otherwise near-white/gray report body.
- **Why it carries the brand**: it's the only place in the whole document with real visual weight (photo, gradient, glow) — remove it and the report would read as a generic spreadsheet export, not a KLG document.
- **How everything else supports it**: the body is deliberately flat and undecorated specifically so the header/footer pair reads as a real bookend, not one loud element among several.
- **Where it appears (and where it deliberately doesn't)**: only header and footer. Every section in between stays on white/`--layer-1` gray. No gradient, glow, or dark surface ever appears mid-report.

**Confidence**: ✅ high.

---

## 2. Design System (tokens)

### 2.1 Colors

| Token | Hex | Role | Where it appears | Confidence |
|---|---|---|---|---|
| `page` | `#f2f5f8` | Page background | `<body>` | ✅ high |
| `surface` | `#ffffff` | Card/section background | All `.section`, cards | ✅ high |
| `layer-1` | `#f7f9fb` | First nesting depth | `.section-body` | ✅ high |
| `layer-2` | `#eef1f5` | Second nesting depth | nested bar tracks | ✅ high |
| `text-primary` | `#0c1420` | Main text/numbers | Hero values, headings | ✅ high |
| `text-secondary` | `#5b6472` | Secondary copy | Sub-labels | ✅ high |
| `text-muted` | `#5c636f` | De-emphasized text | Deltas' "vs last week" | ✅ high |
| `good` | `#006300` | Positive delta | ▲ arrows — **also leaks decoratively, see 6. Don't** | ✅ high |
| `bad` | `#c93a3a` | Negative delta | ▼ arrows | ✅ high |
| `warning` / `warning-bg` | `#8a5a00` / `#fbf1de` | Missing-data state | "No approved Gross data" banner | ✅ high |
| `reefer` | `#2a78d6` | Reefer identity | dot, icon, chart, card tint | ✅ high |
| `dryvan` | `#1baf7a` | Dry Van identity | dot, icon, chart, card tint | ✅ high |
| `gross-accent` | `#2F6F4E` | "Gross" metric family (hero card only) | Best Weekly Gross hero | ✅ high |
| `rpm-accent` | `#3D5A99` | "RPM" metric family (hero card only) | Best RPM hero | ✅ high |
| `fuel-accent` | `#B77A2A` | Fuel metric family | Fuel hero + trend chart | ✅ high |
| `deadhead-accent` | `#7357A6` | Deadhead metric family | Deadhead hero | ✅ high |
| `dark-bg` → `dark-good`/`dark-accent` | `#0a1420` → `#3ec93e`/`#5aa2ef` | Header/footer-only palette | Header, footer | ✅ high |

No dark-mode theme exists — the dashboard is light-only.

### 2.2 Typography

- **Family**: `system-ui, -apple-system, "Segoe UI", sans-serif` — a deliberate choice, confirmed correct for UI/web (not a corner-cut) per Practical Typography's own guidance that the "avoid system fonts" rule is scoped to print documents.
- **Confidence**: ✅ high (literal value in source, not inferred)

**Observed scale** (8 steps, `--fs-*` tokens):

| Token | Size | Typical weight | Use |
|---|---|---|---|
| `display` | 34px | 800 | Header H1, big fuel-discount stat |
| `stat` | 22px | 800 | Hero values, footer slogan |
| `title` | 20px | 700 | Section sub-headers |
| `subtitle` | 16px | 600 | Card headers |
| `body` | 14px | 400-700 | Running copy, contact line |
| `label` | 12px | 700, +6-7% tracking | Uppercase eyebrow labels |
| `micro` | 11px | varies | Fine print, sub-captions |
| `caption` | 10px | varies | Smallest chart labels |

**Weight ceiling**: 800 is the hard cap for every numeric "value" element across the whole file (hero values, trend-stat values, bar/line chart labels) — nothing ever goes to 900. This is a deliberate, consistently-applied rule (see Do's).

### 2.3 Spacing

- **Inferred base unit**: 2px, with most real gaps landing on 4px multiples (4/6/8/12/14/16/18/20/22/24).
- **Consistency**: ✅ high — no arbitrary odd values found (e.g. no 13px, 17px paddings) after the 2026-07-24 type-scale cleanup pass.

### 2.4 Radii

- `sm` 8px — market-cards, small chips.
- `md` 14px — hero cards, trend cards, trailer-compare cards, footer bar (the dominant "card" radius).
- `lg` 16px — header (the single largest surface).
- `pill` 999px — hero-eyebrow badge, bar-chart date chips **only**.

### 2.5 Elevation system

| Level | Name | Treatment | Use |
|---|---|---|---|
| 0 | Flat | No shadow, hairline `1px solid var(--gridline)` or none | Trend cards, market cards, trailer cards |
| 1 | Resting card | `0 4px 14px rgba(20,32,48,0.035)` | Hero cards (4 "Best of the Week") |
| 2 | Hover | `0 7px 18px rgba(20,32,48,0.055)` + `translateY(-1px)` | Hero cards, trailer-compare cards on hover |

Only two tiers exist, and the second is hover-only, not a static resting state anywhere — a deliberately light-touch elevation system, appropriate for a data-dense report where heavy shadows would read as decoration.

#### Decorative depth (non-functional)

- **Atmospheric gradient scoping**: the only gradient/glow/photo treatment in the entire document is the header (`135deg` navy gradient + a radial glow + a photo with a fade overlay) and the footer (flat dark gradient, no photo). Nowhere else. This scoping is absolute and load-bearing for the brand voice (see 1.3).

### 2.6 Borders

- Base: `rgba(11,20,32,0.10)` (a neutral near-black at 10% alpha, not a flat gray hex) — a more "premium" choice than a flat `#e0e0e0`, since it tints subtly with whatever's behind it.
- Colored borders (hero cards, trailer-compare cards) use the **same alpha-scale pattern**: ~14-16% at rest, doubling to ~28-32% on hover. This is a real, consistently-applied parallel alpha scale — a mature-system signal.

### 2.7 Accessibility quick-check

Known, already-fixed contrast issues this session (not re-litigated here, just logged): `--text-muted` was raised from `#6e7681` (4.59:1) to `#5c636f` (6.05:1) specifically for Telegram JPEG-recompression resilience; the hero-eyebrow label was moved off `--dark-gold` (1.93:1 on light bg — a real failure) onto `--warning` (5.42:1). Both are ✅ high confidence, already verified with real contrast math earlier this session, not estimated here.

---

## 3. Components Inventory

### 3.1 Generic components

#### hero-card
- **Role**: the 4 "Best of the Week" cards. `{components.hero-card}` — tinted background per metric family, `{rounded.md}`, `{colors.gross-accent}`/`{colors.rpm-accent}`/`{colors.fuel-accent}`/`{colors.deadhead-accent}` border+icon.
- **Confidence**: ✅ high

#### trend-card
- **Role**: the "5-Week Trends" Reefer/Dry Van cards. `{rounded.md}`, plain `{colors.surface}` background, hairline border.
- **Confidence**: ✅ high

#### trailer-compare-card
- **Role**: the "By Trailer Type" cards. Background = trailer brand hex lightened ~92%, `{rounded.md}`.
- **Confidence**: ✅ high

#### market-card
- **Role**: the "National Market Snapshot" cards. `{rounded.sm}` (the one exception to the md-radius default), `1px solid {colors.gridline}`.
- **Confidence**: ✅ high

#### footer-bar
- **Role**: the closing brand/contact/QR band. `{colors.dark-bg}` gradient, `{rounded.md}`.
- **Confidence**: ✅ high

#### pill-badge
- **Role**: `{rounded.pill}` shape — the hero-eyebrow "Best of the Week" badge and bar-chart date chips only. Never used on a card or container (see Do's/Don'ts).
- **Confidence**: ✅ high

#### delta-indicator (`▲`/`▼` + %)
- **Variants**: colored by good/bad direction, reused identically across hero cards, trend mini-stats, market cards, deadhead card.
- **States**: up-good (green), up-bad (red, e.g. deadhead getting worse), down-good, down-bad.
- **Confidence**: ✅ high

#### icon-chip (colored circle + Lucide SVG)
- **Variants**: one per metric/trailer family, background = family hex at ~13% alpha (`hex + "22"` suffix), icon = full-strength hex.
- **Confidence**: ✅ high

#### tab (KPI mini-stat)
- **States**: active (colored 2px border + tinted background), inactive (gridline border, plain surface), hover (translateY(-2px) + shadow).
- **Confidence**: ✅ high

### 3.2 Signature components

#### gross-bar-chart-rpm-line-chart-toggle (`.trend-stat-mini` tabs)
- **What it is**: clicking "Avg RPM" / "Avg Gross" swaps the chart below between a line-draw and a staggered bar-grow, with a title crossfade.
- **Why it's signature**: not a generic tab component — the two chart types share an identical 560×170 canvas specifically so the card never changes height when switching, and both directions (RPM→Gross and Gross→RPM) now animate symmetrically.
- **Confidence**: ✅ high

#### no-approved-gross-data-warning-banner ("No approved Gross data this week")
- **What it is**: replaces a bar/number entirely with a `warning`-colored banner when a trailer type has no representative Gross data.
- **Why it's signature**: most dashboards would show a fabricated `$0` or hide the row silently; this system treats "we don't have a trustworthy number" as a first-class state, matching the report's whole "don't fabricate, flag instead" ethos.
- **Confidence**: ✅ high

---

## 4. Layout & Composition

### 4.1 Grid & containers

- Container max-width 1000px, 16px horizontal padding (`.wrap`).
- Hero row: `repeat(4, 1fr)` → 2-col at ≤820px → 1-col at ≤520px.
- Trend/market grids: `repeat(2, 1fr)` → 1-col at ≤720-820px depending on section.

### 4.2 Composition patterns

- Single-column vertical flow of full-width `.section` cards — no sidebar, no multi-track layout. Appropriate for a document meant to be screenshotted/scrolled on a phone.

### 4.3 Responsive behavior

#### Breakpoints

| Name | Width | Key changes |
|---|---|---|
| Mobile | ≤520px | Hero row → 1-col |
| Mobile-md | ≤600px | Methodology note wraps to multiple lines |
| Tablet | ≤720-820px | Trend/market/trailer grids → 1 or 2-col; header photo hides |
| Desktop | >820px | Full multi-column grids |

**Known headless-testing gotcha** (not a design flaw, a tooling one): headless Chrome's `--window-size` silently clamps below ~500px, so true sub-500px behavior (e.g. the market-grid's 480px single-column rule) has never been visually confirmed in this session — only reasoned about by code inspection. Flagged here as an Open Question.

#### Touch targets

- KPI tabs and trailer cards have generous padding (≥14px), comfortably above the 44px touch-target floor once rendered at real mobile width.

#### Collapsing strategy

- Grids step down one column count per breakpoint rather than jumping straight to 1-col — a gradual, not abrupt, collapse.

### 4.4 Image behavior

- Header photo: fixed 400px-wide right-aligned box, long one-directional fade-in from the navy background, no fade on the right edge (flush to the rounded corner). Hides entirely ≤720px rather than trying to responsively resize.
- Logo (header + footer): plain PNG, transparent background, no card/frame around it.
- QR code: fixed 70×70px white chip, `object-fit:cover`.

---

## 5. Reconstruction Notes

### Suggested stack

**Vanilla HTML/CSS/JS, no framework, no build step.**

Justification: this is a deliberate constraint (Claude Artifacts single-file requirement), not a taste choice — and it's the correct choice given this file's proven history of Claude Artifacts' mobile JS execution being unreliable. Introducing a framework or an external animation library (GSAP was considered and explicitly rejected for this reason) would add a dependency that could fail in the exact environment this file needs to be most reliable in.

### Quick wins

- The 8-step type scale and 3-step radius scale already cover ~95% of new-component styling needs without inventing new values.
- The alpha-border hover pattern (`hex + opacity%` doubling on hover) is copy-pasteable for any new interactive card.

### Tricky bits

- The categorical color system currently has exactly 6 hues in active use (reefer, dryvan, gross, rpm, fuel, deadhead) with zero collisions after this session's fixes — adding a 7th data category (e.g. a new trailer type) will require deliberately picking a hue that clears both the existing set AND stays distinct from the metric-family hero colors, not just "the next unused-looking color."
- The entrance-animation layer is defensively engineered around a real, proven failure mode (JS not executing in Artifacts' mobile sandbox) — any future animation addition must follow the same "CSS default + JS-guarded reveal in one block" pattern, not a naive `opacity:0` default.

### Implicit states to define

- Focus-visible states for keyboard navigation on the KPI tabs (currently only hover/active are styled explicitly; browser default focus ring likely applies but wasn't audited this session).

### Confidence map

| Layer | Confidence | Why |
|---|---|---|
| Identity | ✅ high | Built and reviewed live, not inferred |
| Colors | ✅ high | Literal hex from `:root`, cross-checked against a full session of color-collision fixes |
| Typography | ✅ high | Literal values, not visually guessed |
| Spacing | ✅ high | Verified consistent post-cleanup |
| Components | ✅ high | Full component set known from build history |
| Layout / responsive | ⚠️ medium | Sub-500px behavior reasoned, not visually confirmed (tooling limitation) |

---

## 6. Do's and Don'ts

### Do

- **Reserve `rounded.pill` (999px) for badges/tags/date-chips only** (`hero-eyebrow`, bar-chart date pills). Never apply it to a card or container — the system's card radius is always `rounded.md`/`rounded.sm`.
- **Cap numeric-value font-weight at 800.** Every hero value, trend-stat value, and chart label already stops here — don't introduce a 900-weight number anywhere.
- **Assign each new data category (trailer type, metric family) its own hue, checked against all 6 existing hues, not just eyeballed.** The system has already had two real color-collision bugs this session (Gross-hero vs Dry Van, RPM-hero vs Reefer) from skipping this check.
- **Use the established alpha-doubling hover pattern** (`rgba(...,0.14–0.16)` → `rgba(...,0.28–0.32)`) for any new interactive card border, rather than inventing a new hover treatment.
- **Keep the header/footer as the only two surfaces allowed a gradient or photo.** This scoping is the report's one deliberate "brand moment" — diluting it by adding a gradient elsewhere would flatten the effect.
- **When data is missing or unrepresentative, show an explicit warning state**, never a fabricated zero or a silently-hidden row.

### Don't

- **Don't reuse the `good` (`#006300`/`#3ec93e`) token for anything that isn't an actual positive-direction indicator.** It currently also colors the header date and footer wordmark purely decoratively — a real, if minor, semantic inconsistency (see Open Questions).
- **Don't add a JS-dependent "hidden by default" state without a same-block guaranteed reveal.** This file has a proven, documented history of injected JS not executing reliably on Claude Artifacts' mobile sandbox — every reveal/animation in this system was deliberately re-architected around that constraint.
- **Don't introduce an external animation library (GSAP, Framer Motion, etc.) into this specific file.** Explicitly evaluated and rejected this session — adds a load-dependency risk with no corresponding benefit given the existing defensive vanilla system already works.
- **Don't blend the "5-Week Trends" section's per-week historical data with the current week's `trucks`-derived numbers without keeping them manually in sync** — `TRAILER_LAST_WEEK_GROSS` and `trailerTrends.gross`'s "1 week ago" value are intentionally the same number stored in two places (the functions don't share scope); forgetting to update both on a future edit will silently desync the "By Trailer Type" delta from the "5-Week Trends" chart.
- **Don't treat Dry Van's current trend-array values as re-derivable from settlement PDFs** — they're the user's own deliberate approximate override (small driver sample), not a placeholder to "fix" back to raw PDF math.
- **Don't add a 7th categorical hue without running it through the same CVD/contrast check** used for the existing 6 (Flatbed's original purple was found too close to Reefer's blue under deuteranopia simulation earlier this session).

---

## 7. Open Questions

- **Does the `good` token's decorative reuse (header date, footer label) need fixing, or is it accepted as "just an accent green" in practice?** Flagged, not resolved — a judgment call for the user, not a clear bug.
- **Sub-500px responsive behavior** (the market-grid's 480px single-column breakpoint) has never been visually confirmed — headless Chrome's window-size clamp makes it untestable with the current tooling. Would need a real device or a CDP-based emulation script (Node not previously available in this environment; now installed, so `Emulation.setDeviceMetricsOverride` via a small script is newly possible).
- **Keyboard focus-visible states** on interactive elements (KPI tabs, hero cards) were not explicitly audited this session — relies on browser default, unverified whether that default is legible against every card background.

---

## 8. Companion files

- [ ] `design-tokens.json` — not generated in this pass (can be added on request; all values above are already in DTCG-compatible shape in the frontmatter)
- [x] `design-a11y.md` — not a separate file; contrast findings are logged inline in Section 2.7 and in this project's memory notes, already verified with real math earlier this session
- [ ] `design-screenshot.png` — not attached; multiple verification screenshots already exist in the scratchpad from this session's edits

---

*End of analysis. This file documents the system as it stands on 2026-07-26. If the color
system, type scale, or component set changes in a future session, regenerate rather than
hand-edit this file, so it stays a trustworthy source of truth rather than drifting from
the live dashboard.*
