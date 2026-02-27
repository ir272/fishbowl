# The Impossible Fishbowl — Complete

## What Was Built

A real-time 3D aquarium ecosystem simulation running entirely in the browser as a single HTML file (~3600 lines). The experience features a glass fishbowl with three species of fish governed by Craig Reynolds' Boids flocking algorithm, a self-balancing ecosystem with predator-prey dynamics, a full day/night cycle, procedural ambient audio with generative music, and over 20 custom GLSL shaders.

## What Works

**Core Rendering**
- Glass fishbowl with fresnel transparency, animated sparkle glints, chromatic edge tinting, and dual specular highlights
- Bright bowl rim with inner glow ring
- Water droplets that slide down the glass exterior
- Sandy floor with Voronoi-based animated caustic light patterns, wind ripple marks, and procedural debris spots
- Caustic light pool projected under the bowl onto the surface
- 4 volumetric god ray light shafts that dim/brighten with day/night cycle and shift color (golden at dawn, blue at night)
- Animated water surface with multi-layer ripples, fresnel effect, meniscus, surface tension highlights, and edge foam
- 250 floating plankton particles with bioluminescent night glow and circular water current
- 30 dust motes drifting lazily through the water
- 35 rising bubble particles with wobble animation and surface pop ripples
- Fish swim trails (additive-blended glow particles behind fast swimmers)
- Sand disturbance particles when fish swim near the bottom
- Air stone with focused bubble stream and green tube
- Dynamic underwater atmosphere depth fog (shifts with day/night)
- Dynamic vignette overlay (darkens at night, warms at dawn/dusk)
- Background with bokeh dots, twinkling stars at night, moon glow, animated clouds (day), and nebula haze (night)

**Decorations**
- Procedural rocks (6), branching coral (4) with animated pulsing polyps and emissive tips, shader-animated seaweed (7)
- Sea anemones (3) with shader-animated waving tentacles, bright tips, and 18 orbiting firefly particles at night
- Decorative shells (4), scattered pebbles (15), starfish (2)
- Treasure chest with animated hinged lid and sparkling gold coins
- Scuba diver figurine with mask, tank, flippers

**Fish System**
- 3 species: Neon Tetra (blue schooling), Angelfish (gold mid-tier), Betta (purple predator)
- Each fish built from procedural BufferGeometry with 16 spine segments, 10 ring segments
- Species-specific body profiles (torpedo, diamond, robust)
- Iridescent ShaderMaterial with view-angle hue shift, scale patterns, rim lighting
- Depth-based blue tinting and caustic light dappling on bodies
- School color pulse: tetras shimmer in synchronized blue waves when close together
- Real-time spine undulation for swimming animation
- Animated tail fin, dorsal fin, pectoral fins
- Betta: extra-large flowing tail, flowing dorsal crown, ventral belly fin
- Mouth that opens and pulses when near food
- Soft shadow projected on sand floor (fades with height)
- Eye glow at night with species-specific colors
- Body banking on turns for realistic movement
- Growth system: babies start at 40% scale and grow
- Smooth quaternion slerp rotation toward movement direction
- Individual personality system: boldness, sociability, curiosity, energy
- Barrel roll and surface jump tricks
- Idle hovering behavior (pause, bob gently, then resume)
- Glass curiosity (curious fish investigate the bowl wall)
- Dying fish float belly-up to the surface with wobble
- Feeding frenzy speed boost after food drops

**Boids Algorithm**
- Separation, alignment, cohesion (modulated by personality)
- Wall avoidance (quadratic force near bowl boundary)
- Vertical bounds (stay below water, above sand)
- Predator avoidance (modulated by boldness personality)
- Prey hunting behavior
- Food attraction (modulated by curiosity personality, breaks idle state)
- Mouse scatter (flee from mouse near glass)
- Glass curiosity (occasional drift toward bowl wall)
- Idle hovering (with food interruption)
- Speed modulated by energy personality

**Ecosystem**
- Food chain: large eats medium+small, medium eats small
- Reproduction: mature fish produce offspring that fade in
- Lifespan: old fish float belly-up and fade
- Population protection: minimum species counts enforced, respawn if needed
- Endangered species warnings
- Auto-feed every 45 seconds
- Event notifications with sound effects for all ecosystem events
- Ecosystem statistics tracking (births, deaths, meals, food drops)
- Runs self-balancing for extended periods

**Day/Night Cycle**
- 4-minute full cycle: dawn (warm orange) → day (bright) → dusk (golden/purple) → night (deep blue)
- Dynamic sun color, intensity, ambient light, and exposure
- Background responds to phase with horizon glow at dawn/dusk, animated clouds
- Twinkling star field, moon glow, and nebula during night
- Bioluminescent plankton at night (blue-green color shift)
- God rays shift color with time of day
- Dynamic vignette responds to lighting phase
- Anemone fireflies appear at night

**Audio**
- Procedural ambient underwater audio via Web Audio API
- Deep rumble (low-pass filtered noise)
- Mid-range water ambiance (bandpass filtered noise)
- Periodic bubble pop sounds
- Ambient procedural music: gentle pentatonic tones (day) / minor tones (night) with vibrato
- Ecosystem event sounds: rising cheerful tone (birth), snap (predation), descending somber tone (death)
- Starts on first user interaction

**Interaction**
- Click/tap to drop food particles (3-5 per click, drift down with wobble/spin, attract fish)
- Water splash ripple rings on food drop
- Click on fish to follow with smooth camera transition (orbit around followed fish)
- Double-click to toggle zoom
- Mouse hover near glass scatters nearby fish
- Drag to orbit, scroll to zoom (smooth lerp)
- Pinch-to-zoom on mobile
- Tap on fish to follow on mobile
- Feed button for mobile
- Touch support for all interactions

**Keyboard Controls**
- Space/P — Pause/unpause
- F — Drop food
- +/- — Speed control (0.25x to 8x)
- T — Time-lapse toggle (1x ↔ 8x)
- U — Underwater dive mode (first-person inside bowl)
- S — Screenshot (saves PNG with flash effect)
- R — Reset camera view
- H — Toggle keyboard help overlay
- Z — Zen mode (hide HUD)
- M — Cinema mode (slow-mo + wide FOV)
- I — Ecosystem statistics
- Esc — Stop following / exit dive mode

**HUD**
- Frosted glass panel with population counts per species (animated pop on change)
- Total population count
- Ecosystem health indicator (Thriving/Balanced/Stressed/Critical)
- Day counter (1 real minute = 1 day)
- Time of day label (Dawn, Sunrise, Morning, Midday, etc.)
- Simulation speed indicator
- Animated event notification toasts
- Animated hint overlay that fades after 8 seconds
- FPS counter
- Loading screen with spinner

## What I'd Improve With More Time

- **Post-processing**: Screen-space refraction through the glass bowl using render targets
- **Instanced rendering**: Move fish to InstancedMesh for better performance at higher counts
- **Depth of field**: Fake bokeh blur for fish far from the focal plane
- **Cloth sim fins**: Betta fins with spring-mass vertex animation
- **Procedural kelp**: Multi-segment physics-based kelp with better animation
- **Biome zones**: Different areas of the bowl with temperature/light variation
- **Fish territorial behavior**: Bettas defending territory, school formation leader
- **Multiplayer**: Share bowls between friends via WebRTC
- **Custom fish colors**: Let users choose fish species colors
- **Aquarium customization**: Drag and drop decorations

## How to View

```bash
open index.html
# or
python3 -m http.server 8888
# then visit http://localhost:8888
```

Works in Chrome, Firefox, Safari, or Edge. Best experienced fullscreen.
