---
name: radius-subdomain-page
description: Build subdomain/product landing pages for the Radius ecosystem (e.g. facilitator.radiustech.xyz, docs, status pages). Complements the base `radius-ui-kit` skill with patterns for compact subdomain branding, hero eyebrows, tonal-container icons, 2-column sticky documentation layouts, syntax-highlighted code blocks, and numbered protocol flows. Use when the user mentions "Radius subdomain", "Radius docs page", "Radius product page", "x402 facilitator", or needs a product-specific landing page that lives under a Radius parent brand.
license: MIT
---

# Radius Subdomain Page Kit

Composable page patterns for building subdomain/product landing pages within the Radius ecosystem. Layers on top of the base `radius-ui-kit` brand identity.

**Use cases:**
- `facilitator.radiustech.xyz` (x402 payment facilitator)
- `docs.radiustech.xyz` (developer documentation)
- Status pages, changelogs, reference implementations
- Product-specific landing pages that need to signal "part of Radius"

**Philosophy:**
- Establishes parent-child brand hierarchy (Radius → product) via the nav lockup
- Dense, docs-friendly content layouts (2-column sticky grids)
- Dev-focused details: endpoint pills, syntax-highlighted code, numbered protocol flows
- Inherits all base Radius tokens (colors, typography, spacing)

---

## 1. Design Tokens (delta from base kit)

Add these CSS variables **on top of** the base `radius-ui-kit` tokens:

```css
:root {
  /* Extended palette */
  --radius-bg-card-hover: rgba(31, 31, 37, 0.08);
  --radius-text-muted: #6B6B72;
  --radius-coral-soft: rgba(235, 99, 89, 0.12);
  --radius-border-subtle: rgba(31, 31, 37, 0.08);

  /* Monospace — for code blocks, endpoints, technical identifiers */
  --font-mono: ui-monospace, SFMono-Regular, Menlo, Consolas, monospace;

  /* Scale overrides — match Radius About page (radiustech.xyz/about) */
  --text-display: clamp(40px, 5vw, 60px);   /* matches --_2025---typography--h1 */
  --text-h2: clamp(36px, 4vw, 48px);         /* matches --_2025---typography--h2 */

  /* Spacing */
  --space-section: clamp(72px, 10vw, 128px);
}
```

**Typography refinements** for display headings (match Radius `.text-style-h1`):
- `font-family: 'Mona Sans Expanded', 'Mona Sans', sans-serif` — Expanded width for display/hero titles
- `line-height: 1.1` (not `1` or `0.95` — those are too tight)
- `letter-spacing: 0.01em` (not negative tracking)
- `font-weight: 700`
- `text-transform: uppercase`

> **Note on Mona Sans.** This subdomain skill inherits the base kit's font stack. Display headings use `'Mona Sans Expanded', 'Mona Sans', sans-serif`; section labels and eyebrows use `'Mona Sans', sans-serif` at ExtraBold (800). Both widths are **self-hosted** from `MonaSans-2.0.8/webfonts/static/` — see the `@font-face` blocks in `radius-ui-kit` (`MonaSans-*` + `MonaSansExpanded-*`, four weights each).

---

## 2. Subdomain Nav (centered pill lockup)

A compact floating pill that establishes **parent-brand → product** hierarchy. No nav links, no CTAs — this is a subdomain, not the main marketing site.

```html
<nav class="radius-nav">
  <a class="brand" href="https://radiustech.xyz">
    <svg class="brand-logo" viewBox="0 0 805.28 216.2">...</svg>
    <span class="brand-divider" aria-hidden="true"></span>
    <span class="brand-product">x402 Facilitator</span>
  </a>
</nav>
```

```css
.radius-nav {
  position: sticky;
  top: 16px;
  z-index: 50;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 12px 24px;
  margin: 0 auto;
  width: fit-content;        /* shrink to content */
  background: rgba(255, 255, 255, 0.85);
  border: 1px solid rgba(0, 0, 0, 0.06);
  border-radius: 200px;       /* full pill */
  box-shadow: var(--radius-shadow-nav);
  backdrop-filter: blur(12px);
}

.brand {
  display: flex;
  align-items: center;
  gap: 12px;
  font-weight: 500;
  font-size: 16px;
  color: #1F1F25;
}

.brand-logo {
  height: 22px;
  width: auto;
  color: #1F1F25;             /* inherits into SVG currentColor */
}

.brand-divider {
  width: 1px;
  height: 18px;
  background: rgba(31, 31, 37, 0.18);
}

.brand-product {
  color: #3E3E42;             /* secondary text — subordinate to Radius wordmark */
  font-weight: 500;
}
```

