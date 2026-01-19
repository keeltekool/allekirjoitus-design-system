# Allekirjoitus.fi Web Design Skill

When building or updating the allekirjoitus.fi website, apply these design guidelines to ensure 1:1 consistency with the existing site.

---

## Design System Location

**Assets are located at:** `G:\My Drive\SK_RE\Allekirjoitus_DesignSystem\`

```
assets/
├── logos/
│   ├── logo-full-color.svg    # Full logo for light backgrounds
│   ├── logo-full-white.svg    # Full logo for dark/colored backgrounds
│   ├── logo-mark-orange.svg   # "A." mark in brand orange
│   ├── logo-mark-white.svg    # "A." mark in white
│   └── logo-mark-black.svg    # "A." mark in black
├── patterns/
└── icons/
```

---

## Color Palette

### Primary Colors (from live website SVG)

```css
:root {
  /* Brand Orange - Primary accent */
  --allekirjoitus-orange: #ef4224;
  --allekirjoitus-orange-alt: #e23013;  /* Used in buttons/CTAs */
  --allekirjoitus-orange-hover: #bd2605;

  /* Text Colors */
  --allekirjoitus-black: #231f20;       /* Primary text (from logo) */
  --allekirjoitus-text: #010101;        /* Body text */
  --text-black: #000000;                /* Headings */

  /* Neutral Colors */
  --allekirjoitus-white: #ffffff;
  --allekirjoitus-gray: #bebdbd;        /* ".fi" text, secondary elements */
  --allekirjoitus-gray-light: #f2f2f2;  /* Section backgrounds */
  --gray-border: #e5e5e5;               /* Borders, dividers */
  --gray-400: #9ca3af;                  /* Language switcher separator */
  --gray-500: #6b7280;                  /* Pricing note text */
  --gray-600: #4b5563;                  /* Pricing price unit text */

  /* Layout */
  --container-max: 1200px;
  --container-narrow: 750px;
}
```

---

## Typography

### Font Families

```css
/* Primary - Body text */
font-family: "Metropolis", "Helvetica Neue", Helvetica, Arial, sans-serif;

/* Headings */
font-family: "Barlow Condensed", Helvetica, Arial, sans-serif;
```

### Font Loading

```html
<!-- Barlow Condensed from Google Fonts -->
<link href="https://fonts.googleapis.com/css2?family=Barlow+Condensed:wght@400;500;600;700&display=swap" rel="stylesheet">
```

**IMPORTANT: Metropolis Font (REQUIRED)**

Metropolis is NOT on Google Fonts. You MUST load it locally via @font-face:

```css
/* Metropolis font files - stored in assets/fonts/ */
@font-face {
  font-family: 'Metropolis';
  font-style: normal;
  font-weight: 300;
  src: url('assets/fonts/Metropolis-Light.otf') format('opentype');
}
@font-face {
  font-family: 'Metropolis';
  font-style: normal;
  font-weight: 400;
  src: url('assets/fonts/Metropolis-Regular.otf') format('opentype');
}
@font-face {
  font-family: 'Metropolis';
  font-style: normal;
  font-weight: 500;
  src: url('assets/fonts/Metropolis-Medium.otf') format('opentype');
}
@font-face {
  font-family: 'Metropolis';
  font-style: normal;
  font-weight: 600;
  src: url('assets/fonts/Metropolis-SemiBold.otf') format('opentype');
}
@font-face {
  font-family: 'Metropolis';
  font-style: normal;
  font-weight: 700;
  src: url('assets/fonts/Metropolis-Bold.otf') format('opentype');
}
```

Font files location: `website/assets/fonts/`
- Metropolis-Regular.otf
- Metropolis-Medium.otf
- Metropolis-SemiBold.otf
- Metropolis-Bold.otf
- Metropolis-Light.otf

**WARNING:** Without Metropolis font files, body text will fall back to Helvetica/Arial and appear thinner than the original site!

### Type Scale (VERIFIED from live site via Playwright)

| Element | Size (exact) | Weight | Line Height | Font | Alignment |
|---------|--------------|--------|-------------|------|-----------|
| Body | 17px | 400 | 1.65 | Metropolis | - |
| **H1 (Hero)** | **78.2px** | **500** | 1.1 | Barlow Condensed | **centered** |
| H2 Section titles (Edut, Paketit, UKK) | 51px | 500 | 1.2 | Barlow Condensed | centered |
| H2 About section | 36px | 400 | 1.2 | Barlow Condensed | left |
| H3 Benefits (Nopea ja joustava) | 30px | 400 | 1.3 | Barlow Condensed | centered |
| H3 Pricing titles | 20px | 600 | 1.3 | Barlow Condensed | centered |
| Pricing price | 47.6px (~48px) | 400 | - | Barlow Condensed | centered |
| Navigation | 16px | 500 | 1.4 | Metropolis | - |
| FAQ Headers | 17px | 400 | - | Metropolis | left |
| CTA Buttons | 16px | **600** | - | - | center |

**IMPORTANT:**
- The hero H1 is significantly larger (78px) than section H2s (51px)
- Section titles (Edut, Paketit, UKK) use 51px, NOT 36px
- About section H2s use 36px

---

## Layout

### Container Widths

```css
.container { max-width: 1200px; }
.container-narrow { max-width: 750px; }
```

### Spacing

```css
/* Section padding */
--section-padding-desktop: 4rem;
--section-padding-tablet: 3rem;
--section-padding-mobile: 2rem;

