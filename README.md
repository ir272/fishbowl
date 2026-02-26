# The Impossible Fishbowl

A mesmerizing real-time 3D aquarium ecosystem simulation running entirely in the browser. Built with Three.js r128 — no build tools, no assets, everything procedurally generated.

## How to View

Open `index.html` in any modern browser (Chrome, Firefox, Safari, Edge).

```
# macOS
open index.html

# or start a local server for best results
python3 -m http.server 8888
# then visit http://localhost:8888
```

## Features

### The Tank
- Glass fishbowl with realistic fresnel transparency and specular highlights
- Sandy floor with animated caustic light patterns
- Procedural rocks, branching coral, and swaying seaweed
- Volumetric god ray light shafts
- Floating plankton/debris particles
- Animated water surface with ripple patterns
- Subtle underwater atmosphere fog

### Fish (3 Species)
- **Neon Tetra** (blue) — Small, fast schooling fish. Tight formations, darting movement.
- **Angelfish** (gold) — Medium, elegant fish. Loose schools, graceful turns.
- **Betta** (purple) — Large solitary predator. Dramatic fins, slow but powerful.

Each fish has:
- Procedural body geometry with real-time spine undulation
- Animated tail, dorsal, and pectoral fins
- Smooth quaternion-based rotation toward movement direction
- Craig Reynolds' Boids algorithm: separation, alignment, cohesion

### Ecosystem
- Food chain: Bettas hunt Angelfish and Tetras. Angelfish hunt Tetras.
- Predator avoidance and prey chasing behavior
- Reproduction over time (new fish fade in near parents)
- Lifespan system (old fish fade out and sink)
- Self-balancing population with minimum species protection
- Population counter on the HUD

### Interaction
- **Click/tap** on the bowl to drop food — fish swarm toward it
- **Drag** to orbit the camera around the bowl
- **Scroll/pinch** to zoom in and out
- **Mouse hover** near the glass makes nearby fish scatter
- **Feed button** on HUD for mobile users

### Visual Effects
- Fresnel glass with chromatic edge tint and dual specular highlights
- Procedural caustic light network on sand floor
- Crossed-plane volumetric god rays with pulsing animation
- Additive-blend floating particles
- Slowly shifting background gradient (simulates time of day)
- Underwater depth atmosphere

## Tech Stack
- Single `index.html` file (~1400 lines)
- Three.js r128 from CDN
- All geometry, textures, and effects generated in code
- No build tools, no npm, no external assets
- Targets 60fps with 30+ fish

## Controls
| Action | Desktop | Mobile |
|--------|---------|--------|
| Orbit | Click + drag | Touch + drag |
| Zoom | Scroll wheel | Pinch (browser native) |
| Feed | Click on water | Tap on water / Feed button |
| Scatter | Move mouse near glass | — |
