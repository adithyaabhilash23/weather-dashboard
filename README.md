# WeatherLens v2 — Enhanced

A ground-up rewrite of the original WeatherLens dashboard. Core functionality is identical, but the entire CSS layer was expanded significantly — CSS now accounts for over two-thirds of the codebase, powering scroll animations, ambient backgrounds, hover micro-interactions, and a new type system. No new external dependencies added.

---

## Overview

Same data, completely reimagined presentation. The goal was to push CSS as the primary driver of the experience — animations, transitions, layout, and visual atmosphere — while keeping JavaScript lean and focused only on data fetching and DOM updates.

---

## Features

Everything from v1, plus:

- **Scroll reveal animations** — every section fades and slides into view using `IntersectionObserver` + CSS transitions, with staggered delays on child cards
- **Ambient background** — three floating radial orbs drifting continuously via `@keyframes`, layered with a dot-grid and radial mask
- **Hero shimmer** — a light sweep animation plays across the hero card on loop
- **Hover micro-interactions** — stat cards lift with per-card color-matched glows, forecast days slide up with a gradient underline sweep, city chips scale with a shimmer overlay
- **Animated hero entry** — temperature scales in on render, weather icon spins in with a spring bounce
- **Sliding unit toggle** — the °C / °F pill indicator slides entirely via CSS, no JS visual changes
- **Dedicated sunrise/sunset cards** — side-by-side card row with amber glow on hover
- **Logo breathing pulse** — glow animation on the header icon
- **Dual-color loading spinner** — conic ring with blinking mono text
- **Spring easing** — custom `cubic-bezier(0.34, 1.56, 0.64, 1)` spring curve used on interactive elements
- Upgraded chart animations with `easeOutQuart` easing
- Accessible markup throughout — `aria-label`, `aria-pressed`, `aria-live`, `role="alert"`

---

## Language Stack

| Language | Lines | Percentage |
|----------|-------|------------|
| CSS | 1,294 | **67.8%** |
| JavaScript | 433 | 22.7% |
| HTML | 179 | 9.3% |
| TypeScript | 0 | 0% |
| **Total** | **1,906** | |

---

## Fonts

| Font | Usage |
|------|-------|
| Syne (400–800) | Headings, logo, buttons |
| Space Grotesk | Body text, labels |
| Fira Code | Numbers, data values, mono labels |

All fonts loaded via Google Fonts CDN — no install needed.

---

## External Dependencies

| Library | Version | Purpose | Load method |
|---------|---------|---------|-------------|
| Chart.js | 4.4.1 | Line and bar charts | CDN |
| OpenWeatherMap API | v2.5 | Weather data | REST / fetch |

---

## API Endpoints Used

| Endpoint | Data fetched |
|----------|-------------|
| `/data/2.5/weather` | Current conditions |
| `/data/2.5/forecast` | 5-day / 3-hour forecast |
| `/data/2.5/air_pollution` | AQI and pollutant levels |

---

## Setup

### 1. Get a free API key
Sign up at [openweathermap.org](https://openweathermap.org/api). The free tier covers all three endpoints used here.

### 2. Add your key
Open `weather-dashboard.html` and find this line near the top of the `<script>` block:

```js
const API_KEY = 'YOUR_API_KEY_HERE';
```

Replace it with your actual key.

### 3. Open in browser
No server needed. Double-click the file or drag it into any browser. Works without a key too — falls back to static demo data for Mumbai.

---

## CSS Architecture

The stylesheet is split into 25 named sections, each marked with a block comment:

| # | Section | What it covers |
|---|---------|---------------|
| 1 | Design tokens & reset | CSS variables, box-sizing, base reset |
| 2 | Ambient background layer | Orb animations, dot-grid |
| 3 | Wrapper & layout | Max-width container, padding |
| 4 | Scroll animation system | `.reveal` classes, delays, `visible` state |
| 5 | Header | Glassmorphism bar, entry animation |
| 6 | Search bar | Input, focus ring, button styles |
| 7 | Unit toggle | Sliding pill indicator |
| 8 | Error & loading states | Alert box, spinner ring, blink animation |
| 9 | Landing page | Hero text, floating icon, city chips |
| 10 | Dashboard container | Show/hide wrapper |
| 11 | Hero card | Grid layout, shimmer, bg accent |
| 12 | Section labels | Divider labels with accent line |
| 13 | Stats row | 4-card grid, per-card accent colors |
| 14 | Card base | Shared surface card styles |
| 15 | Charts row | 3:2 grid, canvas wrapper |
| 16 | Forecast row | 5-column grid, hover underline sweep |
| 17 | Bottom row | 1:1 grid for hourly + AQI |
| 18 | Hourly scroll | Horizontal chip strip, custom scrollbar |
| 19 | Air Quality Index | AQI score, bar fills |
| 20 | Sunrise / Sunset cards | Side-by-side amber cards |
| 21 | Footer | Status badge, updated timestamp |
| 22 | Media queries | Breakpoints at 900px, 768px, 560px, 420px |
| 23 | Stagger animation helpers | nth-child transition delays |
| 24 | Global scrollbar | Custom scrollbar styling |
| 25 | Selection & misc | `::selection`, utility classes |

---

## Design Tokens

```css
--bg:           #05080f   /* page background        */
--surface:      #0d1425   /* card surfaces          */
--surface2:     #121b30   /* elevated surfaces      */
--surface3:     #1a2540   /* highest surfaces       */
--accent:       #63b3ed   /* primary blue           */
--accent2:      #9f7aea   /* secondary purple       */
--accent3:      #f6ad55   /* warm amber             */
--teal:         #4fd1c7   /* teal highlight         */
--success:      #68d391   /* green                  */
--danger:       #fc8181   /* red                    */
--ease-spring:  cubic-bezier(0.34, 1.56, 0.64, 1)
--ease-smooth:  cubic-bezier(0.4, 0, 0.2, 1)
```

---

## Browser Support

Works in all modern browsers. Requires `IntersectionObserver` support for scroll animations — available in all browsers since 2019 (Chrome 58+, Firefox 55+, Safari 12.1+, Edge 16+).

---

## Comparison with v1

| | v1 Original | v2 Enhanced |
|-|-------------|-------------|
| Total lines | 777 | 1,906 |
| CSS % | 34.6% | **67.8%** |
| JS % | 45.9% | 22.7% |
| Scroll animations | ✗ | ✓ |
| Ambient background | ✗ | ✓ |
| Hover micro-interactions | Basic | Rich |
| Spring easing | ✗ | ✓ |
| Fonts | DM Serif / DM Sans / JetBrains Mono | Syne / Space Grotesk / Fira Code |
| Accessibility attrs | Minimal | Full |
| CSS sections | Unsectioned | 25 named sections |

---

## License

Free to use and modify. Weather data provided by OpenWeatherMap under their terms of service.
