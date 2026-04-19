# US LNG: A Decade of Exports

An interactive 3D globe visualizing every US LNG cargo shipment from February 2016 through January 2026 — 8,707 real vessel departures sourced directly from DOE data, animated in real time across all major trade routes.

---

## What It Shows

The US became the world's largest LNG exporter over this decade, growing from a single terminal (Sabine Pass) shipping its first cargo in February 2016 to eight operating facilities in January of 2026. This tool lets you watch that entire story unfold — cargo by cargo, month by month — on a rotating globe with live market context.

Every glowing dot is a real ship. Every route is geometrically accurate, but not 100% historically accurate. Every price is historical.

---

## How to Use It

**No installation required.** The visualization is a single self-contained HTML file. Open it in any modern browser (Chrome, Edge, Firefox, Safari) and it runs entirely locally — no server, no dependencies, no internet connection needed after the file loads.

```
open "US LNG 10 Years of Exports.html"
```

---

## The Globe

Ships are rendered as glowing spheres traveling great-circle routes between their origin terminal and destination import facility. Routes are waypointed to stay in navigable water — threading the Strait of Hormuz, rounding the Sinai Peninsula into the Gulf of Aqaba, exiting the Gulf of Mexico through the Florida Straits and around Cuba, navigating the Panama Canal for Pacific-bound cargoes, arcing through the open South Atlantic east of the Brazilian bulge to reach Argentina and Brazil, and separating China-bound and Taiwan-bound routes through distinct Pacific approaches (East China Sea vs. southern strait).

Hovering over a ship shows its origin, destination, and cargo volume as a tooltip. Clicking a ship opens a cargo detail panel on the left side of the screen. Hovering over a destination country shows its cumulative delivered volume. Clicking a country opens a country detail panel.

### Cargo Detail Panel

Clicking any ship opens a panel on the left side of the screen showing:

- **Origin terminal** and **destination country**
- **Load date** and **transit duration** in days
- **Volume** in Bcf or Bcm (respects the active unit toggle)
- **Henry Hub price** at time of loading
- **JKM or TTF price** at time of arrival (depending on destination region)
- **Implied arbitrage spread** between load and delivery prices
- **Delivery progress bar** showing how far through the voyage the ship is at the current timeline position

### Country Detail Panel

Clicking any destination country opens a panel on the left side of the screen showing:

- **Country name** and **region**
- **Cumulative cargo count** and **total volume delivered** to date
- **First arrival** and **most recent arrival** dates
- **Top 3 origin terminals** by volume, each with a proportional bar

---

## Timeline Controls

The timeline bar runs along the bottom of the screen and covers the full period from **February 2016 to January 2026**. It can be hidden to give the globe more screen space and restored with a button.

| Control | Function |
|---|---|
| **Play / Pause** button | Starts or stops the animation |
| **Speed selector** | 0.1×, 0.5×, 1×, 2×, 4×, 8×, 16× — controls how fast time advances |
| **Scrubber bar** | Click or drag anywhere on the timeline to jump to a specific date |
| **Hide button** (⌄) | Collapses the timeline off-screen |
| **Timeline** button | Restores the timeline when hidden — appears at the bottom center |

The timeline header shows the current date in real time as the animation advances.

---

## Unit Toggle

A **Bcf / Bcm** toggle on the left side of the screen, below the view presets, switches all volume figures across the entire visualization between billion cubic feet (Bcf) and billion cubic metres (Bcm). The conversion used is 1 Bcf = 0.0283 Bcm. The toggle affects the cargo detail panel, the country detail panel, the Destinations pie chart total, hover tooltips on ships and countries, and the US dry gas production figure in the Production & Emissions panel.

---

## View Presets

Six camera presets are available via the buttons in the upper left:

| View | Description |
|---|---|
| **US Gulf** | Centers on the Gulf Coast export terminals |
| **LatAm** | Latin America receiving terminals |
| **Europe** | European import facilities |
| **MENA** | Middle East and North Africa |
| **Asia** | East and Southeast Asia |
| **Free orbit** | Unlocked — drag to rotate the globe freely |