**Key rules:**
- The Radius wordmark goes first (parent brand), the product name second (subordinate)
- Use a thin vertical divider — NOT a slash character — between brand and product
- Brand links to the parent domain (`radiustech.xyz`), not `#` or the current page
- **Inline the Radius logo SVG** with `currentColor` fills — do not load from disk paths (especially if folders have spaces; they break in browser preview contexts)

---

## 3. Hero (left-aligned, no background)

Follow the Radius About-page hero pattern: **no background container**, content sits on the page bg, centered container with left-aligned text inside.

```html
<header class="hero">
  <div class="hero-inner">
    <p class="hero-label">Built for Radius</p>
    <h1>Parallel <span class="accent">x402</span> Payment Facilitator</h1>
    <p class="hero-subtitle">
      High-throughput stablecoin settlement for the Radius network.
      Wallet pooling, sub-second finality, and zero nonce conflicts.
    </p>
    <div class="hero-cta">
      <a class="radius-btn radius-btn-secondary" href="#how-it-works">How It Works</a>
      <a class="radius-btn radius-btn-primary" href="#getting-started">Get Started</a>
    </div>
    <div class="hero-endpoint">
      <span class="method">POST</span>
      <span>/settle</span>
    </div>
  </div>
</header>
```

```css
.hero {
  position: relative;
  padding: clamp(72px, 10vw, 128px) 0 clamp(56px, 8vw, 96px);
  background: transparent;      /* NO card, NO gradient */
}

.hero-inner {
  max-width: 860px;             /* reading-width constraint, left-anchored */
}

/* Hero label — NOT a pill, NOT coral. Flat uppercase dark text. */
.hero-label {
  font-family: 'Mona Sans', sans-serif;
  font-size: 18px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.9px;
  line-height: 1.5;
  color: #1F1F25;
  margin-bottom: 12px;
}

.hero h1 {
  font-family: 'Mona Sans Expanded', 'Mona Sans', sans-serif;
  font-size: var(--text-display);
  font-weight: 700;
  text-transform: uppercase;
  line-height: 1.1;
  letter-spacing: 0.01em;
  margin-bottom: 20px;
}

.hero h1 .accent {
  color: #EB6359;                /* single word in coral for emphasis */
}

.hero-subtitle {
  font-size: 22px;
  line-height: 1.35;
  max-width: 560px;
  color: #3E3E42;
  margin-bottom: 32px;
}

.hero-cta {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  margin-bottom: 36px;
}
```

**Rules:**
- **No eyebrow pill.** Flat dark text. The pill pattern is not part of the Radius brand.
- **No background card on hero.** It sits directly on the page bg — matches `/about` and the centered-column pattern from radiustech.xyz.
- **Button order:** outlined secondary on LEFT, coral primary on RIGHT (matches Radius marketing: "Talk to Us" + "Get Started")
- **One-word color accent** in the h1 (e.g. `x402` in coral) — don't colorize multiple words.

### Endpoint pill (subdomain-specific decoration)

A monospace indicator showing the primary endpoint — signals "this is a technical product":

```css
.hero-endpoint {
  display: inline-flex;
  align-items: center;
  gap: 12px;
  font-family: var(--font-mono);
  font-size: 14px;
  color: #3E3E42;
  background: #FFFFFF;
  border: 1px solid var(--radius-border-subtle);
  border-radius: 10px;
  padding: 10px 18px;
}

.hero-endpoint .method {
  color: #EB6359;
  font-weight: 700;
}
```

---

## 4. Eyebrow Row (section labels with divider)

Every content section opens with a left-aligned eyebrow followed by a hairline divider. No index numbers — just the label.

```html
<div class="eyebrow-row">
  <span class="eyebrow">Why Radius</span>
</div>
<div class="section-head">
  <h2 class="section-title">Purpose-built for Radius</h2>
  <p class="section-intro">Radius isn't a typical blockchain...</p>
</div>
```

```css
.eyebrow {
  font-family: 'Mona Sans', sans-serif;
  font-size: 14px;
  font-weight: 800;
  text-transform: uppercase;
  letter-spacing: 0.12em;
  color: #1F1F25;
}

.eyebrow-row {
  display: flex;
  align-items: baseline;
  padding-bottom: 16px;
  margin-bottom: 24px;
  border-bottom: 1px solid var(--radius-border-subtle);
}
```

