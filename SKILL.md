---
name: radius-ui-kit
description: Apply Radius brand identity to web interfaces, dashboards, landing pages, and React components. Use when building anything for Radius, radiustech.xyz, or when the user mentions "Radius brand", "Radius style", "stablecoin network UI", or needs a high-performance fintech/crypto aesthetic. Also use for micropayments, agent payments, or blockchain infrastructure UIs. The Radius design is LIGHT MODE with warm off-white backgrounds, coral accent color, and bold uppercase typography.
license: MIT
---

# Radius UI Kit

Design system and component library based on radiustech.xyz — a high-performance stablecoin network for micropayments and machine-to-machine transactions.

## Brand Identity

**Core positioning**: Infrastructure for infinite economic bandwidth. Technical credibility meets forward-thinking elegance.

**Design philosophy**: 
- **LIGHT MODE** with warm, off-white backgrounds (#F8F9FB)
- Coral/salmon accent color (#EB6359) for primary CTAs
- Bold, uppercase typography for headings using expanded fonts
- Clean, rounded containers with subtle 5% opacity backgrounds
- Professional, trustworthy fintech aesthetic
- Generous whitespace and padding (48px page padding, 96px between sections)

## Design Tokens

### Colors

```css
:root {
  /* Core palette - LIGHT MODE */
  --radius-bg-page: #F8F9FB;           /* Warm off-white page background */
  --radius-bg-card: rgba(31, 31, 37, 0.05);  /* 5% dark overlay for cards/sections */
  --radius-bg-nav: rgba(255, 255, 255, 0.9); /* Semi-transparent white nav */
  --radius-bg-hero-overlay: rgba(255, 255, 255, 0.8); /* Hero text container overlay */
  --radius-white: #FFFFFF;
  
  /* Brand colors */
  --radius-executive-deep: #1F1F25;    /* Primary text - RTQ2 Executive Deep */
  --radius-text-primary: #1F1F25;
  --radius-text-secondary: #3E3E42;    /* Secondary nav text */
  --radius-coral: #EB6359;             /* Primary accent / CTA color */
  --radius-link: #EB6359;              /* Link color (same as coral) */
  
  /* Borders */
  --radius-border-nav: rgba(0, 0, 0, 0.06);
  --radius-border-dark: #1F1F25;       /* Strong dividers - 2px solid */
  
  /* Shadows - layered for nav depth */
  --radius-shadow-nav: 
    0px 79px 22px 0px rgba(0,0,0,0),
    0px 51px 20px 0px rgba(0,0,0,0.01),
    0px 28px 17px 0px rgba(0,0,0,0.05),
    0px 13px 13px 0px rgba(0,0,0,0.09),
    0px 3px 7px 0px rgba(0,0,0,0.1);
}
```

### Typography

**Font stack** (in order of preference):
1. **Headings (display/h1/h2)**: `"Mona Sans Expanded", "Mona Sans", sans-serif` — Bold weight (700), UPPERCASE
2. **Section labels**: `"Mona Sans", sans-serif` — ExtraBold weight (800), UPPERCASE, letter-spacing 0.9px
3. **Body & UI text**: `"Instrument Sans", sans-serif` — Regular (400), Medium (500), Bold (700)

> **Note on Mona Sans.** The kit uses **Mona Sans** (GitHub's Primer design system typeface), self-hosted from the `MonaSans-2.0.8/` folder in the repo. Two widths ship side by side:
>
> - **Mona Sans Expanded** (`MonaSansExpanded-*.woff2`) — for display/hero/section titles at 48–60px. The wider forms carry the "RADIUS" brand voice at large sizes.
> - **Mona Sans** (normal width) — for section labels at ExtraBold (800), and any heading that should read at body width.
>
> Both families load the same four weights (400/500/700/800). The font stack falls back from Expanded → Normal → generic sans-serif, so declaring `'Mona Sans Expanded'` first in display contexts is safe even if the Expanded face fails to load.

**Font loading** (self-hosted Mona Sans + Google Fonts Instrument Sans):

```html
<link href="https://fonts.googleapis.com/css2?family=Instrument+Sans:wght@400;500;700&display=swap" rel="stylesheet">
```

```css
/* Self-hosted Mona Sans — paths relative to the HTML file */
/* Normal width — labels, body-width headings */
@font-face {
  font-family: 'Mona Sans';
  src: url('MonaSans-2.0.8/webfonts/static/MonaSans-Regular.woff2') format('woff2');
  font-weight: 400; font-style: normal; font-display: swap;
}
@font-face {
  font-family: 'Mona Sans';
  src: url('MonaSans-2.0.8/webfonts/static/MonaSans-Medium.woff2') format('woff2');
  font-weight: 500; font-style: normal; font-display: swap;
}
@font-face {
  font-family: 'Mona Sans';
  src: url('MonaSans-2.0.8/webfonts/static/MonaSans-Bold.woff2') format('woff2');
  font-weight: 700; font-style: normal; font-display: swap;
}
@font-face {
  font-family: 'Mona Sans';
  src: url('MonaSans-2.0.8/webfonts/static/MonaSans-ExtraBold.woff2') format('woff2');
  font-weight: 800; font-style: normal; font-display: swap;
}

/* Expanded width — display/hero headings */
@font-face {
  font-family: 'Mona Sans Expanded';
  src: url('MonaSans-2.0.8/webfonts/static/MonaSansExpanded-Regular.woff2') format('woff2');
  font-weight: 400; font-style: normal; font-display: swap;
}
@font-face {
  font-family: 'Mona Sans Expanded';
  src: url('MonaSans-2.0.8/webfonts/static/MonaSansExpanded-Medium.woff2') format('woff2');
  font-weight: 500; font-style: normal; font-display: swap;
}
@font-face {
  font-family: 'Mona Sans Expanded';
  src: url('MonaSans-2.0.8/webfonts/static/MonaSansExpanded-Bold.woff2') format('woff2');
  font-weight: 700; font-style: normal; font-display: swap;
}
@font-face {
  font-family: 'Mona Sans Expanded';
  src: url('MonaSans-2.0.8/webfonts/static/MonaSansExpanded-ExtraBold.woff2') format('woff2');
  font-weight: 800; font-style: normal; font-display: swap;
}
```

**Scale**:
```css
:root {
  /* Display & Headings - UPPERCASE */
  --radius-text-display: 60px;    /* Hero/page titles - Mona Sans Expanded Bold */
  --radius-text-h2: 48px;         /* Section titles - Mona Sans Expanded Bold */
  --radius-text-h3: 36px;         /* Card titles - Instrument Sans Medium */
  --radius-text-h4: 27px;         /* Feature titles - Instrument Sans Medium */
  --radius-text-label: 18px;      /* Section labels - Mona Sans ExtraBold, tracking 0.9px */
  
  /* Body text - Instrument Sans */
  --radius-text-hero-body: 34px;  /* Hero description - Instrument Sans Regular */
  --radius-text-body-lg: 22px;    /* Large body text */
  --radius-text-body: 18px;       /* Standard body */
  --radius-text-nav: 16px;        /* Navigation links - Instrument Sans Bold */
  --radius-text-footer: 15px;     /* Footer text - Instrument Sans Medium */
  
  /* Line heights */
  --radius-leading-tight: 1.1;    /* Headings */
  --radius-leading-body: 1.3;     /* Body text */
  --radius-leading-label: 1.5;    /* Labels */
  
  /* Letter spacing */
  --radius-tracking-label: 0.9px; /* Section labels ONLY */
  
  /* Font feature settings */
  --radius-font-features: 'lnum', 'pnum';  /* Lining & proportional numerals */
}
```

### Spacing

```css
:root {
  /* Page-level spacing */
  --radius-page-padding: 48px;
  --radius-section-gap: 96px;      /* Gap between major sections */
  
  /* Component spacing */
  --radius-gap-xs: 10px;
  --radius-gap-sm: 12px;
  --radius-gap-md: 24px;
  --radius-gap-lg: 48px;
  --radius-gap-xl: 72px;           /* Section internal padding */
  
  /* Container internal padding */
  --radius-card-padding: 24px;
  --radius-section-padding-y: 72px;
  --radius-section-padding-x: 48px;
}
```

### Border Radius

```css
:root {
  --radius-rounded-sm: 10px;      /* Inner elements, images */
  --radius-rounded-md: 20px;      /* Cards, sections */
  --radius-rounded-nav: 200px;    /* Pill-shaped navigation */
  --radius-rounded-btn: 38px;     /* Secondary buttons */
  --radius-rounded-btn-primary: 61px;  /* Primary coral buttons */
}
```

## Component Patterns

> **Navigation is out of scope for this skill.** The base kit does not define a marketing nav — pages built with this kit should either omit the nav or use the brand-lockup pattern from the `radius-subdomain-page` skill (Section 2). The nav-related tokens (`--radius-bg-nav`, `--radius-border-nav`, `--radius-shadow-nav`) remain in the token set for consumers that reuse them.

### Buttons

**Primary Button (Coral)**:
```css
.radius-btn-primary {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 44px;
  padding: 16px 24px;
  background: #EB6359;
  border-radius: 61px;
  
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 700;
  font-size: 16px;
  line-height: 1.1;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}
```

**Secondary Button (Outlined)**:
```css
.radius-btn-secondary {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 44px;
  padding: 16px 24px;
  background: transparent;
  border: 1px solid #1F1F25;
  border-radius: 38px;
  
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 700;
  font-size: 16px;
  line-height: 1.1;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}
```

### Hero Container (with image background)

```css
.radius-hero-container {
  display: flex;
  flex-direction: column;
  align-items: flex-start;
  justify-content: center;
  min-height: 351px;
  padding: 72px 48px;
  border-radius: 20px;
  position: relative;
  overflow: hidden;
}

.radius-hero-container::before {
  content: '';
  position: absolute;
  inset: 0;
  background: rgba(255, 255, 255, 0.8);
  z-index: 1;
}

.radius-hero-content {
  position: relative;
  z-index: 2;
  max-width: 864px;
}

.radius-hero-text {
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 400;
  font-size: 34px;
  line-height: 1.1;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}
```


### Cards (Use Case Cards)

Image treatment is intentionally out of scope — the card defines container, title, and description styling only. Consumers provide their own image/media treatment.

```css
.radius-card {
  padding: 24px;
  background: rgba(31, 31, 37, 0.05);
  border-radius: 20px;
}

.radius-card-title {
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 500;
  font-size: 36px;
  line-height: 1.1;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}

.radius-card-description {
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 400;
  font-size: 22px;
  line-height: 1.3;
  color: #1F1F25;
  margin-top: 24px;
  font-feature-settings: 'lnum', 'pnum';
}
```

### Feature Grid Cards

```css
.radius-feature-card {
  display: flex;
  flex-direction: column;
  gap: 12px;
  padding: 24px;
  background: rgba(31, 31, 37, 0.05);
  border-radius: 20px;
}

.radius-feature-title {
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 500;
  font-size: 27px;
  line-height: 1.1;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}

.radius-feature-description {
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 400;
  font-size: 18px;
  line-height: 1.3;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}

/* Links within feature cards */
.radius-feature-link {
  color: #EB6359;
  text-decoration: underline;
}
```

### CTA Section

```css
.radius-cta {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 24px;
  padding: 120px 24px;
  background: rgba(31, 31, 37, 0.05);
  border-radius: 20px;
  text-align: center;
}

.radius-cta-title {
  font-family: 'Mona Sans Expanded', 'Mona Sans', sans-serif;
  font-weight: 700;
  font-size: 48px;
  line-height: 1.1;
  text-transform: uppercase;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}

.radius-cta-subtitle {
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 400;
  font-size: 20px;
  line-height: 1.3;
  color: #1F1F25;
}
```

### Footer

```css
.radius-footer {
  display: flex;
  flex-direction: column;
  gap: 39px;
  padding: 68px 48px;
  background: rgba(31, 31, 37, 0.05);
  border-radius: 20px;
}

.radius-footer-nav {
  display: flex;
  gap: 12px;
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 500;
  font-size: 15px;
  line-height: 1.1;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}

.radius-footer-divider {
  width: 100%;
  height: 1px;
  background: #1F1F25;
}

.radius-footer-copyright {
  font-family: 'Instrument Sans', sans-serif;
  font-weight: 500;
  font-size: 15px;
  line-height: 1.1;
  color: #1F1F25;
  font-feature-settings: 'lnum', 'pnum';
}
```

## Layout Patterns

### Page Structure

```html
<div class="radius-page">
  <!-- Hero Container with background -->
  <div class="radius-hero-container">
    <p class="radius-hero-text">...</p>
  </div>
  
  <!-- Use Cases -->
  <section class="radius-section">
    <div class="radius-cards">...</div>
  </section>
  
  <!-- Feature Grid -->
  <section class="radius-section">...</section>
  
  <!-- CTA -->
  <div class="radius-cta">...</div>
  
  <!-- Footer -->
  <footer class="radius-footer">...</footer>
</div>
```

```css
.radius-page {
  display: flex;
  flex-direction: column;
  gap: 96px;
  align-items: center;
  padding: 48px;
  background: #F8F9FB;
}
```

## Key Design Rules

1. **All section headings are UPPERCASE** using Mona Sans Expanded Bold (700)
2. **Section labels** use Mona Sans ExtraBold with 0.9px letter-spacing
3. **Body text** uses Instrument Sans with `font-feature-settings: 'lnum', 'pnum'`
4. **Primary CTA buttons** are coral (#EB6359) with rounded-full (61px) corners
5. **Secondary buttons** have 1px dark border (#1F1F25) with 38px rounded corners
6. **Cards and sections** use `rgba(31, 31, 37, 0.05)` background with 20px border-radius
7. **Page background** is #F8F9FB (warm off-white)
8. **All text** is dark (#1F1F25) - this is a LIGHT theme
9. **Links** use coral color (#EB6359) with underline

## Accessibility

- High contrast dark text on light backgrounds
- Clear visual hierarchy through font weights and sizes
- Readable body text at 18-22px
- Focus states for interactive elements
- ARIA labels for icon-only buttons

---

For detailed component implementations with full React/HTML code, see:
- `references/components.md` — Full component library
- `references/icons.md` — Icon set and usage
