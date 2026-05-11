# Design System — Monpro Freudenberg

## Theme

Dark-anchored industrial. The dominant surface is deep anthracite/charcoal, not black, not white. Off-white sections break the weight. A single warm aluminum accent (muted amber-gold) marks interaction and hierarchy. The physical scene: a homeowner arrives on mobile mid-morning, standing in their garden comparing quotes. The site should feel like the product catalogue of an architectural metalworks firm — precise, dense with intent, not loud.

## Color Palette

Strategy: **Committed** — one deep surface color carries 60% of the site. Off-white and the amber accent are deliberate relief.

```css
--color-surface-deep:   oklch(22% 0.008 60);   /* Anthracite — primary background */
--color-surface-mid:    oklch(30% 0.007 60);   /* Panels, cards */
--color-surface-light:  oklch(96% 0.006 80);   /* Off-white sections */
--color-surface-white:  oklch(98% 0.005 80);   /* Form backgrounds */

--color-text-primary:   oklch(96% 0.006 80);   /* On dark surfaces */
--color-text-secondary: oklch(70% 0.006 80);   /* Muted body on dark */
--color-text-dark:      oklch(18% 0.008 60);   /* On light surfaces */
--color-text-muted:     oklch(45% 0.007 60);   /* Captions, labels */

--color-accent:         oklch(72% 0.12 70);    /* Warm amber-gold — aluminum */
--color-accent-hover:   oklch(68% 0.14 70);    /* Hover state */

--color-border:         oklch(35% 0.008 60);   /* Subtle dividers on dark */
--color-border-light:   oklch(88% 0.006 80);   /* Dividers on light */
```

## Typography

Two fonts. One strong, one clean.

- **Display/Headings**: `Bebas Neue` (Google Fonts) — condensed, industrial, commanding. H1–H3.
- **Body/UI**: `Inter` (Google Fonts) — neutral, legible, professional. Body, labels, nav, forms.

```css
--font-display: 'Bebas Neue', sans-serif;
--font-body:    'Inter', sans-serif;

/* Scale — Major Third (1.25) */
--text-xs:   0.75rem;    /* 12px — labels, captions */
--text-sm:   0.875rem;   /* 14px — meta, secondary */
--text-base: 1rem;       /* 16px — body */
--text-lg:   1.125rem;   /* 18px — lead */
--text-xl:   1.25rem;    /* 20px — card titles */
--text-2xl:  1.5rem;     /* 24px — section heads */
--text-3xl:  2rem;       /* 32px — H3 */
--text-4xl:  2.5rem;     /* 40px — H2 */
--text-5xl:  3.5rem;     /* 56px — H1 mobile */
--text-6xl:  5rem;       /* 80px — H1 desktop */
--text-hero: 7rem;       /* 112px — display hero (Bebas Neue) */

--line-height-tight:  1.1;
--line-height-snug:   1.3;
--line-height-normal: 1.5;
--line-height-body:   1.7;

--letter-spacing-wide:   0.08em;   /* Labels, nav */
--letter-spacing-wider:  0.15em;   /* Eyebrows, section tags */
```

## Spacing Scale

Fibonacci-influenced. Varies deliberately — same padding everywhere is monotony.

```css
--space-1:   0.25rem;   /* 4px */
--space-2:   0.5rem;    /* 8px */
--space-3:   0.75rem;   /* 12px */
--space-4:   1rem;      /* 16px */
--space-5:   1.5rem;    /* 24px */
--space-6:   2rem;      /* 32px */
--space-8:   3rem;      /* 48px */
--space-10:  4rem;      /* 64px */
--space-12:  5rem;      /* 80px */
--space-16:  8rem;      /* 128px */
--space-20:  10rem;     /* 160px */
```

## Layout

- **Max content width**: 1200px, centered
- **Grid**: CSS Grid, 12 columns desktop, 4 columns tablet, 1 column mobile
- **Section padding**: `--space-16` vertical on desktop, `--space-10` on mobile
- **Gutter**: `--space-6` between grid columns
- No full-bleed containers wrapping everything. Sections alternate: dark → light → dark.

## Border Radius

Industrial aesthetic — minimal rounding.

```css
--radius-sm:  2px;
--radius-md:  4px;
--radius-lg:  8px;
--radius-xl:  12px;
```