### Section head (asymmetric title + intro)

Title left, intro right — collapses to stacked on mobile:

```css
.section-head {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 48px;
  align-items: end;
  margin-bottom: 56px;
}

@media (max-width: 860px) {
  .section-head {
    grid-template-columns: 1fr;
    gap: 20px;
  }
}
```

---

## 5. Tonal-Container Icon System (Iconoir)

All icons use [Iconoir](https://iconoir.com) via the web-font CDN. Icons sit in rounded **tonal containers** — coral-soft background + coral foreground, same hue at two tonal values.

### Setup

```html
<link href="https://cdn.jsdelivr.net/gh/iconoir-icons/iconoir@main/css/iconoir.css" rel="stylesheet">
```

### Tonal container pattern

```css
.feature-icon {
  width: 44px;
  height: 44px;
  border-radius: 12px;
  background: var(--radius-coral-soft);     /* tonal bg */
  display: flex;
  align-items: center;
  justify-content: center;
  color: #EB6359;                            /* full-saturation fg */
  margin-bottom: 8px;
  font-size: 22px;
}

.feature-icon i { display: inline-flex; line-height: 1; }
```

```html
<div class="feature-icon"><i class="iconoir-flash" aria-hidden="true"></i></div>
```

### Recommended icon names

| Concept | Iconoir class |
|---|---|
| Bidirectional / sync | `iconoir-refresh-double` |
| Money / stablecoin | `iconoir-dollar-circle` |
| Parallel / concurrency | `iconoir-git-fork` |
| Speed / latency | `iconoir-flash` |
| Scale / infinity | `iconoir-infinite` |
| Security / lock | `iconoir-lock` |
| GitHub / Discord / X | `iconoir-github` / `iconoir-discord` / `iconoir-x` |

**Rule:** Never use unicode glyphs (`↔`, `∞`, `🔒`) or emoji in UI. Use Iconoir for consistency.

---

## 6. Feature Grid

6-up feature grid with hover state. Cards use the Radius 5% dark overlay pattern.

```css
.feature-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
  gap: 16px;
}

.feature-card {
  background: rgba(31, 31, 37, 0.05);
  border-radius: 20px;
  padding: 28px;
  transition: background 0.2s ease, transform 0.2s ease;
  display: flex;
  flex-direction: column;
  gap: 14px;
  min-height: 220px;
}

.feature-card:hover {
  background: rgba(31, 31, 37, 0.08);
  transform: translateY(-2px);
}

.feature-card h3 {
  font-family: 'Instrument Sans', sans-serif;
  font-size: 24px;
  font-weight: 500;
  line-height: 1.1;
}

.feature-card p {
  font-size: 18px;
  line-height: 1.4;
  color: #3E3E42;
}
```

---

## 7. 2-Column Sticky Layout (protocol + quickstart)

Documentation-style layout: title sticky on the left, content on the right. **Critical: use `min-width: 0` on grid children** or long URLs/hex strings will break the layout.

```css
.protocol, .quickstart {
  display: grid;
  grid-template-columns: 1fr 1.3fr;       /* or 1fr 1.4fr for quickstart */
  gap: 64px;
  align-items: start;
}

.protocol > *, .quickstart > * {
  min-width: 0;                            /* CRITICAL: override grid default auto */
}

.protocol-sticky {
  position: sticky;
  top: 120px;
}

/* Collapse to single column EARLY — the left column runs out of room for
   display-size titles (48px) well before typical tablet breakpoints */
@media (max-width: 1200px) {
  .protocol, .quickstart {
    grid-template-columns: 1fr;
    gap: 32px;
  }
  .protocol-sticky {
    position: static;                      /* release sticky in collapsed mode */
  }
}
```

**Why 1200px (not 960px):** At intermediate widths, the 1fr title column is too narrow to contain uppercase display headings like "HOW X402 PAYMENTS WORK" at 48px. The text overflows into the adjacent column. Always collapse early.

---

## 8. Numbered Step Patterns

Two variants — use large coral numerals for protocol/narrative flows, tonal circle badges for quickstart/imperative steps.

### Variant A — Large coral numerals (protocol flow)

```html
<li class="protocol-step">
  <span class="protocol-step-num">01</span>
  <div class="protocol-step-body">
    <h4>Client requests a paid resource</h4>
    <p>The resource server responds with <code>402 Payment Required</code>...</p>
  </div>
</li>
```

```css
.protocol-step {
  display: grid;
  grid-template-columns: 88px 1fr;
  gap: 24px;
  padding: 28px 0;
  border-top: 1px solid var(--radius-border-subtle);
}

.protocol-step-num {
  font-family: 'Mona Sans Expanded', 'Mona Sans', sans-serif;
  font-size: 56px;
  font-weight: 700;
  line-height: 1;
  color: #EB6359;
  letter-spacing: -0.04em;
}
```

### Variant B — Tonal circle badge (quickstart)

```html
<div class="quickstart-step">
  <div class="quickstart-badge">1</div>
  <div>
    <h4>Check supported tokens</h4>
    <pre><code>...</code></pre>
  </div>
</div>
```

```css
.quickstart-badge {
  width: 32px;
  height: 32px;
  border-radius: 50%;
  background: var(--radius-coral-soft);     /* tonal bg */
  color: #EB6359;                            /* tonal fg */
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 700;
  font-size: 14px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
  margin-top: 4px;
}
```

**Rule:** For numbered badges ≤ 20px, use body font (Instrument Sans Bold). Display font is overkill at small sizes.

---

## 9. Code Blocks (dark, with syntax highlighting)

```css
pre {
  background: #1F1F25;                       /* Executive Deep */
  color: #f6f7fb;
  border-radius: 12px;
  padding: 18px 20px;
  font-family: var(--font-mono);
  font-size: 13.5px;
  line-height: 1.55;
  overflow-x: auto;                          /* horizontal scroll, NOT wrap */
  white-space: pre;
  max-width: 100%;
  min-width: 0;
}

/* Inline syntax highlighting tokens */
pre .tok-key { color: #ff9b90; }              /* keywords: const, await */
pre .tok-str { color: #a7e1c3; }              /* strings, numbers */
pre .tok-com { color: #888; }                 /* comments */
```

**Rule:** use `white-space: pre` (NOT `pre-wrap`). Long URLs/hex addresses must horizontally scroll, not wrap — wrapping breaks the readability of code.

### API endpoint cards (method pills)

```css
.endpoint {
  background: rgba(31, 31, 37, 0.05);
  border-radius: 20px;
  padding: 24px;
}

.endpoint-method {
  font-family: var(--font-mono);
  font-size: 11px;
  font-weight: 700;
  letter-spacing: 0.08em;
  padding: 4px 8px;
  border-radius: 6px;
  background: var(--radius-coral-soft);
  color: #EB6359;
  text-transform: uppercase;
}

.endpoint-path {
  font-family: var(--font-mono);
  font-size: 15px;
  font-weight: 700;
  color: #1F1F25;
}
```

---

## 10. CTA Block

Simple, flat gray card. Centered. No gradients, no glow. Matches the "Build on Radius" pattern from the marketing site.

```css
.cta {
  border-radius: 20px;
  padding: clamp(72px, 10vw, 120px) clamp(32px, 6vw, 64px);
  background: rgba(31, 31, 37, 0.05);
  text-align: center;
}

.cta-title {
  font-family: 'Mona Sans Expanded', 'Mona Sans', sans-serif;
  font-size: var(--text-h2);
  font-weight: 700;
  text-transform: uppercase;
  line-height: 1.1;
  letter-spacing: 0.01em;
  margin-bottom: 16px;
}

.cta-subtitle {
  font-size: 18px;
  max-width: 540px;
  margin: 0 auto 32px;
  color: #3E3E42;
}

.cta-buttons {
  display: flex;
  gap: 12px;
  justify-content: center;
  flex-wrap: wrap;
}
```

---

## 11. Minimal Footer

Single row: brand lockup left, nav links right, dividers top and bottom, social icons below. No multi-column sitemap — subdomain pages are focused.

```html
<footer class="footer">
  <div class="footer-top">
    <a class="brand" href="https://radiustech.xyz">...brand lockup...</a>
    <nav class="footer-nav">
      <a href="#why-radius">Why Radius</a>
      <a href="#how-it-works">How It Works</a>
      <a href="#api">API</a>
      <a href="#getting-started">Quick Start</a>
      <a href="https://radiustech.xyz">Radius</a>
    </nav>
  </div>
  <div class="footer-bottom">
    <span>x402 Facilitator — Open-source payment infrastructure for the Radius network.</span>
    <div class="footer-social">
      <a href="#" aria-label="GitHub"><i class="iconoir-github"></i></a>
      <a href="#" aria-label="X"><i class="iconoir-x"></i></a>
      <a href="#" aria-label="Discord"><i class="iconoir-discord"></i></a>
    </div>
  </div>
</footer>
```

```css
.footer { padding: 32px 0 16px; }

.footer-top {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 0;
  border-top: 1px solid var(--radius-border-subtle);
  border-bottom: 1px solid var(--radius-border-subtle);
  flex-wrap: wrap;
  gap: 24px;
}

.footer-nav {
  display: flex;
  gap: 28px;
  flex-wrap: wrap;
}

.footer-nav a {
  font-size: 14px;
  font-weight: 500;
  color: #3E3E42;
}

.footer-nav a:hover { color: #EB6359; }

.footer-bottom {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding-top: 20px;
  font-size: 14px;
  color: #6B6B72;
  flex-wrap: wrap;
  gap: 16px;
}

.footer-social a {
  color: #6B6B72;
  font-size: 18px;
  display: inline-flex;
}

.footer-social a:hover { color: #1F1F25; }
```

---

## 12. Page Structure

```html
<div class="page">
  <nav class="radius-nav">...</nav>         <!-- Compact centered pill -->
  <header class="hero">...</header>         <!-- No bg, left-aligned -->

  <section id="why-radius">                 <!-- Eyebrow row + section head + feature grid -->
    <div class="eyebrow-row">...</div>
    <div class="section-head">...</div>
    <div class="feature-grid">...</div>
  </section>

  <section id="how-it-works">               <!-- 2-col sticky + numbered protocol flow -->
    <div class="eyebrow-row">...</div>
    <div class="protocol">
      <div class="protocol-sticky">...</div>
      <ol class="protocol-list">...</ol>
    </div>
  </section>

  <section id="api">                        <!-- Eyebrow + section head + endpoint cards -->
    <div class="eyebrow-row">...</div>
    <div class="section-head">...</div>
    <div class="endpoint-grid">...</div>
  </section>

  <section id="getting-started">            <!-- 2-col sticky + numbered code-block steps -->
    <div class="eyebrow-row">...</div>
    <div class="quickstart">
      <div class="protocol-sticky">...</div>
      <div class="quickstart-steps">...</div>
    </div>
  </section>

  <section>                                 <!-- CTA block -->
    <div class="cta">...</div>
  </section>

  <footer class="footer">...</footer>       <!-- Minimal single-row -->
</div>

<style>
  .page {
    max-width: 1280px;
    margin: 0 auto;
    padding: 20px 32px 48px;                /* hero and sections inherit this padding */
  }
</style>
```

---

## 13. Critical Rules (Lessons Learned)

1. **Inline the Radius logo SVG** with `currentColor` — don't reference file paths, especially if folders have spaces
2. **No pill badges** on eyebrow labels — flat uppercase dark text only
3. **Use `min-width: 0`** on all CSS Grid children that contain monospace content — otherwise long identifiers force overflow
4. **Collapse 2-column layouts at 1200px** — not 960px. Display-size titles need more room than tablet layouts allow
5. **`white-space: pre`** on code blocks (not `pre-wrap`) — URLs/addresses must scroll, not wrap
6. **Align hero with sections** — no extra horizontal padding, no `margin: 0 auto` on hero-inner. Sections and hero share the same left edge (the `.page` wrapper's padding is the source of truth)
7. **Line-height: 1.1 + letter-spacing: 0.01em** on display headings — matches Radius `.text-style-h1`. Negative tracking and sub-1 line-height are too tight
8. **Tonal containers** (same-hue 12% bg + full-saturation fg) for all icon chips and number badges — never use white-on-card or dark-on-coral inversions
9. **Button order:** outlined secondary LEFT, coral primary RIGHT. Always. Nav, hero, CTA — all consistent
10. **Subdomain nav is brand-only** — no nav links, no CTAs. Parent brand + divider + product name, linked to parent domain

---

## 14. When to use this skill vs base kit

**Use `radius-ui-kit` (base) for:**
- The main Radius marketing site
- Pages where Radius IS the product (homepage, about, network)
- Full-navigation sites with multiple top-level destinations

**Use `radius-subdomain-page` (this skill) for:**
- Sub-products with their own domain (`facilitator.`, `docs.`, `status.`)
- Technical/developer-facing product pages
- Pages that need documentation-style layouts (code blocks, protocol flows, API references)
- Any landing page where Radius is the PARENT and the product is subordinate

Both skills share the same color palette, typography, and button styles. This skill adds subdomain-specific patterns on top.