/* Card padding */
--card-padding: 2rem;
```

### Responsive Breakpoints

```css
/* Tablet */
@media (max-width: 922px) { }

/* Mobile */
@media (max-width: 544px) { }
```

---

## Components

### Buttons

There are TWO distinct button styles on the site:

#### 1. Header Login Button (Outline, Pill-shaped)
```css
.login-btn {
  background-color: transparent;
  color: #e23013;
  border: 2px solid #e23013;
  border-radius: 40px;  /* Pill shaped */
  padding: 10px 20px;
  font-size: 14px;
  font-weight: 600;
}

.login-btn:hover {
  background-color: #e23013;
  color: #ffffff;
}
```

#### 2. CTA Buttons (Outline, Pill-shaped)
```css
.btn-outline {
  border: 2px solid #e23013;
  border-radius: 30px;  /* Pill shape */
  padding: 15px 32px 14px;
  color: #e23013;
  background: transparent;
  font-size: 16px;
  font-weight: 600;
  transition: all 0.2s ease;
}

.btn-outline:hover {
  background-color: #e23013;
  color: #ffffff;
}

/* Smaller CTA button for pricing cards */
.btn-outline-sm {
  border: 2px solid #e23013;
  border-radius: 30px;
  padding: 15px 20px 14px;
  color: #e23013;
  background: transparent;
  font-size: 16px;
  font-weight: 600;
}

/* Filled small button (alternate style) */
.btn-filled-sm {
  border: 1.6px solid #e23013;
  border-radius: 30px;
  padding: 15px 20px 14px;
  color: #ffffff;
  background-color: #e23013;
  font-size: 16px;
  font-weight: 500;
}

/* Submit button (forms) */
.btn-submit {
  background-color: #ef4224;
  color: #ffffff;
  border: none;
  border-radius: 4px;
  padding: 12px 24px;
  font-weight: 500;
  cursor: pointer;
}
```

**NOTE:** Button variants:
- **Outline buttons** (.btn-outline, .btn-outline-sm, .btn-outline-contact): 2px border, weight 600
- **Filled buttons** (.btn-filled-sm): 1.6px border, weight 500
- **Submit button** (.btn-submit): No border, 4px radius, weight 500

### Pricing Cards

```css
.pricing-card {
  background: #ffffff;
  border: 1.6px solid #bebebe;  /* Gray border, 1.6px width */
  border-radius: 20px;          /* Rounded corners, NOT 6px */
  padding: 2rem;
  text-align: left;             /* LEFT aligned, NOT center! */
  display: flex;
  flex-direction: column;
  height: 100%;
}

.pricing-card-content {
  flex-grow: 1;
}

.pricing-card-footer {
  margin-top: auto;  /* Pushes button to bottom */
  padding-top: 1rem;
}

.pricing-card-footer .btn-outline-sm {
  display: block;
  width: 100%;  /* Full-width buttons in pricing cards */
}

