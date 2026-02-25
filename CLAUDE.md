# CLAUDE.md — De Charles (Panadería Colonial)

## Project Overview

**De Charles** is a static marketing website for an artisanal Venezuelan bakery (panadería) based in Isla de Margarita, Venezuela. The business specializes in tequeños (fried cheese pastries) and pasapalos (appetizers). The site serves as a product showcase and order intake point via WhatsApp.

All content is in **Spanish**.

## Repository Structure

```
decharles/
├── CLAUDE.md            # This file
└── decharles/           # Deployed application root
    ├── index.html       # Single-page website (all HTML, CSS, and JS)
    ├── vercel.json      # Vercel deployment configuration
    └── img/             # Product/brand images (1.jpeg through 7.jpeg)
```

## Tech Stack

- **HTML5** — Semantic single-page structure
- **CSS3** — Embedded in `<style>` tag; uses CSS custom properties, flexbox, grid, animations
- **Vanilla JavaScript (ES6+)** — Embedded in `<script>` tag; no frameworks or libraries
- **Google Fonts** (CDN) — Playfair Display (headings), DM Sans (body), Caveat (accents)
- **Vercel** — Static hosting with no build step

There are **no** package managers, build tools, test frameworks, or external JS/CSS dependencies.

## Architecture

This is a **monolithic single-file application**. All code lives in `decharles/index.html`:

| Lines | Section | Description |
|-------|---------|-------------|
| 14–26 | CSS Variables | Color palette (`:root` custom properties) |
| 28–366 | CSS Styles | Full styling with section-level comments (`/* NAVBAR */`, etc.) |
| 370–382 | Navbar | Fixed nav with mobile hamburger toggle |
| 384–402 | Hero | Landing section with WhatsApp CTA |
| 404–420 | Marquee | Animated scrolling text banner |
| 422–456 | Story | Company history + 7-image auto-rotating carousel |
| 460–486 | Products | 3 product category cards |
| 488–584 | Menu | Pricing table (tequeños, escolares, pastelitos) |
| 586–606 | Testimonials | 3 customer reviews |
| 608–643 | CTA | Contact section with WhatsApp/Instagram links |
| 645–657 | Footer | Links and copyright |
| 659–696 | JavaScript | Navbar scroll, mobile menu, scroll animations, image carousel |

## Design System

### Color Palette (CSS Variables)
- `--brown-deep: #2C1810` — Primary dark background
- `--brown-rich: #4A2C1A` — Secondary dark
- `--brown-warm: #6B3A2A` — Accent brown
- `--gold: #C8943E` — Primary brand color
- `--gold-light: #E4B861` — Hover/highlight gold
- `--gold-pale: #F5DCA8` — Light text on dark backgrounds
- `--cream: #FAF3E8` — Page background
- `--cream-dark: #EDE0CC` — Borders/dividers

### Typography
- **Headings**: `'Playfair Display', serif` — weight 700/900
- **Body**: `'DM Sans', sans-serif` — weight 300/400/500/700
- **Accents/Labels**: `'Caveat', cursive` — handwritten feel

### Responsive Breakpoint
- Single breakpoint at `768px` (mobile-first adaptations)

## Key Patterns & Conventions

### CSS
- **BEM-like naming**: `.story-image-main`, `.product-card`, `.menu-item-price`
- **Section comments**: Each major block starts with `/* SECTION_NAME */`
- **CSS custom properties** for all colors — always use variables, never hardcode colors
- **No external CSS files** — all styles inline in `<style>` tag

### JavaScript
- **No frameworks** — vanilla DOM manipulation only
- **IntersectionObserver** for scroll-triggered `.fade-in` → `.visible` animations
- **setInterval** for image carousel (3.5s rotation)
- **classList** for toggling states (`.scrolled`, `.open`, `.active`)

### HTML
- **Semantic elements**: `<nav>`, `<section>`, `<footer>`
- **Section IDs** for anchor navigation: `#historia`, `#productos`, `#menu`, `#contacto`
- **External links** open in new tabs (`target="_blank"`)
- **Accessibility**: `aria-label` on interactive elements

## Deployment

- **Platform**: Vercel (static site)
- **Build command**: None (no build step)
- **Output directory**: `.` (the `decharles/` folder)
- **Configuration**: `decharles/vercel.json`
  - Clean URLs enabled (strips `.html` extensions)
  - Image assets cached for 1 year (`Cache-Control: public, max-age=31536000, immutable`)

## Local Development

No build tools needed. Open `decharles/index.html` directly in a browser, or serve it with any static file server:

```bash
cd decharles && python3 -m http.server 8000
```

## Testing

There are no automated tests. Changes should be verified manually by:
1. Opening `index.html` in a browser
2. Checking both desktop and mobile (768px breakpoint) layouts
3. Verifying navigation links, mobile menu toggle, scroll animations, and image carousel

## Business Context

- **WhatsApp ordering**: Links to `https://wa.link/vord2f`
- **Instagram**: `@decharlesmgta`
- **Phone**: +58 424 6163777
- **Prices**: Listed in USD, subject to change
- **Services**: Delivery, pickup, wholesale for businesses/events

## Guidelines for AI Assistants

1. **Language**: All user-facing content must be in Spanish. Code comments can be in English.
2. **No build tools**: Do not introduce npm, webpack, or any build pipeline. Keep it a simple static site.
3. **Single-file architecture**: All HTML, CSS, and JS stay in `index.html` unless the project scope grows significantly.
4. **Use CSS variables**: Never hardcode color values — always reference the `:root` custom properties.
5. **Keep it lightweight**: No external JS/CSS frameworks. The site's simplicity is a feature.
6. **Image assets**: Product images are in `decharles/img/` as numbered JPEGs. New images should follow the same naming convention.
7. **Responsive**: Any new sections or changes must work at both desktop and mobile (<=768px) sizes.
8. **Preserve brand tone**: The copy is casual, warm, and colloquial Venezuelan Spanish ("pa'", "pana", "echar pa'lante"). Maintain this voice.