---

## Right Panel

Three data panels are stacked on the right side of the screen, flush with the top of the dashboard, and update as the timeline advances.

### Markets
Displays the current month's **Henry Hub (HH)**, **Japan Korea Marker (JKM)**, and **Title Transfer Facility (TTF)** spot prices in $/MMBtu on a single condensed line, each with its color swatch and month-over-month delta. A combined time-series chart below plots all three price series on a shared axis spanning the full decade.

### Destinations
A pie chart breaking down all **cumulative delivered** LNG shipments by destination region: Asia, Europe, LatAm, MENA, and Africa. The panel shows the total volume delivered to date and the cumulative cargo count. Hovering over a country on the globe shows the total volume delivered to that country since February 2016. All volume figures reflect the active Bcf / Bcm unit selection.

### Production & Emissions
A dual-line chart showing two series over the full decade:
- **Methane intensity** (% of gross withdrawals, EPA GHGRP approximate) — declining from ~1.25% in 2016 to ~0.74% by 2026 as the industry improved leak detection and capture
- **US dry natural gas production** (Bcf/day or Bcm/day depending on unit selection, EIA approximate) — rising from ~72 Bcf/d in early 2016 to over 103 Bcf/d by 2026

Both series use independent y-axes normalized to the same chart height so trends are visually comparable despite different units.

---

## Terminals

Eight US LNG export facilities are represented:

| Terminal | State | First Cargo |
|---|---|---|
| Sabine Pass | Louisiana | Feb 2016 |
| Cove Point | Maryland | Mar 2018 |
| Corpus Christi | Texas | Dec 2018 |
| Cameron | Louisiana | May 2019 |
| Freeport | Texas | Sep 2019 |
| Elba Island | Georgia | Dec 2019 |
| Calcasieu Pass | Louisiana | Mar 2022 |
| Plaquemines | Louisiana | Dec 2024 |

---

## Destination Countries (45)

Cargoes are routed to import terminals in 45 countries across six regions:

**Asia** — China, Japan, South Korea, Taiwan, India, Pakistan, Bangladesh, Thailand, Singapore, Indonesia, Malaysia, Philippines

**Europe** — Spain, France, UK, Belgium, Netherlands, Italy, Portugal, Greece, Poland, Lithuania, Finland, Croatia, Malta

**LatAm** — Mexico, Brazil, Argentina, Chile, Colombia, Dominican Republic, Jamaica, El Salvador, Panama, Bahamas

**MENA** — Egypt, Jordan, Israel, UAE, Kuwait, Bahrain

**Africa** — Mauritania, Senegal

---

## Data Sources

| Dataset | Source |
|---|---|
| LNG cargo shipments (8,707 departures) | US Energy Information Administration (EIA) |
| Henry Hub natural gas prices | EIA / CME |
| Japan Korea Marker (JKM) prices | Platts/S&P Global (approximate) |
| Title Transfer Facility (TTF) prices | ICE/TTF (approximate) |
| Methane intensity | EPA Greenhouse Gas Reporting Program (GHGRP), interpolated from annual values |
| US dry gas production | EIA Monthly Energy Review, approximate |

All data is embedded directly in the HTML file. No external API calls are made at runtime.

---

## Requirements

- A modern web browser with WebGL support (Chrome 90+, Firefox 88+, Edge 90+, Safari 15+)
- No internet connection required after the file is downloaded
- No installation, build step, or local server needed

The file is large (~280KB) due to the embedded cargo dataset but loads in a few seconds on any modern machine.

---

## Technical Notes

Built as a single-file React + Three.js application with no build toolchain. All JavaScript is inlined, including the complete EIA cargo dataset encoded in a compact array-of-arrays format with lookup tables. Ship positions are computed in real time using spherical linear interpolation (slerp) between waypointed great-circle routes. The globe uses a custom GLSL shader for day/night rendering, ocean specularity, and topographic shading.