.pricing-price {
  font-family: 'Barlow Condensed', Helvetica, Arial, sans-serif;
  font-size: 48px;
  font-weight: 400;
  color: #000;
}

.pricing-price span {
  font-size: 17px;
  color: #4b5563;  /* gray-600 */
}

.pricing-subtitle {
  font-size: 14px;
  color: #ef4224;  /* Orange text for emphasis */
  font-weight: 600;
}
```

**IMPORTANT:**
- Pricing cards have 20px border-radius (rounded), NOT 6px!
- Pricing card content is LEFT-ALIGNED, NOT centered!

### Form Inputs

```css
input, textarea, select {
  width: 100%;
  padding: 12px 16px;
  border: 1px solid #d1d1d1;
  border-radius: 4px;
  font-size: 16px;
  font-family: inherit;
  background-color: #ffffff;
}

input:focus, textarea:focus {
  border-color: #ef4224;
  outline: none;
}
```

### FAQ Accordion

```css
.accordion-item {
  border-bottom: 1px solid #e5e5e5;
}

.accordion-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 28px 10px;
  cursor: pointer;
  font-family: 'Metropolis', Helvetica, Arial, sans-serif;
  font-size: 17px;
  font-weight: 400;
}

.accordion-header:hover {
  color: #ef4224;
}

.accordion-icon {
  font-size: 24px;
  font-weight: 300;
  color: #010101;
}
```

**IMPORTANT:** FAQ uses PLUS sign (+), NOT chevron arrows!

### Icon Sizes (VERIFIED)

```css
/* Benefits section icons (Edut) */
.benefit-icon svg {
  width: 60px;
  height: 60px;
}

/* Feature icons below pricing (eIDAS, etc.) */
.feature-icon svg {
  width: 96px;
  height: 96px;
}

/* Feature text is bold */
.feature-text {
  font-size: 14px;
  font-weight: 600;
}
```

### Contact Section (VERIFIED)

```css
.section-dark {
  background-color: #170703;  /* Dark brown/black */
}

.section-dark h2 {
  color: #ffffff;
  font-size: 51px;
  font-weight: 500;
}

.section-dark p {
  color: #ffffff;
}

/* Contact form WRAPPER - light gray background! */
.contact-form-wrapper {
  background-color: #f2f2f2;  /* Light gray, NOT dark! */
  padding: 2rem;
  border-radius: 8px;
}

/* Form labels - dark text on light background */
.form-group label {
  display: block;
  font-size: 14px;
  font-weight: 500;
  color: #010101;  /* Dark text, NOT white! */
  margin-bottom: 0.25rem;
}

/* Contact form button - OUTLINE style, not filled! */
.btn-outline-contact {
  border: 2px solid #e23013;
  border-radius: 30px;
  padding: 15px 20px 14px;
  color: #e23013;
  background: transparent;
  font-size: 16px;
  font-weight: 600;
  width: 100%;
}
```

**IMPORTANT:**
- Contact SECTION has dark background (#170703)
- Contact FORM WRAPPER has light gray background (#f2f2f2)
- Form labels are dark text, NOT white
- Button is outline style, NOT filled orange

### Enterprise List (Arrow Markers)

```css
.enterprise-list {
  list-style-type: none;
  padding-left: 0;
  text-align: left;
  margin-top: 1rem;
}

.enterprise-list li {
  font-size: 14px;
  color: #000;
  margin-bottom: 0.5rem;
  padding-left: 1rem;
  position: relative;
}

.enterprise-list li::before {
  content: "›";
  position: absolute;
  left: 0;
  color: #ef4224;  /* Orange arrow */
  font-weight: 400;
}
```

**NOTE:** Enterprise list uses orange `›` arrow markers, NOT disc bullets!

### Links

```css
/* Body links */
a {
  color: #ef4224;
  text-decoration: underline;
}

a:hover {
  color: #bd2605;
}

/* Navigation links */
nav a {
  color: #000000;
  text-decoration: none;
  font-weight: 500;
}

nav a:hover {
  color: #ef4224;
}
```

---

## Header/Navigation

### Header Structure
The header contains (left to right):
1. Logo (left)
2. Navigation links (center)
3. Login button + Language switcher (right)

### Header CSS
```css
header {
  background: #ffffff;  /* WHITE, not gray! */
}