## Elevation / Shadow

Dark surfaces use no drop shadow (they are the depth). Light surfaces use subtle shadows.

```css
--shadow-sm:  0 1px 3px oklch(10% 0.008 60 / 0.15);
--shadow-md:  0 4px 16px oklch(10% 0.008 60 / 0.20);
--shadow-lg:  0 12px 40px oklch(10% 0.008 60 / 0.28);
```

## Components

### Button — Primary
- Background: `--color-accent`
- Text: `--color-text-dark` (dark on amber for contrast)
- Padding: `--space-3` vertical, `--space-6` horizontal
- Font: Inter 600, `--letter-spacing-wide`, uppercase
- Border radius: `--radius-sm`
- Hover: `--color-accent-hover` + translate Y -1px (100ms ease-out)
- No box shadow. No gradient.

### Button — Ghost
- Border: 1px solid `--color-text-primary` at 40% opacity
- Text: `--color-text-primary`
- Same sizing as primary
- Hover: border opacity 100%, background `--color-surface-mid`

### Nav
- Fixed top, `--color-surface-deep` background, 1px bottom border `--color-border`
- Logo left, links right
- Link font: Inter 500, `--text-sm`, `--letter-spacing-wide`, uppercase
- Active state: `--color-accent` underline 2px

### Section Eyebrow
- Font: Inter 600, `--text-xs`, `--letter-spacing-wider`, uppercase
- Color: `--color-accent`
- Margin bottom: `--space-3`
- Used above every H2

### Project Card (Portfolio)
- No card border, no shadow on dark surfaces
- Full-bleed image (16:9 ratio)
- Overlay on hover: `--color-surface-deep` at 70% opacity, title + category label slides up
- Title: Bebas Neue, `--text-2xl`
- Transition: 200ms ease-out

### Contact Form
- On light background (`--color-surface-light`)
- Input: full border `--color-border-light`, `--radius-sm`, `--text-base`, `--space-4` padding
- Label: Inter 500, `--text-sm`, `--color-text-muted`
- Focus: border `--color-accent`, no box-glow

## Motion

Exponential ease-out only. No bounce, no elastic.

```css
--ease-out: cubic-bezier(0.16, 1, 0.3, 1);   /* expo-out */
--duration-fast:   100ms;
--duration-base:   200ms;
--duration-slow:   400ms;
```

Animate: opacity, transform, filter only. Never layout properties.

## Page Structure

```
/ (Home)
├── Nav (fixed)
├── Hero — Full viewport, dark, large Bebas Neue headline, single CTA
├── Intro strip — 3 short value statements (horizontal, light bg)
├── Produkte — Editorial grid, 2–3 featured product types
├── Referenzen / Portfolio — Masonry or asymmetric grid of project photos
├── Über uns — Short, direct. No founder-bio card. One paragraph + accent stat.
├── Service — What the process looks like (3–4 numbered steps)
└── Kontakt — Split: left=copy+phone, right=form. Dark bg.

/produkte (Products)
├── Nav
├── Page header — Bebas Neue, dark, full-width
├── Product list — Large editorial rows (alternating image/text), not cards
└── Kontakt CTA strip

/service (Service)
├── Nav
├── Page header
├── Process steps — Numbered, generous spacing
├── Trust signals — Project count, years experience (no star ratings)
└── Kontakt CTA strip
```

## Photography Direction

All images: real project photos from Monpro (to be provided by client via Ionos). 
- Preferred: wide-angle shots of completed installations, natural light
- Avoid: stock photos, people-posing shots, CGI renders
- Format: WebP, 1920px wide max, lazy-loaded below fold
- Ratio standards: Hero 16:9 or 21:9, portfolio cards 4:3 or 16:9

## Competitor Differentiation

| Competitor | Their weakness | Monpro advantage |
|---|---|---|
| DL Metallform | Template-heavy, generic cards, clutter | Editorial layout, deliberate whitespace |
| VK Alu Design | B2B industrial, cold | Same industrial but warm accent, better hierarchy |
| weinor.de | Corporate lifestyle, not local | Regional, direct, craftsman authority |
| id-deluxe.de | Luxury but generic | Focused: one product type, owned clearly |
