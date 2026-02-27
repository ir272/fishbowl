# The Impossible Fishbowl

A mesmerizing real-time 3D aquarium ecosystem simulation running entirely in the browser. Built with Three.js r128 — no build tools, no assets, everything procedurally generated. Features a self-balancing ecosystem, day/night cycle, ambient audio with procedural music, and over 30 interactive controls.

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
- Bright rim with inner glow ring and water droplets sliding down the exterior
- Sandy floor with Voronoi-based animated caustic light patterns, ripple marks, and debris
- Procedural rocks, branching coral with animated pulsing polyps, shader-animated swaying seaweed
- Sea anemones with waving tentacle animations, bright tips, and orbiting fireflies at night
- Decorative shells, scattered pebbles, starfish
- Treasure chest with animated hinged lid and sparkling gold coins
- Scuba diver figurine (classic aquarium piece)
- Air stone with green tube and focused bubble stream
- Volumetric god ray light shafts that shift color with day/night (golden at dawn, blue at night)
- Floating plankton particles with bioluminescent night glow and circular water current
- Rising bubble particles with wobble animation and surface pop ripples
- Fish swim trails (additive-blended glow particles behind fast fish)
- Dust motes drifting lazily through the water
- Sand disturbance particles when fish swim near the bottom
- Animated water surface with multi-layer ripples, fresnel, meniscus, and edge foam
- Caustic light pool projected under the bowl
- Dynamic underwater atmosphere fog (shifts with day/night)
- Dynamic vignette overlay (darkens at night, warms at dawn/dusk)
- Animated sky with drifting clouds (day) and nebula haze (night)

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
- Mouth that opens near food
- Soft shadow projected on sand floor
- Body banking on turns
- Growth system (babies start at 40% scale and grow)
- Smooth quaternion slerp rotation
- Individual personality: boldness, sociability, curiosity, energy
- Craig Reynolds' Boids: separation, alignment, cohesion, wall avoidance
- School color pulse: tetras shimmer in synchronized blue waves when close together
- Eye glow at night (species-specific colors)
- Idle hovering behavior (pause and bob gently, then resume)
- Glass curiosity (curious fish occasionally investigate the bowl wall)
- Tricks: barrel rolls and surface jumps
- Dying fish float belly-up to the surface

### Ecosystem
- Food chain: Bettas hunt Angelfish and Tetras. Angelfish hunt Tetras.
- Predator avoidance and prey chasing (modulated by fish personality)
- Reproduction over time (new fish fade in near parents)
- Lifespan system (old fish float belly-up and fade)
- Self-balancing population with minimum species protection
- Endangered species warnings
- Auto-feed every 45 seconds
- Feeding frenzy: speed boost after food drops
- Event notifications with ecosystem sounds: births, deaths, predation
- Ecosystem statistics tracking (births, deaths, meals, food drops)

### Day/Night Cycle
- Full 4-minute cycle: dawn, day, dusk, night
- Dynamic sun color, intensity, and ambient lighting
- Background shifts with horizon glow at dawn/dusk, clouds during day
- Twinkling star field, moon glow, and nebula at night
- Bioluminescent plankton during night phase (blue-green color shift)
- God rays shift color: golden at dawn, cool blue during day, deep blue at night
- Anemone fireflies glow and orbit at night

### Ambient Audio
- Procedural underwater audio via Web Audio API
- Deep low-frequency rumble (filtered noise)
- Mid-range water ambiance
- Periodic bubble sound effects
- Ambient procedural music: gentle pentatonic tones (day) / minor tones (night)
- Ecosystem event sounds: cheerful birth tone, snap for predation, somber death tone
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
| Zen mode | Z key (hide HUD) | — |
| Cinema mode | M key (slow-mo + wide FOV) | — |
| Stats | I key | — |
| Zoom toggle | Double-click | Double-tap |

### HUD
- Frosted glass panel with population counts per species (animated on change)
- Total population count
- Ecosystem health indicator (Thriving/Balanced/Stressed/Critical)
- Day counter (1 minute = 1 day)
- Time of day label
- Simulation speed indicator
- Feed button for mobile
- Animated event notification toasts

## Tech Stack
- Single `index.html` file (~3600 lines)
- Three.js r128 from CDN
- Web Audio API for procedural audio and music
- All geometry, textures, shaders, and effects generated in code
- 20+ custom GLSL shaders (glass, sand caustics, water, seaweed, anemones, fish, background, god rays, atmosphere)
- No build tools, no npm, no external assets
- Targets 60fps with 30+ fish
- Loading screen with animated spinner
- Pinch-to-zoom and touch support for mobile