.header-inner {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.5rem 0;
}

.logo svg {
  height: 39px;
  width: 310px;
}

nav a {
  color: #000000;
  font-weight: 500;
}

nav a:hover {
  color: #ef4224;
}
```

**IMPORTANT:** The header background is WHITE (#ffffff), NOT gray!

### Language Switcher
The language switcher is INLINE HORIZONTAL, not stacked vertically:

```html
<!-- Language Switcher - INLINE with separator -->
<div class="lang-switcher">
  <a href="/fi">FI</a>
  <span>|</span>
  <a href="/en">EN</a>
</div>
```

```css
.lang-switcher {
  display: flex;
  align-items: center;
  font-size: 14px;
}

.lang-switcher span {
  margin: 0 0.5rem;
  color: #9ca3af;
}
```

---

## Footer

```css
footer {
  background: #ffffff;
  border-top: 1px solid #e5e5e5;
  padding: 2rem 0;
  text-align: center;
}

footer p {
  color: #000000;
  font-size: 14px;
}
```

---

## Logo Usage Rules (from Brand Guidelines PDF)

### Spacing
- Minimum clear space: 2x the "A" height on all sides
- Minimum width: 420px digital / 16mm print

### Color Combinations
| Background | Logo Version |
|------------|--------------|
| White/Light | Full color (orange "A.", black text, gray ".fi") |
| Black | White logo |
| Orange | White logo |
| Gray | Black "A." mark |

### Don'ts
- Don't rotate or skew the logo
- Don't change the colors
- Don't add effects (shadows, gradients)
- Don't stretch or distort proportions
- Don't use low-resolution versions

---

## Section Background Pattern (VERIFIED)

**RULE: Main content sections ALTERNATE between WHITE and GRAY backgrounds.**

The site uses specific background colors for each section:

| Section | Background Color | Notes |
|---------|-----------------|-------|
| Header | WHITE (#ffffff) | Fixed, not part of alternation |
| Hero | GRAY (#f2f2f2) | Starting point |
| About (support notice + images) | WHITE (#ffffff) | Alternates from Hero |
| Benefits (Edut) | GRAY (#f2f2f2) | Alternates from About |
| Pricing (Paketit) | WHITE (#ffffff) | Alternates from Benefits |
| Features (eIDAS icons) | GRAY (#f2f2f2) | Alternates from Pricing |
| FAQ | WHITE (#ffffff) | Alternates from Features |
| Contact | DARK (#170703) | Special dark section |
| Footer | WHITE (#ffffff) | Fixed |

**ALTERNATION RULE:**
```
Hero (GRAY) → About (WHITE) → Edut (GRAY) → Pricing (WHITE) → Features (GRAY) → FAQ (WHITE) → Contact (DARK)
```

**IMPORTANT:**
- Header is WHITE, NOT gray!
- Main sections ALTERNATE: gray → white → gray → white...
- Contact section is DARK (#170703) - exception to the alternation
- Support notice is part of the About section (WHITE)

---

## Hero Section

```css
.hero-section {
  background-color: #f2f2f2;
  background-image: url("https://allekirjoitus.fi/wp-content/uploads/2025/10/bg-9.png");
  background-size: cover;
  background-position: center;
  background-repeat: no-repeat;
  padding: 10rem 0;  /* Desktop */
  text-align: center;
}

.hero-section h1 {
  font-size: 78px;
  font-weight: 500;
  line-height: 1.1;
  margin-bottom: 2rem;
}
```

---

## Design Principles

1. **Clean & Minimal** - Generous whitespace, no clutter
2. **Professional Trust** - Corporate feel appropriate for e-signature service
3. **Orange as Accent** - Use #ef4224 / #e23013 sparingly for CTAs and emphasis
4. **High Contrast** - Black text on white for readability
5. **Consistent Rounding** - Pill buttons (30-40px radius), pricing cards (20px radius)

---

## Quick Reference - Pure CSS Classes

```css
/* Orange text */
color: #ef4224;

/* Orange background */
background-color: #ef4224;

/* Light gray section */
background-color: #f2f2f2;

/* Hero H1 (78px) */
h1 {
  font-family: 'Barlow Condensed', Helvetica, Arial, sans-serif;
  font-size: 78px;
  font-weight: 500;
  line-height: 1.1;
}

