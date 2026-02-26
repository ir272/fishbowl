# The Impossible Fishbowl

A mesmerizing real-time 3D aquarium ecosystem simulation running entirely in the browser. Built with Three.js r128 — no build tools, no assets, everything procedurally generated. Features a self-balancing ecosystem, day/night cycle, ambient audio, and over 30 interactive controls.

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
- Glass fishbowl with fresnel transparency, animated sparkle glints, and dual specular highlights
- Sandy floor with Voronoi-based animated caustic light patterns
- Procedural rocks, branching coral, shader-animated swaying seaweed
- Sea anemones with waving tentacle animations and bright tips
- Decorative shells, scattered pebbles, starfish
- Treasure chest with gold coins spilling out
- Scuba diver figurine (classic aquarium piece)
- Air stone with green tube and focused bubble stream
- Volumetric god ray light shafts that respond to day/night intensity
- Floating plankton particles with bioluminescent night glow
- Rising bubble particles with wobble animation
- Animated water surface with multi-layer ripples, fresnel, and meniscus
- Caustic light pool projected under the bowl
- Underwater depth atmosphere fog
- Vignette overlay

### Fish (3 Species)
- **Neon Tetra** (blue) — Small, fast schooling fish. Tight formations, darting movement.
- **Angelfish** (gold) — Medium, elegant fish. Loose schools, graceful turns.
- **Betta** (purple) — Large solitary predator. Dramatic flowing fins, slow but powerful.

Each fish has:
- Procedural body geometry with real-time spine undulation
- Iridescent ShaderMaterial with view-angle hue shift, scale patterns, rim lighting
- Depth-based blue tinting (deeper = bluer underwater feel)
- Caustic light dappling on bodies from above
- Animated tail, dorsal, pectoral fins (Betta: extra-large flowing tail + ventral fin)
- Body banking on turns
- Growth system (babies start small and grow)
- Smooth quaternion slerp rotation
- Individual personality: boldness, sociability, curiosity, energy
- Craig Reynolds' Boids: separation, alignment, cohesion, wall avoidance

### Ecosystem
- Food chain: Bettas hunt Angelfish and Tetras. Angelfish hunt Tetras.
- Predator avoidance and prey chasing (modulated by fish personality)
- Reproduction over time (new fish fade in near parents)
- Lifespan system (old fish fade out and sink)
- Self-balancing population with minimum species protection
- Endangered species warnings
- Auto-feed every 45 seconds
- Event notifications: births, deaths, predation, population warnings

### Day/Night Cycle
- Full 4-minute cycle: dawn, day, dusk, night
- Dynamic sun color, intensity, and ambient lighting
- Background shifts with horizon glow at dawn/dusk
- Twinkling star field and moon glow at night
- Bioluminescent plankton during night phase
- God rays dim at night, brighten during day

### Ambient Audio
- Procedural underwater audio via Web Audio API
- Deep low-frequency rumble (filtered noise)
- Mid-range water ambiance
- Periodic bubble sound effects
- Starts on first user interaction (browser requirement)

### Interaction & Controls
| Action | Desktop | Mobile |
|--------|---------|--------|
| Orbit | Click + drag | Touch + drag |
| Zoom | Scroll wheel | Pinch |
| Feed | Click on water / F key | Tap on water / Feed button |
| Scatter | Mouse hover near glass | — |
| Follow fish | Click on a fish | Tap on a fish |
| Stop following | Esc | — |
| Pause | Space or P | — |
| Speed +/- | + / - keys | — |
| Time-lapse | T key (toggles 8x) | — |
| Dive mode | U key | — |
| Screenshot | S key | — |
| Reset view | R key | — |
| Show controls | H key | — |
| Zoom toggle | Double-click | Double-tap |

### HUD
- Frosted glass panel with population counts per species
- Total population count
- Ecosystem health indicator (Thriving/Balanced/Stressed/Critical)
- Day counter (1 minute = 1 day)
- Time of day label
- Simulation speed indicator
- Feed button for mobile
- Animated event notification toasts

## Tech Stack
- Single `index.html` file (~2800 lines)
- Three.js r128 from CDN
- Web Audio API for procedural audio
- All geometry, textures, shaders, and effects generated in code
- Custom GLSL shaders throughout (glass, sand caustics, water, seaweed, anemones, fish, background, god rays)
- No build tools, no npm, no external assets
- Targets 60fps with 30+ fish
- Loading screen with animated spinner
