# React — Reaction Timer

A polished, portfolio-grade reaction timer game built with vanilla HTML, CSS, and JavaScript — featuring a live Three.js 3D background that reacts to every game state.

![Game States](https://img.shields.io/badge/states-5-00D4FF?style=flat-square) ![Rounds](https://img.shields.io/badge/rounds-5-A8FF3E?style=flat-square) ![No Dependencies](https://img.shields.io/badge/dependencies-none-FFB830?style=flat-square)

---

## Overview

React challenges you to click as fast as possible when the stimulus fires — but click too early and the round resets. Play 5 rounds, then see your average, best, and worst reaction times on the results screen.

The Three.js background isn't decorative. Each game state — waiting, ready, go, early click, and results — triggers a distinct visual response in the 3D scene, making the experience feel cohesive and intentional.

---

## Features

- **Precise timing** using `performance.now()` for millisecond accuracy
- **Early click detection** with penalty, visual shake, and round reset
- **5-round sessions** with per-round results and aggregate stats (average, best, worst)
- **Three.js animated background** with state-driven color, speed, and explosion effects
- **Fully responsive** — works on desktop and mobile
- **Touch support** alongside mouse and keyboard (Space / Enter)
- **Share button** — copies your score summary to clipboard
- **Zero dependencies** — Three.js loaded via CDN, no build tools or npm required

---

## Game States

| State | UI | 3D Scene |
|---|---|---|
| **Waiting** | Circle pulses cyan, label reads WAIT | Shapes drift slowly at low opacity |
| **Ready** | Ring brightens, label reads READY | Shapes accelerate and brighten, building tension |
| **Go** | Circle flashes lime green, label reads CLICK! | Shapes explode outward, then drift back |
| **Too early** | Circle flashes red, label reads TOO EARLY | Shapes shake and flash red |
| **Results** | Stats screen with round breakdown | Shapes settle into a slow amber orbit |

---

## Getting Started

No installation or build step required. Just open the file.

```bash
# Clone the repo
git clone https://github.com/your-username/react-reaction-timer.git
cd react-reaction-timer

# Open directly in your browser
open index.html
```

Or drag `index.html` into any browser window.

---

## Deployment

The entire project is a single `index.html` file. Deploy it anywhere that serves static files.

**Vercel**
```bash
npx vercel --prod
```

**Netlify** — drag and drop `index.html` into the Netlify dashboard, or use the CLI:
```bash
npx netlify deploy --prod --dir .
```

**GitHub Pages** — push to a repo, go to Settings → Pages, set the source to your main branch root.

---

## Project Structure

```
index.html
│
├── CSS Custom Properties      # All colors and typography tokens
├── Three.js Canvas Layer      # Fullscreen WebGL background (z-index: 0)
├── Game UI Overlay            # HTML screens layered on top (z-index: 10)
│
└── JavaScript Sections
    ├── 1 — Init & Constants
    ├── 2 — Three.js Scene Setup
    ├── 3 — Game State
    ├── 4 — UI Helpers
    ├── 5 — Game Logic
    ├── 6 — Results Screen
    └── 7 — Event Handlers
```

---

## Design System

**Colors**

| Token | Hex | Usage |
|---|---|---|
| `--bg` | `#0D1B2A` | Page background |
| `--surface` | `#1C2E40` | Cards and UI surfaces |
| `--cyan` | `#00D4FF` | Primary accent, idle state |
| `--lime` | `#A8FF3E` | Go state, best time |
| `--red` | `#FF4757` | Early click, worst time |
| `--white` | `#E8F0F7` | Body text |
| `--amber` | `#FFB830` | Stats, results state |
| `--muted` | `#4A6080` | Secondary labels |

**Typography**
- **Space Grotesk** — headings, timer display, round labels
- **Inter** — body text, stats, feedback messages

Both loaded from Google Fonts.

---

## Technical Notes

- Timing uses `performance.now()` — not `Date.now()` — for sub-millisecond precision
- The random stimulus delay is between 2000ms and 5000ms to prevent anticipation
- Three.js shapes use `MeshBasicMaterial` with wireframe rendering for a lightweight, stylized look
- The renderer uses `alpha: true` so the WebGL canvas composites cleanly over the HTML background color
- All colors are defined as CSS custom properties and mirrored as `0x` hex constants for Three.js

---

## Browser Support

Any modern browser with WebGL support. Tested on Chrome, Firefox, Safari, and Edge.