/* Section H2 (51px) */
h2.section-title {
  font-family: 'Barlow Condensed', Helvetica, Arial, sans-serif;
  font-size: 51px;
  font-weight: 500;
  line-height: 1.2;
}

/* About H2 (36px) */
h2.about-title {
  font-family: 'Barlow Condensed', Helvetica, Arial, sans-serif;
  font-size: 36px;
  font-weight: 400;
  line-height: 1.2;
}

/* Benefits H3 (30px) */
h3.benefit-title {
  font-family: 'Barlow Condensed', Helvetica, Arial, sans-serif;
  font-size: 30px;
  font-weight: 400;
  line-height: 1.3;
}

/* Pricing H3 (20px) */
h3.pricing-title {
  font-family: 'Barlow Condensed', Helvetica, Arial, sans-serif;
  font-size: 20px;
  font-weight: 600;
  line-height: 1.3;
}

/* Login button (header - outline pill) */
.login-btn {
  background-color: transparent;
  color: #e23013;
  border: 2px solid #e23013;
  border-radius: 40px;
  padding: 10px 20px;
  font-size: 14px;
  font-weight: 600;
}

/* CTA button (outline pill) */
.btn-outline {
  border: 2px solid #e23013;
  border-radius: 30px;
  padding: 15px 32px 14px;
  color: #e23013;
  background: transparent;
  font-size: 16px;
  font-weight: 600;
}

/* Card */
.pricing-card {
  background: #ffffff;
  border: 1.6px solid #bebebe;
  border-radius: 20px;  /* Rounded corners! */
  padding: 2rem;
}

/* Body text */
body {
  font-family: 'Metropolis', 'Helvetica Neue', Helvetica, Arial, sans-serif;
  font-size: 17px;
  line-height: 1.65;
  color: #010101;
}

