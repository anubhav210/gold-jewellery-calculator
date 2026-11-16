# Gold Jewellery Price Calculator

**Live app:** https://anubhav210.github.io/gold-jewellery-calculator/

A single-page calculator for working out what gold jewellery actually costs. Enter the gold rate, carat, weight,
making charges and GST to instantly see the 24 carat equivalent price, the full price breakdown and the final payable
amount.

## Features

- Instant recalculation on every input change — no submit button
- 24 carat equivalent rate derived from the selected carat
- Gold value calculated per gram from the rate per 10 g
- Making charges as a percentage of gold value
- GST applied to the subtotal (gold value + making charges)
- Indian number formatting (₹1,35,000.00) and two-decimal rounding
- Responsive layout with a one-tap **Reset**
- Installable as a PWA and works offline

## Install as an app

Open the live URL in Chrome, Edge or Safari and use **Install app** / **Add to Home Screen**. The app is cached by a
service worker, so it keeps working without a network connection.

## How the price is calculated

| Step | Formula |
| --- | --- |
| Price per gram | `rate ÷ 10` |
| 24 carat price (per 10 g) | `rate × 24 ÷ carat` |
| Gold value | `price per gram × weight` |
| Making charges | `gold value × making %` |
| Subtotal | `gold value + making charges` |
| GST | `subtotal × GST %` |
| Final amount | `subtotal + GST` |

Figures are indicative and rounded to two decimals. They do not include wastage, stone charges, hallmarking fees or
other retailer-specific add-ons.

## Project structure

```
index.html     # markup, styles and calculator logic (no build step, no dependencies)
manifest.json  # PWA manifest (name, icons, theme colours)
sw.js          # service worker for offline caching
icon-192.png   # app icon
icon-512.png   # app icon
```

## Run locally

No build tools are needed. Any static server works:

```bash
python -m http.server 8080
```

Then open <http://localhost:8080>. Opening `index.html` directly also works, but service workers (offline mode) need
`http://` or `https://`.

## Deployment

The site is served with GitHub Pages from this repository, so any push to the publishing branch goes live at
https://anubhav210.github.io/gold-jewellery-calculator/.

## Tech

Plain HTML, CSS and JavaScript — no frameworks, no dependencies, no build step.
