# ✈️ AeroKawaii Flight Operations Desk

A fully client-side, GitHub Pages-ready flight operations web app that blends aviation telemetry with a pastel Kawaii/Anime interface.

## Features

- **Pastel Tailwind UI** using Sakura Pink `#FFDEE9`, Lavender `#E8E5F6`, Mint Green `#E3FDF5`, and Cream `#FFFDF9`
- **Persistent ops header** with realtime **LOCAL**, **ZULU/UTC**, and **JST (UTC+9)** clocks
- **Animated dispatch mascot** reacting to crosswind severity and radar health
- **Live Kanto Radar** with Leaflet, centered on **RJTT Haneda** (`35.5494, 139.7798`) and a permanent hub marker
- **OpenSky ADS-B stream** filtered to Tokyo/Kanto bbox:
  - `lamin=34.8`
  - `lomin=138.8`
  - `lamax=36.2`
  - `lomax=140.8`
- Aircraft popup telemetry with:
  - Callsign
  - Altitude converted to feet
  - Ground speed converted to knots
- Japanese callsign flair icon (`JA*` prefix handling)
- **Crosswind Vector Calculator** (headwind/tailwind and left/right crosswind components)
- **Wind Correction Angle (WCA) tool** using law-of-sines style `asin` drift solution
- **Bi-directional altimeter converter** (`hPa = inHg × 33.8639`)
- **Aircraft Fleet Hangar** with profile persistence in `localStorage`
- **Live ATC panel** linking to legal public streams for **RJTT** and **RJAA**
- **NOTAM RegEx highlighter** for critical keywords:
  - `CLOSED`
  - `HAZARD`
  - `WIP`
  - `UNSERVICEABLE`

## Security & Stability Notes

- App runs completely serverless in the browser (no backend required)
- Async network requests are wrapped in `try/catch` for graceful offline/rate-limit behavior
- Inputs are validated before calculations to enforce type-safe numeric operations
- API and user text are rendered via safe DOM operations (`textContent`, created elements) to mitigate XSS

## Tech Stack

- **HTML5 + Vanilla JavaScript**
- **Tailwind CSS** (CDN, custom theme extension)
- **Leaflet.js** map
- **OpenSky Network API** for public ADS-B state vectors
- **GitHub Actions + GitHub Pages** deployment

## Run Locally

Open `index.html` in any modern browser.

> Note: OpenSky can occasionally rate-limit anonymous requests. The UI handles this and retries automatically.

## Deployment

Deployment is automated by `.github/workflows/pages.yml`:

- Triggers on push to `main`
- Uploads repository root as static artifact
- Deploys to GitHub Pages using official `actions/deploy-pages`