/* Language switcher (inline) */
.lang-switcher {
  display: flex;
  align-items: center;
  font-size: 14px;
}
```

---

## File Structure for Website Project

```
allekirjoitus-website/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── main.js
├── assets/
│   ├── images/
│   └── logos/          # Copy from design system
│       ├── logo-full-color.svg
│       └── logo-mark-orange.svg
└── package.json
```

---

*Allekirjoitus.fi Web Design Skill v1.13 - January 2026*
*Updated with verified specs from live website Playwright analysis*

## Changelog

### v1.13 (January 19, 2026) - CSS Variables Complete
- **ADDED:** Missing CSS variables: `--text-black`, `--gray-border`, `--gray-400`, `--gray-500`, `--gray-600`
- **ADDED:** Layout variables: `--container-max`, `--container-narrow`
- **FIXED:** Variable naming now matches clone exactly (was `--allekirjoitus-text-dark`, now `--text-black`)
- **FIXED:** Variable naming for border (was `--allekirjoitus-gray-border`, now `--gray-border`)

### v1.12 (January 19, 2026) - Complete Button Documentation
- **ADDED:** `.btn-filled-sm` class documentation (filled orange button with 1.6px border, weight 500)
- **ADDED:** `.btn-submit` class documentation (form submit button, 4px radius, no border)
- **FIXED:** Button NOTE section now correctly lists all button variants and their differences
- **FIXED:** Changelog v1.1 entry had wrong border width (said 1.6px, correct is 2px)

### v1.11 (January 19, 2026) - Full Audit Alignment
- **FIXED:** Pricing card border is **1.6px** (was incorrectly documented as 2px)
- **FIXED:** Navigation link font-weight is **500** (was incorrectly documented as 600)
- **FIXED:** Enterprise list uses **orange `›` arrow markers**, NOT disc bullets
- **FIXED:** Pricing price span color is **#4b5563** (gray-600), NOT #666
- **FIXED:** Design principles now correctly says pricing cards use 20px radius (was incorrectly 6px)
- **FIXED:** Form inputs now correctly show no box-shadow, added `font-family: inherit`
- **ADDED:** Metropolis weight **300 (Light)** to @font-face declarations (was missing)
- **UPDATED:** All Quick Reference CSS to match clone implementation

### v1.10 (January 19, 2026)
- **FIXED:** Contact form area has LIGHT GRAY background (#f2f2f2), NOT dark
- **ADDED:** `.contact-form-wrapper` class with light gray background and padding
- **FIXED:** Form labels are DARK text (#010101), NOT white
- **UPDATED:** Contact Section documentation with wrapper structure

### v1.9 (January 19, 2026)
- **ADDED:** Metropolis font files to `website/assets/fonts/` (Regular, Medium, SemiBold, Bold, Light)
- **ADDED:** @font-face declarations for local Metropolis font loading
- **FIXED:** Body text now uses actual Metropolis font (was falling back to Helvetica/Arial)
- **UPDATED:** Font Loading documentation with required @font-face code

### v1.8 (January 19, 2026)
- **FIXED:** All button font-weight is **600** (semi-bold), NOT 500 - GLOBAL rule
- **UPDATED:** Button styling note with all 3 global rules (2px border, 600 weight, center align)

### v1.7 (January 19, 2026)
- **FIXED:** All button borders are **2px** (bolder), NOT 1.6px - this is a GLOBAL rule
- **FIXED:** Button text is CENTER-ALIGNED (only card CONTENT is left-aligned)
- **UPDATED:** All button CSS in documentation

### v1.6 (January 19, 2026)
- **FIXED:** Pricing card content is LEFT-ALIGNED, NOT centered
- **FIXED:** All pricing buttons use OUTLINE style (transparent bg, orange border)
- **UPDATED:** Pricing card CSS documentation with correct alignment

### v1.5 (January 19, 2026)
- **FIXED:** About section (with support notice + images) has WHITE background, NOT gray
- **ADDED:** Clear ALTERNATION RULE for section backgrounds
- **RULE:** Hero (GRAY) → About (WHITE) → Edut (GRAY) → Pricing (WHITE) → Features (GRAY) → FAQ (WHITE) → Contact (DARK)

### v1.4 (January 19, 2026)
- **FIXED:** Support notice is PART OF about section, not separate section
- **FIXED:** Features icons section (eIDAS) has GRAY background (#f2f2f2)
- **FIXED:** Features text is BOLD (font-weight: 600)
- **FIXED:** Contact section has DARK background (#170703), NOT white
- **FIXED:** Contact form button is OUTLINE style, NOT filled orange
- **FIXED:** Contact heading is WHITE text, 51px size
- **ADDED:** Contact section CSS documentation
- **UPDATED:** Section background pattern table

### v1.3 (January 19, 2026)
- **FIXED:** Header background is WHITE (#ffffff), NOT gray
- **FIXED:** Logo size: 310px wide, 39px tall
- **FIXED:** Pricing cards have 20px border-radius (rounded), NOT 6px
- **FIXED:** Pricing card border is 1.6px solid #bebebe
- **FIXED:** Pricing buttons are full-width
- **FIXED:** FAQ uses plus (+) icons, NOT chevrons
- **FIXED:** Benefits icons: 60x60px
- **FIXED:** Feature icons (eIDAS): 96x96px
- **ADDED:** Section background pattern documentation
- **ADDED:** Icon sizes documentation
- **ADDED:** Pricing subtitle orange styling

### v1.2 (January 19, 2026)
- **VERIFIED:** All typography specs via Playwright computed styles
- **CONFIRMED:** H1 hero = 78px, weight 500
- **CONFIRMED:** H2 section titles = 51px, weight 500 (NOT 36px)
- **CONFIRMED:** H2 about section = 36px, weight 400
- **CONFIRMED:** H3 benefits = 30px, weight 400
- **CONFIRMED:** H3 pricing = 20px, weight 600
- **ADDED:** Pure CSS implementation (no Tailwind dependency)
- **ADDED:** Flexbox pricing card structure for button alignment
- **ADDED:** Enterprise list with proper disc bullets

### v1.1 (January 19, 2026)
- **FIXED:** H1 hero size is 78px (not 36px) with font-weight 500
- **FIXED:** Login button is outline pill style (#e23013, 40px radius, 2px border)
- **FIXED:** Language switcher is inline horizontal "FI | EN", NOT stacked vertically
- **ADDED:** Clear distinction between Header Login Button and CTA Buttons
- **ADDED:** Header structure documentation
